# TryHackMe Hacker Holidays CTF Challenge #4: Packed Light

## Overview

This challenge involved analyzing network traffic to identify and decrypt a covert data exfiltration channel. The attacker used a malicious keylogger that disguised stolen keystrokes as legitimate HTTP traffic, employing XOR encryption and Base64 encoding to evade detection.

**Difficulty Level:** Medium  
**Key Concepts:** Packet Analysis, Cryptography, Data Exfiltration, HTTP Protocol Analysis

---

## Challenge Scenario

During off-peak hours, suspicious network activity was detected at a hotel. An attacker had successfully established a covert communication channel to extract data equivalent to an entire hotel tower's worth of information each night. The exfiltrated data was cleverly hidden within normal-looking HTTP traffic.

Before the connection could be traced, Vera managed to capture a packet dump from the guest network. The capture contained evidence of a recurring malicious process—one that appeared isolated and didn't correspond to any legitimate hotel service.

**Objective:** Analyze the packet capture to identify the covert channel, extract the hidden data, and recover the flag.

---

## Tools Used

| Tool | Purpose |
|------|---------|
| **Wireshark** | Network packet analysis and HTTP traffic examination |
| **CyberChef** | Decoding Base64 and performing XOR operations |
| **Python** | Understanding the malicious script logic |

---

## Methodology

### Step 1: Initial Reconnaissance with Wireshark

I opened the provided PCAP file in Wireshark to get an overview of the network traffic. Initial observations:
- Multiple HTTP GET requests to the same destination
- Requests originated from the internal network to an external server
- Traffic pattern appeared repetitive and automated

**Key Finding:** The HTTP requests were all going to `http://byte-lotus-hotel.thm:8080/a`

### Step 2: Filtering and Identifying the Malicious Script
<img width="1171" height="585" alt="image" src="https://github.com/user-attachments/assets/b7a56c7f-a753-4f24-8d74-aec91f254f61" />

Applied an HTTP-only filter to isolate web traffic:

```
http
```

Examining the HTTP responses revealed interesting payload data—specifically, a Python script implementing a keylogger using the `pynput` library.

<img width="1140" height="502" alt="image" src="https://github.com/user-attachments/assets/ba9479e6-6ca3-4cdb-a3f3-a6fd58e691cc" />

#### Keylogger Analysis

The malicious script had the following characteristics:

**Libraries Used:**
- `pynput.keyboard` - Captures keyboard input
- `requests` - Sends HTTP requests to the C2 server
- `base64` - Encodes encrypted data

**Key Functions:**

```python
def getkey(p1, p2):
    """Generates encryption key from two parameters"""
    key = (p1 + p2) % 256
    return key

def sendltr(letter):
    """Processes each keystroke and sends it to C2"""
    # Convert to bytes
    # XOR encrypt with derived key
    # Base64 encode
    # Insert into HTTP cookie
    # Send to C2 server
```

**Command & Control (C2) Server:** `byte-lotus-hotel.thm:8080`

### Step 3: Identifying the Exfiltration Channel

The data exfiltration mechanism was ingeniously simple yet effective:

**Transport Vector:** HTTP Cookie Header  
**Cookie Name:** `hotel_sess_state`  
**Encoding Chain:** Keystroke → UTF-8 Bytes → XOR Encrypt → Base64 Encode

Each keystroke was processed individually in the following workflow:

```
User Input (e.g., "A")
    ↓
keyboard.Listener detects key press
    ↓
on_press() callback triggered
    ↓
sendltr("A") processes the character
    ↓
Convert character to bytes using UTF-8
    ↓
XOR encrypt using derived secret key
    ↓
Base64 encode the encrypted bytes
    ↓
Insert into Cookie: hotel_sess_state=[base64_data]
    ↓
Send HTTP GET request to C2 server
    ↓
Server decodes and decrypts to recover original keystroke
```

**Why This Method Was Effective:**
- HTTP cookies are rarely inspected in detail by basic security tools
- The data appears to be legitimate session state
- Each request looks like normal traffic to the untrained eye
- The User-Agent header was spoofed: `Mozilla/5.0 (Windows NT 10.0; Win64; x64) ByteLotusClient/1.1`

### Step 4: Extracting Cookie Values

<img width="1168" height="620" alt="image" src="https://github.com/user-attachments/assets/e6f5c52d-0e69-4e49-973e-8c3a2800475e" />

Applied a Wireshark filter to isolate all requests containing the malicious cookie:

```
http.cookie contains "hotel_sess_state"
```
The value of the Cookie can be found in the Cookie field under the HyperText Transfer Protocol Tab. Below is an example of the cookie value for the first packet found using the Wireshark filte, but also repeat the process by finding the cookie values for the other remaining packets.

<img width="1167" height="487" alt="image" src="https://github.com/user-attachments/assets/3c03c57e-b782-40b3-9e15-bba2a4dd804e" />

