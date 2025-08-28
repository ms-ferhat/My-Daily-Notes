
> Active Directory (AD) is a directory service for Windows network environments. It is a distributed, hierarchical structure that allows for centralized management of an organization's resources.


__Active Directory Domain Services (AD DS)__ 
gives an organization ways to store directory data and make it available to both standard users and administrators on the same network.

__Active Directory Structure__
```shell-session
INLANEFREIGHT.LOCAL/
├── ADMIN.INLANEFREIGHT.LOCAL
│   ├── GPOs
│   └── OU
│       └── EMPLOYEES
│           ├── COMPUTERS
│           │   └── FILE01
│           ├── GROUPS
│           │   └── HQ Staff
│           └── USERS
│               └── barbara.jones
├── CORP.INLANEFREIGHT.LOCAL
└── DEV.INLANEFREIGHT.LOCAL
```

## Definitions

> [!info]- __Object__
An object can be defined as ANY resource present within an Active Directory environment such as OUs, printers, users, domain controllers, etc.

> [!info]-  Attributes
Every object in Active Directory has an associated set of [attributes](https://docs.microsoft.com/en-us/windows/win32/adschema/attributes-all) used to define characteristics of the given object.

> [!info]-  Schema
The Active Directory [schema](https://docs.microsoft.com/en-us/windows/win32/ad/schema) is essentially the blueprint of any enterprise environment. It defines what types of objects can exist in the AD database and their associated attributes. It lists definitions corresponding to AD objects and holds information about each object.

> [!info]- __Domain__
> A domain is a logical group of objects such as computers, users, OUs, groups, etc. We can think of each domain as a different city within a state or country. Domains can operate entirely independently of one another or be connected via trust relationships.

> [!info]- __Forest__
> A forest is a collection of Active Directory domains


## Active Directory Functionality

| **Roles**                  | **Description**                                                                                                                                                                                                                                                                                                    |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Schema Master`            | This role manages the read/write copy of the AD schema, which defines all attributes that can apply to an object in AD.                                                                                                                                                                                            |
| `Domain Naming Master`     | Manages domain names and ensures that two domains of the same name are not created in the same forest.                                                                                                                                                                                                             |
| `Relative ID (RID) Master` | The RID Master assigns blocks of RIDs to other DCs within the domain that can be used for new objects. The RID Master helps ensure that multiple objects are not assigned the same SID. Domain object SIDs are the domain SID combined with the RID number assigned to the object to make the unique SID.          |
| `PDC Emulator`             | The host with this role would be the authoritative DC in the domain and respond to authentication requests, password changes, and manage Group Policy Objects (GPOs). The PDC Emulator also maintains time within the domain.                                                                                      |
| `Infrastructure Master`    | This role translates GUIDs, SIDs, and DNs between domains. This role is used in organizations with multiple domains in a single forest. The Infrastructure Master helps them to communicate. If this role is not functioning properly, Access Control Lists (ACLs) will show SIDs instead of fully resolved names. |


## AD Protocols

### Kerbores

![[Pasted image 20250426095415.png]]

### DNS

![[Pasted image 20250426095807.png]]




## NTLM Authentication


### NTHash (NTLM)

![[Pasted image 20250426102049.png]]

## AD Objects

> [!info] __User__
>  Users are one of the objects known as **security principals**, meaning that they can be authenticated by the domain and can be assigned privileges over **resources** like files or printers.

> [!info] __Machine__
> machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

> [!info] __Group__
> Groups can have both users and machines as members. If needed, groups can include other groups as well.


### Some Define Groups in AD

|   |   |
|---|---|
|**Security Group**|**Description**|
|Domain Admins|Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs.|
|Server Operators|Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.|
|Backup Operators|Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.|
|Account Operators|Users in this group can create or modify other accounts in the domain.|
|Domain Users|Includes all existing user accounts in the domain.|
|Domain Computers|Includes all existing computers in the domain.|
|Domain Controllers|Includes all existing DCs on the domain.|
