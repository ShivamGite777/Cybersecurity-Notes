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
