##### Link: [Pickle Rick | Tryhackme](https://tryhackme.com/room/picklerick)
##### Link: [Summary Section](#Summary)

---
##### 1. Web App Enumeration
- **Manual Enumeration**
	- Following the instructions, we skip port scanning and directly access the web app
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_03-46-37_edit.png)
	- We find a simple webpage asking us to find the password and obtain all 3 secret ingredients
	- Checking the source page, we find notes containing username `R1ckRul3s`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-29-42_edit.png)
	- Checking `/robots.txt`, we find string `Wubbalubbadubdub`. Because we found username earlier, this is likely the password
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-33-25_edit.png)
	- If credential exist, there should be a login form for it. Let’s find it
- **Page Discovery**
	- Use `FFUF`
		- `ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-files.txt -u http://10.49.171.79//FUZZ`
			- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-35-01_edit.png)
	- Among the findings, we discover login form at `/login.php`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-37-48_edit.png)
- **Gain Access**
	- Login with credentials `R1ckRul3s:Wubbalubbadubdub` 
	- We find a command line input. 
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-43-16_edit.png)
	- There are other tabs like `Potions, Creature` but none of them work.
- **Authenticated Enumeration**
	- Run some commands to gain information about the target:
		- `ls`
			- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-44-44_edit.png)
		- `pwd`
			- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-55-22_edit.png)
		- `whoami`
			- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-55-55_edit.png)
		- `sudo -l` → Checking sudo permission
			- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_04-56-59_edit.png)
	- We find that:
		- We gain access as `www-data` and are currently in `/var/www/app` aka the webserver’s directory.
		- We have full root privileges.
	- We proceed to the next step.
##### 2. 1st Ingredient
- From running `ls` earlier, we find what seems to be the 1st ingredient:
	- `cat Sup3rS3cretPickl3Ingred.txt`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-01-18_edit.png)
- `cat` command is disabled. We can use alternative like `less`
	- `less Sup3rS3cretPickl3Ingred.txt`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-02-06_edit.png)
- We obtain the 1st ingredient
- Before continuing, we also find `clue.txt`, which tells us to look around    
	- `less clue.txt`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-03-38_edit.png)
- Let’s continue with finding the 2nd ingredient
##### 3. 2nd Ingredient
- In CTF challenges, the usual directories to store useful files are the webserver (our current directory), user, and root    
- Let’s check the user directory    
	- `ls /home`
	- `ls /home/rick`
	- `less /home/rick/"second ingredients"`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-07-35_edit.png)
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-08-05_edit.png)
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-08-45_edit.png)
- We find the 2nd ingredient in `Rick`’s home directory
##### 4. 3rd Ingredient 
- Let’s look at `root` directory. This requires sudo permissions, which our user already has
	- `sudo ls /root`
	- `sudo less /root/3rd.txt`
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-13-20_edit.png)
		- ![](../Challenge%20Attachment/Pickle%20Rick/2026-05-14_05-13-49_edit.png)
- We find the 3rd and last ingredient
---
##### Summary
- Obtain credentials and find the login form to gain access    
- Obtain the 1st ingredient in the current directory    
- Obtain the 2nd ingredient in Rick’s home directory    
- Obtain the 3rd ingredient in the root home directory.