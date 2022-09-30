# How to log into a course-specific account on ieng6.<br/>

### Step 1: Installing VScode.<br/>
To install VScode, students must first go to [VScode Installer](https://code.visualstudio.com/). <br/>

After installing and opening the application VScode, your application should look like this.
![SC of VScode](https://user-images.githubusercontent.com/114313685/193160564-fd903885-78fe-480b-b297-de2585290972.png) <br/> <br/>

### Step 2: Remotely Connecting. <br/>
With VScode open, go to the top of the application and click terminal. After opening the terminal menu, create a new terminal. <br/>
With a new terminal, type in the following command into the terminal: <br/>
```
ssh cs15lfa22zz@ieng6.ucsd.edu
```
The zz should be replaced with whatever your account letters are. <br/>
It will then prompt you to enter your password. <br/>
If you have successfully entered in the command and password, your terminal should look like this: <br/>
![SC of Connecting](https://user-images.githubusercontent.com/114313685/193162688-eb9ba353-3944-4555-a727-8c224257e831.png) <br/> <br/>

### Step 3: Testing Out Commands. <br/>
With remote access to the server, there are several commands that can be used. <br/>
For example, there are commands such as ls, cat, cs, and cd. <br/>
ls lists the files in the current directory; cd changes the current directory; 
cat views and prints thecontents of the file currently selected. <br/>
Here is an example of some of the commands: <br/>
![SC of Commands](https://user-images.githubusercontent.com/114313685/193163605-65c80d87-a868-4733-9882-d6c1109ef03c.PNG) <br/> <br/>

### Step 4: Moving Files with scp. <br/>
To move files from local to the server, students must first create or find what file to move. <br/>
In this example, a java file named WhereAmI is the file that is going to be moved to the remote server. <br/>
First, students must be logged out of the ssh and change their directory to wherever the file they want to move is. <br/>
Once in the directory, use the following command to move the selected file to the remote server.
```
scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/
```
(replace the zz with the letters of your account). <br/>
After inputting the command above, log back into the ssh and use the command ls to see if your file has been moved. <br/>
If you see your file, you have sucessfully learned how to move a file to a server! Look below to see what the file move looks like. <br/>
![SC of SCP](https://user-images.githubusercontent.com/114313685/193165874-257b98f4-346e-4298-a7c8-bfc4b3c3edb8.PNG) <br/>
An example of the difference between using the WhereAmI file from the server and locally: <br/>
![SC of Difference](https://user-images.githubusercontent.com/114313685/193166090-6b5e709e-9820-4afa-96b4-b386fe5d6122.PNG) <br/>
Looking at the image above, you can see that the outputs are different depending on where the WhereAmI file is running. <br/> <br/>

### Step 5: Setting an SSH Ke.y <br/>
(Logged out of the SSH) Use the commands below to create a pair of files called the public key and private key.
```
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/joe/.ssh/id_rsa): /Users/joe/.ssh/id_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/joe/.ssh/id_rsa.
Your public key has been saved in /Users/joe/.ssh/id_rsa.pub.
```
Once done with these commands, log back on to the ssh. To connect to the ssh use the command below. <br/>
```
ssh cs15lfa22zz@ieng6.ucsd.edu
```
Once connected to the ssh, use the commands: <br/>
```
mkdir.ssh
exit
```
Once finished, use the command: <br/>
```
scp /Users/joe/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys
```
Once finish with this command, you should be able to connect to ssh without having to input your password. <br/>
An example of not having to input a password to connect to ssh: <br/>
![SC of sshkey](https://user-images.githubusercontent.com/114313685/193167485-9d735420-b9c6-49c8-b914-e4faaa1ba6c1.PNG) <br/>
You can see in the example, the user only have to input the command ssh cs15lfa22hb@ieng6.ucsd.edu to connect to the ssh. <br/> <br/>

### Step 6: Optimizing Remote Running. <br/>
Some ways to increase efficiency when running: <br/>
- You can write a command in quotes at the end of an ssh command to directly run it on the remote server, then exit.
- You can use semicolons to run multiple commands on the same line in most terminals.
- You can use the up-arrow on your keyboard to recall the last command that was run. <br/> <br/>
An example of using semicolons to run multiple commands on one line: <br/>
![SC of optimization](https://user-images.githubusercontent.com/114313685/193168198-387dda87-5238-4cd9-9bcf-294b5395c4c8.PNG) <br/>
In the example, I am running two commands on one line which is cat WhereAmI.java and cat hello.txt
