## CIA Key Security Concepts

- **Confidentiality** - Protects data from unauthorised disclosure
- **Integrity** - Ensure data is accurate and unmodified
- **Availability** - Systems and data are accessible when needed

- **Authenticity** - Verifies the identity of users and data sources
- **Accountability** - Actions can be traced to a responsible entity
---
Including hardware, software, firmware and information being stored, processed and communicated.

| Resource                         | Availability                                                                                 | Confidentiality                                                                                     | Integrity                                                                                         |
| -------------------------------- | -------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Hardware                         | Equipment is stolen or disabled, thus denying service.                                       | An unencrypted CD-ROM or DVD is stolen.                                                             | —                                                                                                 |
| Software                         | Programs are deleted, denying access to users.                                               | An unauthorized copy of software is made.                                                           | A working program is modified to cause it to fail during execution or perform an unintended task. |
| Data                             | Files are deleted, denying access to users.                                                  | An unauthorized read of data is performed. An analysis of statistical data reveals underlying data. | Existing files are modified or new files are fabricated.                                          |
| Communication Lines and Networks | Messages are destroyed or deleted. Communication lines or networks are rendered unavailable. | Messages are read. The traffic pattern of messages is observed.                                     | Messages are modified, delayed, reordered, or duplicated. False messages are fabricated.          |
## Levels of Impact

**Low Impact**
A limited adverse effect on operations, assets or individuals. Systems may experience degraded performance but core functions remain. Examples: **minor data exposure, brief service disruption**

**Moderate Impact**
A serious adverse effect. Significant degradation of capabilities, financial loss or harm to individuals is likely. Examples: **breach of a departmental database, extended system downtime.**

**High Impact**
A severe or catastrophic effect. Critical functions are lost, major financial damage occurs, or individual safety is jeopardised. Examples: **National infrastructure breach, large scale exfiltration.**

## Computer Security Problems and Assets

| No. | Challenge                          | Implication                                       | Example                                                                                |
| --- | ---------------------------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------- |
| 1   | Security is not simple             | Requires layered, detailed strategies             | Passwords alone are not enough; firewalls, encryption, and monitoring are also needed. |
| 2   | Must consider potential attacks    | Designs must anticipate threats                   | Strong encryption is useless if passwords are weak.                                    |
| 3   | Procedures may be counterintuitive | Security feels inconvenient but necessary         | Multi-factor authentication adds steps but helps prevent breaches.                     |
| 4   | Placement matters                  | Wrong placement weakens defenses                  | A firewall in the wrong network segment offers little protection.                      |
| 5   | Involves more than algorithms      | Managing secret information is critical           | Encryption is useless if keys are leaked.                                              |
| 6   | Attackers need only one weakness   | Defense must cover all gaps                       | One unpatched vulnerability can compromise a system.                                   |
| 7   | Often an afterthought              | Systems are weaker if security is bolted on later | Adding security after application development can create loopholes.                    |
| 8   | Requires constant monitoring       | Must adapt to evolving threats                    | Log monitoring, intrusion detection, and patch updates.                                |
| 9   | Undervalued until failure          | Organizations act only after breaches             | Companies invest in security only after a cyberattack.                                 |
| 10  | Seen as a burden                   | Strong security reduces usability                 | Users resist long passwords or frequent logins.                                        |

|Component|Description|Threats|
|---|---|---|
|Hardware|Physical components including CPUs, servers, routers, and storage devices.|Theft, vandalism, and environmental damage.|
|Software|Operating systems, applications, and utilities.|Malware infection, unauthorised modification, and software vulnerabilities.|
|Data|Files, databases, and communications in transit or at rest.|Exfiltration, corruption, and destruction.|
|Networks|Communication links and network infrastructure.|Eavesdropping, packet tampering, denial-of-service attacks, and unauthorised access.|

|Resource|Confidentiality|Integrity|Availability|Authenticity|Accountability|
|---|---|---|---|---|---|
|Hardware|Restrict physical access|Ensure devices aren't tampered with|Maintain redundant systems and backups|Verify trusted devices|Track device use and maintenance logs|
|Software|Limit unauthorised use|Prevent code modification|Patch vulnerabilities to maintain uptime|Verify legitimate software sources|Log software installations and updates|
|Data|Encrypt sensitive data|Prevent unauthorised changes|Backup and recovery processes|Verify data origin using digital signatures|Track who accessed or modified data|
|Networks|Secure transmissions (VPN, TLS)|Detect packet tampering|Keep network services online|Authenticate users and devices|Monitor network traffic and log access|
## Vulnerabilities, Threats and Attacks

