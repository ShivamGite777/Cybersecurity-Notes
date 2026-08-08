### Windows Defender Firewall

Windows Firewall protects a Windows system by controlling **incoming and outgoing network traffic**.
What is a firewall?

Per Microsoft, "Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit".

## Firewall Profiles

Windows has **3 firewall profiles**:

| Profile | Used For |
|---|---|
| **Domain** | Network where the computer can authenticate with a domain controller |
| **Private** | Trusted networks, such as home networks |
| **Public** | Untrusted networks, such as airports, cafés, public Wi-Fi |

##  Firewall Options

Each profile can have options to:

- **Turn Firewall ON/OFF**
- **Block all incoming connections**

Keep Windows Firewall **enabled** unless you know exactly what you're doing.

## Allow an App Through Firewall

You can control which applications are allowed through the firewall.
An application can be allowed on:

- **Private networks**
- **Public networks**
- Both

## Advanced Settings

**Advanced Firewall Settings** provide more detailed control over firewall rules.

Used mainly by:

- System Administrators
- Network Administrators
- Security Professionals

## 🖥️ Open Windows Firewall

Run:

```cmd
WF.msc
```

##  Cybersecurity Takeaway

> **Windows Firewall controls network traffic and helps prevent unauthorized network connections to the Windows system.**

```text
Network Traffic
      ↓
Windows Firewall
      ↓
Allow ✅ / Block ❌
```
   
### Windows Firewall — App Access & Advanced Settings

##  Allow an App Through Firewall

Windows Firewall allows you to control which applications can communicate through the network.

Apps can have different permissions for:

- **Private** networks
- **Public** networks

Example:

```text
App.exe
├── Private → ✅ Allowed
└── Public  → ❌ Blocked
```
<img width="783" height="525" alt="image" src="https://github.com/user-attachments/assets/f423244f-be3d-4a71-b868-3030f87cf7da" />

### Details

The **Details** button may provide additional information about the application.

---

## ⚙️ Advanced Settings
<img width="1041" height="736" alt="image" src="https://github.com/user-attachments/assets/90c6d2c5-a242-46b4-a50f-5dac3606378d" />

Advanced Settings provides detailed control over Windows Firewall rules.

You can configure:

- **Inbound Rules** → Control incoming connections
- **Outbound Rules** → Control outgoing connections

```text
Network Traffic
      ↓
Firewall Rules
      ↓
Allow ✅ / Block ❌
```
### Microsoft Defender SmartScreen

**SmartScreen** is a Windows security feature that helps protect against:

- Phishing websites
- Malicious websites
- Malicious applications
- Potentially dangerous downloads

## SmartScreen Settings
<img width="533" height="629" alt="image" src="https://github.com/user-attachments/assets/54d1cf7c-1543-45a5-a375-5b907df85b9d" />

SmartScreen can be set to:

```text
Warn  → Warns the user about suspicious content
Block → Blocks the suspicious content
Off   → Disables SmartScreen ⚠️
```
## Check Apps and Files

SmartScreen checks **unrecognized apps and files downloaded from the web**.

```text
Download App/File
       ↓
SmartScreen checks it
       ↓
Safe → Allow
Suspicious → Warn / Block
```

> **Purpose:** Helps prevent users from running malicious or untrusted files.

## Exploit Protection

**Exploit Protection** is a built-in Windows security feature that helps protect Windows and applications against **exploitation attacks**.

```text
Application
     ↓
Exploit Attempt
     ↓
Exploit Protection
     ↓
Helps prevent the attack
```
<img width="492" height="695" alt="image" src="https://github.com/user-attachments/assets/ca1cc494-08b8-4c93-880a-2bf24c2f7c9b" />
> **SmartScreen → Protects against malicious websites, apps & downloads.**

> **Exploit Protection → Helps protect applications from exploitation attacks.**

## Cybersecurity Takeaway

```text
SmartScreen
   → Phishing
   → Malicious websites
   → Suspicious apps
   → Dangerous downloads

Exploit Protection
   → Software exploitation
   → Attack techniques
```
