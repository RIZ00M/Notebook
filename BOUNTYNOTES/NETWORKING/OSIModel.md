**# OSI (Open Systems Interconnection)\[cite: 1]**



**## Layers\[cite: 1]**

**1. Physical Layer\[cite: 1]**

**2. Data Link Layer\[cite: 1]**

**3. Network Layer\[cite: 1]**

**4. Transport Layer\[cite: 1]**

**5. Session Layer\[cite: 1]**

**6. Presentation Layer\[cite: 1]**

**7. Application Layer\[cite: 1]**



**> \*\*Mnemonic:\*\* \*\*P\*\*lease \*\*D\*\*o \*\*N\*\*ot \*\*T\*\*ouch \*\*S\*\*omebody’s \*\*P\*\*urple \*\*A\*\*pe\[cite: 1]**



**---**



**## MAC Address Breakdown\[cite: 1]**

**\* \*\*`a4:c3:f0`\*\* - Intel (vendor)\[cite: 1]**

**\* \*\*`85:ac:2d`\*\* - Network interface (unique address)\[cite: 1]**



**!\[WireShark MAC Address](assets/WireSharkMacAddress.jpg)**

**!\[MAC Address Structure](assets/MACAddress.png)**

**!\[IP Breakdown](assets/IPBreakdown.png)**



**---**



**## OSI Model Layers Overview\[cite: 1]**



**| Layer | Name | Function | Examples | Notes |**

**|---|---|---|---|---|**

**| \*\*Layer 7\*\* | Application layer | Providing services and interfaces to applications\[cite: 1] | HTTP, FTP, DNS, POP3, SMTP, IMAP\[cite: 1] | Serves the network directly to end user applications, i.e hypertext transfer protocol.\[cite: 1] |**

**| \*\*Layer 6\*\* | Presentation layer | Data encoding, encryption, and compression\[cite: 1] | Unicode, MIME, JPEG, PNG, MPEG\[cite: 1] | Ensures data is delivered in an understandable format.\[cite: 1] |**

**| \*\*Layer 5\*\* | Session layer | Establishing, maintaining, and synchronising sessions\[cite: 1] | NFS, RPC\[cite: 1] | Establishes and maintains communication. I.e Network File System and Remote Procedure call.\[cite: 1] |**

**| \*\*Layer 4\*\* | Transport layer | End-to-end communication and data segmentation\[cite: 1] | UDP, TCP\[cite: 1] | Enables end to end communication, i.e Transmission Control Protocol and User Datagram Protocol.\[cite: 1] |**

**| \*\*Layer 3\*\* | Network layer | Logical addressing and routing between networks\[cite: 1] | IP, ICMP, IPSec\[cite: 1] | Sends the data between two nodes.\[cite: 1] |**

**| \*\*Layer 2\*\* | Data link layer | Reliable data transfer between adjacent nodes\[cite: 1] | Ethernet (802.3), WiFi (802.11)\[cite: 1] | Contains the protocol to enable data transfer.\[cite: 1] |**

**| \*\*Layer 1\*\* | Physical layer | Physical data transmission media\[cite: 1] | Electrical, optical, and wireless signals\[cite: 1] | Contains physical connection between devices.\[cite: 1] |**



**---**



**## Protocol Ports**



**!\[Port Table](assets/PortTable.png)**



**---**



**## HTML Injection Payloads**



**!\[HTML Injection](assets/image\_262d03.png)**



**### How It Works**

**If user input is placed directly into a page without sanitisation, you can inject your own HTML/JavaScript, which the browser will then render or execute.**



**1. User types information into an input field.**

**2. The input is used in a JavaScript function to show the name on the page.**

**3. Because no input is sanitised, you can write your own HTML or JavaScript, and it will be used on the page.**



**### Payloads**



**#### Inject a Link**

**```html**

**<a href="url">link text</a>**

