
## Logging Overview

**Used of logs**
- **Incident Response**: Logs can show when and how the attack occurred
- **Threat Hunting**: Logs allow you to search for signs of malicious activity
- **Alerting and Triage**: Logs are a building block of any alert or detection rule

>[!info]- Location of logs on windows is 
>`C:\Windows\System32\winevt\Logs`


## Security Log: Authentication


**The most important Authentication event ID**

|**Event ID**|**Purpose**|**Logging**|**Limitations**|
|---|---|---|---|
|**4624  <br>**(Successful Logon)|Detect suspicious RDP/network logins and identify the attack starting point|Logged on the target machine, the one you are trying to access|**Noisy**. You will see hundreds of logon events per minute on loaded servers|
|**4625  <br>**(Failed Logon)|Detect brute force, password spraying, or vulnerability scanning|Logged on the target machine, the one you are trying to access|**Inconsistent**. The logs have lots of caveats that may trick you into the wrong understanding of the event|


## Security Log: User Management

**The most important User Management event ID**

| **Event ID**                   | **Description**                                                | **Malicious Usage**                                                                                                                                                                                        |
| ------------------------------ | -------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **4720** / **4722** / **4738** | A user account was  <br>created / enabled / changed            | Attackers might create a backdoor account or even enable an old one to avoid detection                                                                                                                     |
| **4725** / **4726**            | A user account was  <br>disabled / deleted                     | In some advanced cases, threat actors may disable privileged SOC accounts to slow down their actions                                                                                                       |
| **4723** / **4724**            | A user changed their password /  <br>User's password was reset | Given enough permissions, threat actors might reset the password and then access the required user                                                                                                         |
| **4732** / **4733**            | A user was added to /  <br>removed from a security group       | Attackers often add their backdoor accounts to privileged groups like "[Administrators](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups#administrators)" |


### Structure of User Management Events

1. **Subject**: The account doing the action. Note the Logon ID field - you can use it to correlate this event with the preceding 4624 login event!
2. **Object**: This can be named differently depending on an event ID (e.g. New Account or Member), but it always means the same - the target of the action.
3. **Details**: A target group for 4732 and 4733 events, or new user's attributes like full name or password expiration settings for the 4720 event.

![[Pasted image 20250705141557.png]]