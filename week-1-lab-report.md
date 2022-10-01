# Lab Report 1 - Remote Access and Filesystem

## 1. Installing VScode

* Go to this website, [VS Code Studio Website](URL 'https://code.visualstudio.com/'), to download Visual Studio Code. 
* Make sure to download the correct version for your operating systems, such as Windows, and OS X

![image](https://user-images.githubusercontent.com/54129361/193386141-04868c3d-c993-4b45-b4b0-5d51344782ef.png)

## 2. Remotely Connecting
* In this step, you will be connecting your computer to the remote server. 
* Open terminal to run OpenSSH client, not the server. 
* Login to the remote server by typing, “ssh <ucsd username>@ieng6.ucsd.edu” and then your password. 
* If it asks to continue, type “yes.” You will see the screenshot after you login.

![image](https://user-images.githubusercontent.com/54129361/193386145-b7a72951-a6a4-409d-8b27-910f47a3cbbe.png)

## 3. Trying Some Commands
* Using OpenSSH client, you can run command on your computer or remote computer. 
* You can change directory, list files, concatenate the code from the file, which is shown below.

![image](https://user-images.githubusercontent.com/54129361/193386238-301de2e5-bee6-40cd-9289-1c928497fda0.png)

## 4. Moving Files with scp
* o	Using scp command, you can copy the file on your computer to the remote server. 
* Type “scp <filename> <user email>:~/” to copy the file to the remote server. 
* The screenshot below shows the output after scp command has run.
* Due to technical issues, all the command is not shown in the screenshot.

![image](https://user-images.githubusercontent.com/54129361/193386340-1e8f566b-0b3e-41a4-9c25-cdb0ddbf617e.png)
  
## 5. Setting an SSH Key
* Logging into SSH takes time and is annoying. 
* To skip the time-consuming process, follow the screenshot below. 
* Following the screenshot help to save time and it is more convenient.

![image](https://user-images.githubusercontent.com/54129361/193386346-57826899-afe0-4bbd-be31-e857e3f22ed0.png)

![image](https://user-images.githubusercontent.com/54129361/193386347-5d84a24f-8d04-45e3-b485-7607d6f43f22.png)

## 6. Optimizing Remote Running
* After completing the steps above, now you can optimize the remote server. 
* See how convenient it is to command with less steps and reducing waiting times.

![image](https://user-images.githubusercontent.com/54129361/193386350-25c658f4-e8e1-4552-9d31-7b93d9f1e4af.png)
