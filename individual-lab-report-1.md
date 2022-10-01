# Week 1 Lab Report #
**Installing VS Code**
![Image](VS.png)
- Before starting with the lab I had already installed VS Code due to starting on PA 0 beforehand. 
- I had followed these instructions a few days back on the PA 0 instructions so this is why my VS Code looks this way. 

**Remotely Connecting** 
![Image](Remote.png) 
- For this specific section my CS 15L account didn't work so I had to use my gmail account. 
- I was basically connecting to a remote computer through VS Code hence why I had to use "vsanchezmartinez@ieng6.ucsd.edu".
- To clarify, the "client" would refer to my macbook while the remote server is the actions tied to my "@ieng6.ucsd.edu" account. 

**Trying Some Commands**
![Image](Commands.png)
- During this part of the lab we were instructed to input some commands and see what would occur. 
- I did commands such as cd, cd ~, ls -lat, ls <directory>, and so on. 
- What I had noticed was that the simple cd command was not working on its own. 

**Moving Files with scp**
![Image](TestingWhere.png)
![Image](MacWhere.png)
-This is the section where I copy a file from my macbook to a remote server.
-I created a file called WhereAmI, ran commands such as "Javac WhereAmI.java" and finding my file in my home directory. 
**Setting an SSH Key**
![Image](Key.png)
-Here we used the ssh-keygen command that creates a public and private key which I could use to copy to a server and save my login password
-This part was actually very tricky for me and took me a while but when it finally copied I had to re-enter my password, logout, and then was finally able to login without having to type my password 
**Optimizing Remote Running**
![Image](Running.png)
-Here I used the "ssh vsanchezmartinez@ieng6.ucsd.edu ls command to directly log into the server and get the home directory. 
-Since I had created my key, I did not have to type in my password. The other line on the terminal was a list of commands that I was able to type in and get several results printed out.