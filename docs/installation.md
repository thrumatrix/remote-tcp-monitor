# Installation Guide

This guide explains how to install and deploy **Remote TCP Monitor** and its core agent component, **TCPv Service**, across various environments.

---

## 1. Remote TCP Monitor (UWP App)

The main application is distributed via Microsoft Store.  
To install, visit the appropriate version link:

- [Trial Version](https://apps.microsoft.com/detail/9N9VFVV2KVJG?hl=en-us&gl=CN&ocid=pdpshare)
- [Standard Edition](https://apps.microsoft.com/detail/9N0M98DCR26T?hl=en-us&gl=CN&ocid=pdpshare)
- [Pro Edition](https://apps.microsoft.com/detail/9P4GP7TWN8ML?hl=en-us&gl=CN&ocid=pdpshare)

---

## 2. Remote TCP Monitor (Win32 App)

The Win32 version of Remote TCP Monitor is available from the official Toposoft download portal:

🔗 [Download from Toposoft](https://ort.toposoft.top:8882/downloads.html)

- Includes `.msi` installer for traditional desktop environments
- **Trial version** is free to use
- **Standard** and **Pro** editions require activation and include lifetime updates and support

> ⚠️ Some antivirus software (e.g., Windows Defender) may falsely flag the installer as malicious (e.g., *Trojan:Script/Wacatac.B!ml*).  
> This is a known false positive. Please verify the installer using SHA256 checksum if needed.  
> See [Microsoft's explanation](https://learn.microsoft.com/en-us/answers/questions/465937/msi-is-detected-by-windows-defender-and-it-shows-t) for more details.

---

## 3. TCPv Service (Agent Component)

**TCPv Service** is a core agent responsible for collecting TCP and UDP connection data from remote hosts. It supports both **automatic deployment** and **manual installation**, depending on your network environment.

### 🔄 Automatic Installation

When registering a client:

- If the **"Lightweight Connection"** option is **not selected**, the TCPv service will be **automatically installed** on the remote computer.
- No user intervention is required.

### 🔔 Local Update Prompt

If an outdated version of TCPv service is detected on the local machine:

- The system will prompt the user to update when initiating local monitoring.
- **UAC confirmation** is required to proceed.

---

### 🛠 Manual Installation

Manual installation is recommended for:

- Cross-subnet or Internet hosts
- Devices behind firewalls or with restricted network access
- Environments with third-party antivirus or strict policies

#### 📁 Step 1: Copy the Service Executable

Copy `tcpvsvc.exe` from the local installation path to any accessible folder on the target computer.

**Typical source paths:**

- **Win32 App**  
  ```
  C:\Program Files\Remote TCP Monitor Aio\ort\services\tcpvsvc.exe
  ```

- **UWP App**  
  *(Replace `5.0.379.0` with the actual version number)*  
  - **Standard Edition**  
    ```
    C:\Program Files\WindowsApps\29910XieShidong.RemoteTCPMonitor_5.0.379.0_x64__02gh7fjn484g8\ORT\services\tcpvsvc.exe
    ```
  - **Pro Edition**  
    ```
    C:\Program Files\WindowsApps\29910XieShidong.RemoteTCPMonitorPro_5.0.379.0_x64__02gh7fjn484g8\ORT\services\tcpvsvc.exe
    ```
  - **Trial Edition**  
    ```
    C:\Program Files\WindowsApps\29910XieShidong.RemoteTCPMonitorTrial_5.0.379.0_x64__02gh7fjn484g8\ORT\services\tcpvsvc.exe
    ```

#### ⚙️ Step 2: Run Installation Command

On the target computer, open **Command Prompt as Administrator**, then run:

```
tcpvsvc.exe -is
```

To uninstall the service, run:

```
tcpvsvc.exe -u
```

---

### ✅ When to Use Manual Installation

Manual deployment is ideal when:

- Automatic installation is blocked by security software
- Remote access policies prevent agent push
- You require controlled, auditable deployment steps

Ensure the TCPv service is running properly to enable full monitoring capabilities.

---
