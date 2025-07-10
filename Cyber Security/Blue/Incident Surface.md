
## Linux Incident Surface

> [!info]- Linux Attack Surface
> The Linux Attack Surface refers to all the points of interaction in a Linux system where an adversary might attempt to exploit vulnerabilities to gain unauthorized access or carry out malicious activities.

> [!info]- Linux Incident Surface
> The Linux Incident Surface, on the other hand, refers to all the system areas involved in the detection, management, and response to an actual security incident (post-compromise). It includes where security breaches may be detected and analyzed and where a response plan must be implemented to mitigate the incident.

### 1. Processes and network communication

we could used some Linux commands to investee process.

1. `ps aux`: to show all process
2. `lofs`: to show process details
3. `OSquereyi` to show process details


### 2. Persistence

#### Method 1: create account

> Attack could ensure persistence by create new account on the system.

**Investigation method**
1. **search inside ath.log about create new user.**
```
	cat auth.log | grep useradd
```
2. **Examining /etc/passwd File**
```
	cat /etc/passwd
```

#### Method 2: Cron Job

> Attacker could create scheduler task run every timer interval or with reboot to ensure persistence

**Investigation method**
1. **Examining Malicious Cronjobs**
```
	ls /var/spool/cron/crontabs/[username]
```


#### Method 3: Services

> Another way to achieve persistence on a compromised system is installing a service

**Investigation Methods**
1. **Reviewing the Directory**
```
	ls /etc/systemd/system
```
2. **Evidence in the Logs**
```
	cat /var/log/syslog
```
3. **Examining  Journalctl**
```
	sudo journalctl -u suspicious
```