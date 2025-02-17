
# Introduction to Windows Forensics

> [!info] __Forensic Artifacts__
>  Forensic artifacts are essential pieces of information that provide evidence of human activity.


__1. What is the most used Desktop Operating System right now?__
```
Answer: Microsoft Windows
```

# Windows Registry and Forensics

> [!info] __The Registry__
> The Windows Registry is a collection of databases that contains the system's configuration data.

The registry on any Windows system contains the following five root keys:

1. HKEY_CURRENT_USER
2. HKEY_USERS
3. HKEY_LOCAL_MACHINE
4. HKEY_CLASSES_ROOT
5. HKEY_CURRENT_CONFIG

![[Pasted image 20250118090203.png]]

__2. What is the short form for HKEY_LOCAL_MACHINE?__
```
Answer: HKLM
```



# Accessing registry hives offline

 if you only have access to a disk image, you must know where the registry hives are located on the disk. The majority of these hives are located in the `C:\Windows\System32\Config` directory and are:

1. **DEFAULT** (mounted on `HKEY_USERS\DEFAULT`)
2. **SAM** (mounted on `HKEY_LOCAL_MACHINE\SAM`)
3. **SECURITY** (mounted on `HKEY_LOCAL_MACHINE\Security`)
4. **SOFTWARE** (mounted on `HKEY_LOCAL_MACHINE\Software`)
5. **SYSTEM** (mounted on `HKEY_LOCAL_MACHINE\System`)


__3. What is the path for the five main registry hives, DEFAULT, SAM, SECURITY, SOFTWARE, and SYSTEM?__
```
Answer: C:\Windows\System32\Config
```

__4. What is the path for the AmCache hive?__
```
Answer: C:\Windows\AppCompat\Programs\Amcache.hve
```

# Data Acquisition

For acquiring these files, we can use one of the following tools:
1. Kape
2. Autopsy
3. FTKimager


__5. Try collecting data on your own system or the attached VM using one of the above mentioned tools__
```
NO Answer Needed
```

# Exploring Windows Registry

Once we have extracted the registry hives, we need a tool to view these files as we would in the registry editor. Since the registry editor only works with live systems and can't load exported hives, we can use the following tools:  

1. **Registry Viewer:**
2. **Zimmerman's Registry Explorer**
3.  **RegRipper**


__6. Study the above material to understand the difference between the different tools__
```
NO Answer Needed
```

# System Information and System Accounts

## **OS Version:**

 To find the OS version, we can use the following registry key:
 `SOFTWARE\Microsoft\Windows NT\CurrentVersion`

## **Current control set:**

1. `SYSTEM\ControlSet001`
2. `SYSTEM\ControlSet002`
3. `HKLM\SYSTEM\CurrentControlSet`
4. `SYSTEM\Select\LastKnownGood`

## **Computer Name:**

- `SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`

## **Time Zone Information:**

- `SYSTEM\CurrentControlSet\Control\TimeZoneInformation`

## **Network Interfaces and Past Networks:**

1. `SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces`
2. `SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Unmanaged`
3. `SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Managed`

## **AutoStart Programs (Autoruns):**

1. `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`
2. `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`
3. `SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`
4. `SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run`
5. `SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
6. `SYSTEM\CurrentControlSet\Services`

## **SAM hive and user information:**

- `SAM\Domains\Account\Users`


## Answer the questions below

__7. What is the Current Build Number of the machine whose data is being investigated?__
```
Answer: 19044
```

__8. Which ControlSet contains the last known good configuration?__
```
Answer: 1
```

__9. What is the Computer Name of the computer?__
```
Answer: THM-4n6
```

__10. What is the value of the TimeZoneKeyName?__
```
Answer: Pakistan Standard Time
```

__11. What is the DHCP IP address__
```
Answer: 192.168.100.58
```

__12. What is the RID of the Guest User account?__
```
Answer: 501
```


# Usage or knowledge of files/folders

## **Recent Files:**

1. `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs`
2. `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.pdf`

## **Office Recent Files:**

1. `NTUSER.DAT\Software\Microsoft\Office\VERSION`
2. `NTUSER.DAT\Software\Microsoft\Office\15.0\Word`
3. `NTUSER.DAT\Software\Microsoft\Office\VERSION\UserMRU\LiveID_####\FileMRU`


