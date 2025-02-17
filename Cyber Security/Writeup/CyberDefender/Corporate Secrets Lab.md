
## What is the current build number on the system?

__First we need to open the image using FTK imager then extract `Software hive`, after that we could used Registry Explorer to search about Current build number.

![[Pasted image 20250212094529.png]]

under `system32/config`, we could find `Software hive`, Right click--> Export files.

![[Pasted image 20250212094712.png]]

now open it using __Registry explorer__, under `SOFTWARE\Microsoft\Windows NT\CurrentVersion` we could find the __current build number__.

> Answer: 16299



## How many users are there?

There are a lot of ways to answer this question, let's used the simple one, from __FTK imager__ under `Users`, we could see this.

![[Pasted image 20250212095754.png]]


> Answer: 6


