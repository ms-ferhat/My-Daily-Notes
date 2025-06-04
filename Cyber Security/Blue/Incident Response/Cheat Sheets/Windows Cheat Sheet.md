
### User Accounts
- Identify curious-looking accounts in the Administrators group __use lusrmgr.msc for GUI access__
- Related Command: `net user`
- Related Command: `net localgroup administrators`
### Processes (focus on those running with high privileges)
- Identify abnormal processes __use taskmgr.exe for GUI access__
- Related Command: `tasklist`
-  Related Command: `wmic process list full`
-  Related Command: `wmic process get name,parentprocessid,processid`
-  Related Command: `wmic process where processid=[pid] get commandline`
### Services
- Identify abnormal services  __use services.msc for GUI access__
-  Related Command: `net start`
-  Related Command: `sc query | more`
-  Related Command (associate running services with processes): `tasklist /svc`

### Scheduled Tasks

- Identify curious-looking scheduled tasks.
    - Navigate to: `Start -> Programs -> Accessories -> System Tools -> Scheduled Tasks` (GUI access).
- **Related Command:**

    ```sh
    schtasks
    ```


### Extra Startup Items

- Identify users’ autostart folders.
- **Related Commands:**
    
    ```sh
    dir /s /b "C:\Documents and Settings\[username]\Start Menu\"
    dir /s /b "C:\Users\[username]\Start Menu\"
    ```
    

### Auto-start Registry Key Entries

- Check the following registry keys for malicious autorun configurations:
    - `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`
    - `HKLM\Software\Microsoft\Windows\CurrentVersion\Runonce`
    - `HKLM\Software\Microsoft\Windows\CurrentVersion\RunonceEx`
- **Related Command:**
    
    ```sh
    reg query [reg key]
    ```
    
- Alternative: Use **Autoruns** MS tool to inspect every auto-start location.

### Listening and Active TCP and UDP Ports

- Identify abnormal listening and active TCP and UDP ports.
- **Related Command:**
    
    ```sh
    netstat –nao 10
    ```
    

### File Shares

- Ensure all available file shares are justified.
- **Related Command:**
    
    ```sh
    net view \\127.0.0.1
    ```
    

### Files

- Identify major decreases in free space.
- **Tip:** Use File Explorer’s search box and enter:
    
    ```
    size:>5M
    ```
    

### Firewall Settings

- Examine current firewall settings to detect abnormalities from a baseline.
- **Related Commands:**
    - **Windows XP/2003:**
        
        ```sh
        netsh firewall show config
        ```
        
    - **Vista - Windows 8+**
        
        ```sh
        netsh advfirewall show currentprofile
        ```
        

### Systems Connected to the Machine

- Identify **NetBIOS over TCP/IP** activity.
- **Related Command:**
    
    ```sh
    nbtstat –S
    ```
    

### Open Sessions

- Determine who has an open session with a machine.
- **Related Command:**
    
    ```sh
    net session
    ```
    

### Sessions with Other Systems (NetBIOS/SMB)

- Identify active sessions the machine has with other systems.
- **Related Command:**
    
    ```sh
    net use
    ```
    

### Log Entries

- Identify suspicious log events.
- **GUI Access:**
    - Open **Event Viewer** (`eventvwr.msc`).
- **Related Command:**
    
    ```sh
    wevtutil qe security
    ```