|Category|Type|Description|Example|
|---|---|---|---|
|Vulnerabilities|Corrupted|Loss of integrity; data or system state is altered.|Data is modified without authorisation.|
|Vulnerabilities|Leaky|Loss of confidentiality; information is disclosed without authorisation.|Sensitive information is exposed.|
|Vulnerabilities|Unavailable or slow|Loss of availability; services cannot be accessed or respond too slowly.|A website becomes unavailable.|
|Threats|General|Capable of exploiting one or more vulnerabilities and represent potential security harm to an asset.|An attacker targets an unpatched system.|
|Attacks|Passive|Attempt to learn or use information without affecting system resources.|Eavesdropping or traffic analysis.|
|Attacks|Active|Attempt to alter system resources or affect their operation.|Replay, masquerade, or denial-of-service attacks.|
|Attacks|Insider|Initiated by an entity within the security perimeter.|An employee accesses confidential files without permission.|
|Attacks|Outsider|Initiated from outside the security perimeter.|An external hacker attempts to access a network.|

| Threat Consequence      | Definition                                                           | Threat Actions (Attacks)                                                                                                                                                                                                                                              |
| ----------------------- | -------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Unauthorized Disclosure | When an entity gains access to data for which it is not authorized.  | **Exposure:** Sensitive data is directly released.  <br>**Interception:** Unauthorized access to data in transit.  <br>**Inference:** Indirect access to sensitive data (e.g., deducing from patterns).  <br>**Intrusion:** Circumventing protections to access data. |
| Deception               | An authorized entity receives false data and believes it to be true. | **Masquerade:** Attacker pretends to be an authorized entity.  <br>**Falsification:** Inserting false data.  <br>**Repudiation:** Denying responsibility for an action.                                                                                               |
| Disruption              | Interrupts or prevents the correct operation of system services.     | **Incapacitation:** Disables a system component.  <br>**Corruption:** Modifies system functions or data undesirably.  <br>**Obstruction:** Interrupts or hinders system service delivery.                                                                             |
| Usurpation              | Unauthorized control of system services or functions.                | **Misappropriation:** Unauthorized control of a resource.  <br>**Misuse:** Making the system perform harmful or unintended actions.                                                                                                                                   |

|Passive Attack|Active Attack|
|---|---|
|Attempts to learn or use information from the system without affecting system resources.|Attempts to alter system resources or affect their operation.|
|Eavesdropping on or monitoring transmissions.|Involves modifying the data stream or creating a false stream.|
|**Goal:** Obtain information that is being transmitted.|**Goal:** Change, disrupt, or manipulate system operations or data.|
|**Two types:**|**Four categories:**|
|1. Release of message contents|1. Replay|
|2. Traffic analysis|2. Masquerade|
||3. Modification of messages|
||4. Denial of service|

## Attack Surfaces
| Attack Surfaces - Examples                                                                                          |
| ------------------------------------------------------------------------------------------------------------------- |
| Open ports on outward-facing web and other servers, and code listening on those ports                               |
| Services available on the inside of a firewall                                                                      |
| Code that processes incoming data, email, XML, office documents, and industry-specific custom data exchange formats |
| Interfaces, SQL, and web forms                                                                                      |
| An employee with access to sensitive information who is vulnerable to a social engineering attack                   |

|Attack Surface Category|Description|Examples|
|---|---|---|
|Network Attack Surface|Vulnerabilities over an enterprise network, wide-area network, or the Internet.|Network protocol vulnerabilities, denial-of-service attacks, disruption of communications links, and intruder attacks.|
|Software Attack Surface|Vulnerabilities in application, utility, or operating system code.|Web server software vulnerabilities.|
|Human Attack Surface|Vulnerabilities created by personnel or outsiders.|Social engineering, human error, and trusted insiders.|

## Standards

**Standards have been developed to cover management**  
**practices and the overall architecture of security**  
**mechanisms and services**  
• The most important of these organizations are:  
• National Institute of Standards and Technology (NIST)  
• NIST is a U.S. federal agency that deals with measurement science,  
standards, and technology related to U.S. government use and to the  
promotion of U.S. private sector innovation  

**Internet Society (ISOC)**  
• ISOC is a professional membership society that provides leadership in  
addressing issues that confront the future of the Internet, and is the  
organization home for the groups responsible for Internet  
infrastructure standards  

**International Telecommunication Union (ITU-T)**  
• ITU is a United Nations agency in which governments and the private  
sector coordinate global telecom networks and services  
• International Organization for Standardization (ISO)  
• ISO is a nongovernmental organization whose work results in  
international agreements that are published as International  
Standards