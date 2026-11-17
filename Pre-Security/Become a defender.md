# TryHackMe: Become a Defender

![Platform](https://img.shields.io/badge/Platform-TryHackMe-212C42?logo=tryhackme&logoColor=white)
![Focus](https://img.shields.io/badge/Focus-Defensive%20Security-blue)
![Team](https://img.shields.io/badge/Team-Blue%20Team-1f6feb)

> Room: [Become a Defender](https://tryhackme.com/room/becomeadefender)

## Table of Contents

- [Overview](#overview)
- [1. What Is Defensive Security?](#1-what-is-defensive-security)
- [2. Understanding the Defender's Scope](#2-understanding-the-defenders-scope)
- [3. Understanding Attack Paths](#3-understanding-attack-paths)
- [4. Available Defensive Security Controls](#4-available-defensive-security-controls)
- [5. Key Terminology](#5-key-terminology)
- [6. Key Takeaways](#6-key-takeaways)
- [Skills & Concepts](#skills--concepts)

---

## Overview

This room introduces the fundamentals of **Defensive Security**, focusing on how cybersecurity professionals protect organizational systems, monitor infrastructure, identify suspicious activity, and respond to potential threats.

Defensive security is primarily associated with the **Blue Team**, whose responsibility is to maintain the confidentiality, integrity, and availability (**CIA Triad**) of an organization's systems and data.

The room explores the responsibilities of defenders, the importance of understanding client infrastructure, common defensive measures, and the principles behind identifying and mitigating cyber threats.

---

## 1. What Is Defensive Security?

Defensive security involves implementing security controls and monitoring mechanisms to prevent, detect, and mitigate cyberattacks.

Defenders must understand their environment, identify vulnerabilities, monitor system activity, and respond to incidents before they cause significant damage.

The main responsibilities of defensive security include:

- **Prevention:** Implementing security controls such as firewalls, antivirus software, and regular security patching to reduce the likelihood of attacks.
- **Detection:** Monitoring network traffic, system logs, and security alerts to identify suspicious or malicious activity.
- **Mitigation:** Limiting the impact of an attack by blocking malicious traffic, isolating compromised systems, or disabling affected accounts.
- **Analysis:** Investigating security incidents by reviewing logs, identifying indicators of compromise (IOCs), and determining how an attack occurred.
- **Response and Improvement:** Recovering affected systems, documenting incidents, and strengthening security controls to prevent similar attacks.

---

## 2. Understanding the Defender's Scope

Before implementing security controls, defenders must understand the organization's infrastructure and determine which systems and assets require protection.

This includes identifying employee workstations, servers, applications, network devices, and the connections between them.

A city analogy helps explain how different infrastructure components relate to defensive security:

| Infrastructure | Purpose | City Analogy |
|---|---|---|
| Employee Devices | Used by employees to access organizational resources | Homes |
| Web Server | Hosts websites and applications | Shops and public buildings |
| Mail Server | Sends and receives organizational emails | Post office |
| Firewall | Controls incoming and outgoing network traffic | City gate |
| Internet | External networks outside organizational control | Outside the city |

Understanding the environment allows defenders to determine which assets are exposed, where sensitive information is stored, and which security controls are required.

---

## 3. Understanding Attack Paths

An important responsibility of defenders is understanding how attackers can move through an organization's infrastructure.

Attackers rarely focus on a single system. Instead, they may compromise one asset and use it as an entry point to access additional systems and sensitive information.

### Example Attack Scenario

1. An employee receives a phishing email containing a malicious attachment.
2. The employee opens the attachment, potentially compromising their workstation.
3. The attacker attempts to steal usernames and passwords.
4. Using compromised credentials, the attacker attempts to access the organization's mail server.
5. The attacker attempts to move laterally toward database servers containing sensitive information.

Each stage represents an opportunity for defenders to detect suspicious behaviour and prevent further compromise.

### Key Defender Principles

- **Threat Anticipation:** Consider potential attack scenarios and identify how attackers could exploit weaknesses in the environment.
- **Attack Awareness:** Understand common attack techniques, tactics, and stages to recognize suspicious activity.
- **Risk Prioritization:** Identify critical systems and prioritize assets based on their importance and potential impact if compromised.
- **Continuous Adaptation:** Regularly review and improve security controls as vulnerabilities, technologies, and attacker techniques evolve.

---

## 4. Available Defensive Security Controls

Defenders use multiple security technologies and controls to protect organizational infrastructure. This is known as a **layered security approach**, where different mechanisms work together to reduce the likelihood and impact of an attack.

| Component | Potential Threat | Defensive Measures |
|---|---|---|
| Employee Devices | Malicious links, malware, unsafe downloads | Antivirus, endpoint protection, regular patching |
| Web Server | Unauthorized access and malicious web traffic | Traffic filtering, secure communication, access controls |
| Mail Server | Phishing emails and malicious attachments | Spam filtering, email security, attachment scanning |
| Firewall | Unauthorized network access | Firewall rules, traffic filtering, IP blocking |
| External Internet | Threats originating outside the organization | Restrict inbound traffic and monitor network activity |

No single security solution can prevent every attack. Effective defense requires multiple layers of protection, continuous monitoring, and timely incident response.

---

## 5. Key Terminology

| Term | Definition |
|---|---|
| Blue Team | Cybersecurity professionals responsible for defending systems and responding to threats. |
| Client Infrastructure | An organization's networks, servers, devices, and applications that require protection. |
| Visibility | The ability to monitor systems, network traffic, logs, and alerts to identify potential security issues. |
| Threat | A potential danger, such as malware or an attacker, that could compromise systems or data. |
| Prevention | Security measures designed to stop attacks before they cause damage. |
| Detection | Identifying suspicious or malicious activity through monitoring and security tools. |
| Mitigation | Actions taken to limit the impact of an identified threat. |
| Risk | The likelihood and potential impact of a threat exploiting a vulnerability. |

---

## 6. Key Takeaways

Completing this room helped reinforce the importance of understanding an organization's infrastructure before attempting to defend it.

Key concepts learned:

- Defensive security focuses on protecting the confidentiality, integrity, and availability of organizational systems and information.
- Blue Teams rely on visibility through system logs, network traffic, and security alerts to identify suspicious activity.
- Understanding client infrastructure helps defenders determine which assets require protection and where security controls should be implemented.
- Attackers can move laterally between compromised systems, making it important to understand potential attack paths.
- Prevention, detection, mitigation, analysis, and response are essential components of an effective defensive security strategy.
- Layered security controls provide multiple opportunities to prevent or limit successful attacks.

**Overall:** This room established a foundation for understanding the Blue Team's role in cybersecurity and how defenders approach protecting organizational infrastructure against evolving threats.

---

## Skills & Concepts

`Defensive Security` `Blue Team` `CIA Triad` `Threat Detection` `Risk Assessment` `Network Monitoring` `Incident Response` `Attack Paths` `Security Controls` `Infrastructure Security`