This revealed all encoded keystrokes in sequence. The captured cookie values were:

```
HA== AA== BQ== Mw== Hg== ew== Og== fA== Fw== eQ== Ow== Fw== Pw== 
fA== PA== Kw== IA== eQ== Jg== Lw== Fw== eA== Pg== LQ== Gg== Fw== 
MQ== eA== PQ== NQ==
```

### Step 5: Decryption Process Using CyberChef

To decrypt each keystroke, I needed to reverse the encryption process:

**Decryption Steps:**
1. Base64 Decode - Convert the encoded string back to bytes
2. XOR Decrypt - Apply XOR operation with the secret key to recover the original character

#### Decoding the First Character

<img width="1377" height="567" alt="image" src="https://github.com/user-attachments/assets/ebea9f04-5531-4968-9bad-08abfee2e108" />

I used CyberChef to decode the first cookie value `HA==`:

**CyberChef Recipe:**
- **Operation 1:** From Base64
  - Alphabet: `A-Za-z0-9+/=`
  - Remove non-alphabet characters: ✓
  
- **Operation 2:** XOR
  - Key: `H` (the derived secret key)
  - Scheme: Standard
  - Input type: UTF8

**Result:** The first character decoded to `T`

#### Processing All Cookies

<img width="1363" height="417" alt="image" src="https://github.com/user-attachments/assets/58626c07-2945-436d-bf17-f0018cd3351d" />

Following the same Base64 decode → XOR decrypt process for each cookie value in sequence:

```
HA== → T
AA== → H
BQ== → M
Mw== → {
[... continuing for all values ...]
NQ== → }
```

### Step 6: Assembling the Flag

Concatenating all decrypted characters in order recovered the complete flag. Flag was not disclosed.

---

## Key Technical Insights

### 1. XOR Encryption Weakness
XOR is a symmetric cipher, meaning the same operation both encrypts and decrypts. While simple, it's vulnerable to frequency analysis and known-plaintext attacks.

### 2. Covert Channel Characteristics
This attack demonstrates several hallmarks of a covert channel:
- **Legitimacy Masking:** Data hidden within normal protocol elements
- **Low Volume:** Single keystrokes sent individually avoid rate-limiting triggers
- **Protocol Abuse:** Misuse of HTTP cookies for command & control

### 3. Detection Indicators
A security analyst could have identified this threat by:
- Monitoring for repeated requests to unusual internal domains
- Analyzing cookie contents for suspicious Base64-encoded data
- Correlating automated GET requests with keyboard input patterns
- Identifying spoofed User-Agent strings

---

## Lessons Learned

1. **Don't Trust Superficial Traffic Patterns** - Malicious traffic can look completely normal at first glance
2. **Deep Inspection Matters** - Looking beyond protocol headers reveals hidden data channels
3. **Encoding ≠ Encryption** - Base64 is encoding (obfuscation), not encryption; it doesn't provide security
4. **Protocol Flexibility** - HTTP has many fields (cookies, headers, body) that can be abused for data exfiltration
5. **Combined Techniques** - Layering encoding + encryption + hiding in normal traffic significantly increases stealth

---

## Tools & Techniques Summary

| Technique | Application |
|-----------|-------------|
| **Packet Filtering** | Isolate HTTP traffic and identify specific cookie patterns |
| **Protocol Analysis** | Understand HTTP structure and identify anomalies |
| **Base64 Decoding** | Reverse the encoding layer |
| **XOR Cryptanalysis** | Decrypt the encrypted data |
| **Pattern Recognition** | Connect individual keystrokes into readable text |

---

## Challenges Encountered

- **Initial Reconnaissance:** Determining which field contained the exfiltrated data required careful examination of HTTP headers
- **Key Derivation:** Understanding how the encryption key was generated was crucial to successful decryption
- **Manual Processing:** Decoding 25+ cookies individually was tedious but necessary for verification

---

## Conclusion

The "Packed Light" challenge effectively demonstrated how attackers can hide data in plain sight by:
1. Using legitimate protocols for illegitimate purposes
2. Applying basic encryption to obscure content
3. Breaking data into small, inconspicuous chunks
4. Hiding the covert channel within expected traffic patterns

Successfully recovering the flag required methodical analysis, understanding of cryptographic concepts, and persistence in examining seemingly innocuous network traffic. This challenge reinforces the importance of deep packet inspection and behavioral analysis in threat detection.

---

## Related Security Concepts

- **Data Exfiltration:** Unauthorized removal of sensitive data from a system
- **Covert Channels:** Hidden communication paths that bypass normal security controls
- **C2 Communication:** Command and Control infrastructure used to manage compromised systems
- **Protocol Abuse:** Misusing legitimate protocols for malicious purposes
- **Steganography vs. Cryptography:** Hiding vs. securing information

---
*Challenge completed as part of TryHackMe Hacker Holidays CTF Series*
