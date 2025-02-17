
> Case Overview:  
	The SOC team got an alert regarding some illegal port scanning activity coming from an employee's system. The employee was not authorized to do any port scanning or any offensive hacking activity within the network. The employee claimed that he had no idea about that, and it is probably a malware acting on his behalf. The IR team managed to respond immediately and take a full forensic image of the user's system to perform some investigations.
	There is a theory that the user intentionally installed illegal applications to do port scanning and maybe other things. He was probably planning for something bigger, far beyond a port scanning!
	It all began when the user asked for a salary raise that was rejected. After that, his behavior was abnormal and different. The suspect is believed to have weak technical skills, and there might be an outsider helping him!
	Your objective as a SOC analyst is to analyze the image and to either confirm or deny this theory.


__First let Mount this image using FTK imager__

![[Pasted image 20250204104619.png]]


## 1. What is the computer name of the suspect machine?

__In order to answer this we need to check `System` hive, let's extract it and load to `Registry Explorer`

![[Pasted image 20250204105038.png]]__Export `System hive` from FTK imager__

__Now let's load `System` using Registry Explorer, and using the Bookmark->ComputerName We could find the Answer.

![[Pasted image 20250204105705.png]]

## What is the computer IP?

__Also let's used Bookmarks-> Interfaces__

![[Pasted image 20250204110329.png]]

> 10.0.2.15
## What was the DHCP LeaseObtainedTime?

__We will find the answer in the same place as previous. Just edit the format.

>21/06/2016 02:24:12 UTC