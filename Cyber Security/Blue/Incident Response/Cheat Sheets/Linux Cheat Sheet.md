
## User Accounts
- Identify curious-looking accounts in `/etc/passwd`
- **Related Commands:**
  - `passwd -S [User_Name]`
  - `grep :0: /etc/passwd`
  - `find / -nouser -print`

## Log Entries
- Identify suspicious events such as:
  - Large number of authentication or login failures (e.g., `telnetd`, `sshd`, etc.)
  - Overly long and strange-looking strings being passed as input (possible buffer overflow attempts)

## Resources
- Identify deviations from normal resource utilization  
- **Related Commands:**
  - **System CPU Load ("load average")**:  
    ```bash
    uptime  # Compare this to a baseline
    ```
  - **Memory Utilization**:  
    ```bash
    free  # Compare this to a baseline
    ```

## Running Processes (Focus on those running with root privileges)
- Identify abnormal processes that could indicate malicious activity  
- **Related Commands:**
  - `ps aux`
  - `lsof -p [pid]` (for more details)

## Services
- Identify abnormal services  
- **Related Commands:**
  - `service --status-all` (For RedHat and Mandrake, use `chkconfig --list` instead)

## Scheduled Tasks (Focus on cron jobs configured by root or any UID 0 account)
- Identify suspicious scheduled tasks  
- **Related Commands:**
  - `crontab -l -u [account]`
  - `cat /etc/crontab`
  - `cat /etc/cron.*`

## Listening and Active TCP/UDP Ports
- Identify abnormal listening and active TCP/UDP ports  
- **Related Commands:**
  - `lsof -i` (Compare this to a baseline)
  - `netstat -nap` (Compare this to a baseline)

## ARP
- Identify abnormal IP–MAC mappings  
- **Related Command:**
  ```bash
  arp -a  # Compare this to a baseline