## **ShellBags:**

1. `USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\Bags`
2. `USRCLASS.DAT\Local Settings\Software\Microsoft\Windows\Shell\BagMRU`
3. `NTUSER.DAT\Software\Microsoft\Windows\Shell\BagMRU`
4. `NTUSER.DAT\Software\Microsoft\Windows\Shell\Bags`

## **Open/Save and LastVisited Dialog MRUs:**

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePIDlMRU`
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\LastVisitedPidlMRU`

## **Windows Explorer Address/Search Bars:**

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\TypedPaths`
`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\WordWheelQuery`


## Answer the questions below

__13. When was EZtools opened?__
```
Answer: 2021-12-01 13:00:34
```

__14. At what time was My Computer last interacted with?__
```
Answer: 2021-12-01 13:06:47
```

__15. What is the Absolute Path of the file opened using notepad.exe?__
```
Answer: C:\Program Files\Amazon\Ec2ConfigService\Settings
```

__16. When was this file opened?__
```
2021-11-30 10:56:19
```


# Evidence of Execution

## **UserAssist**:

`NTUSER.DAT\Software\Microsoft\Windows\Currentversion\Explorer\UserAssist\{GUID}\Count`

## **ShimCache:**

`SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache`


## **AmCache:**

`Amcache.hve\Root\File\{Volume GUID}\`

## **BAM/DAM:**

`SYSTEM\CurrentControlSet\Services\bam\UserSettings\{SID}`
`SYSTEM\CurrentControlSet\Services\dam\UserSettings\{SID}`

## Answer the questions below

__17. How many times was the File Explorer launched?__
```
Answer: 26
```

__18. What is another name for ShimCache?__
```
Answer: AppCompatCache
```

__19. Which of the artifacts also saves SHA1 hashes of the executed programs?__
```
Answer: AmCache
```

__20. Which of the artifacts saves the full path of the executed programs?__
```
Answer: BAM/DAM
```

# External Devices/USB device forensics

## Device identification:

`SYSTEM\CurrentControlSet\Enum\USBSTOR`
`SYSTEM\CurrentControlSet\Enum\USB`

## First/Last Times:

`SYSTEM\CurrentControlSet\Enum\USBSTOR\Ven_Prod_Version\USBSerial#\Properties\{83da6326-97a6-4088-9453-a19231573b29}\####`

## **USB device Volume Name:**

`SOFTWARE\Microsoft\Windows Portable Devices\Devices`

## Answer the questions below

__21. What is the serial number of the device from the manufacturer 'Kingston'?__
```
1C6f654E59A3B0C179D366AE&0
```

__22. What is the name of this device?__
```
Kingston Data Traveler 2.0 USB Device
```

__23. What is the friendly name of the device from the manufacturer 'Kingston'?__
```
USB
```


# Hands-on Challenge

![[Pasted image 20250118105601.png]]


__24. How many user created accounts are present on the system?__

```
Answer: 3
```

__25. What is the username of the account that has never been logged in?__

```
Answer: thm-user 2
```

__26. What's the password hint for the user THM-4n6?__
```
Answer: Count
```


__27. When was the file 'Changelog.txt' accessed?__

First load `NTUSER.DAT` for __THM-4n6__ user, then under `NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs\.txt` will see.

![[Pasted image 20250118110856.png]]

```
Answer: 2021-11-24 18:18:48
```

__28. What is the complete path from where the python 3.8.2 installer was run?__
```
Answer: Z:\setups\python-3.8.2.exe
```

__29. When was the USB device with the friendly name 'USB' last connected?__
```
Answer: 2021-11-24 18:40:06
```