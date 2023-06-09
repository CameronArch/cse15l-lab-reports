# Lab Report 1 - Remote Access and FileSystem

## Step 1: Installing Visual Studio Code

1. Click on this link to go to the download page for VScode: [Visual Studio Code Download](https://code.visualstudio.com/Download)

2. Next, select the download for your operating system. (I will be showing the Windows version) 
![Image](VScode download.png)

3. Go to your downloads and double-click on the VSCodeUserSetup. 
![Image](installer.png)

4. Accept the terms and click next until you see install. 
![Image](terms.png)!![Image](next.png)

5. Click install.                     
![Image](install.png)

6. Finally, open Visual Studio Code. 
![Image](VScode.png)

## Step 2: Remotely Connecting With Course-Specific Account on ieng6

1. Download git: [git Download](https://github.com/git-for-windows/git/releases/download/v2.40.0.windows.1/Git-2.40.0-64-bit.exe)

2. Go to your downloads and double-click on the git installer. 
![Image](gitInstaller.png)

3. Hit next without changing anything. Then, click install.                      
![Image](gitinstall.png)

4. Next, go to Visual Code Studio and open a terminal (Click Terminal -> New Terminal)
![Image](terminal.png)

5. In the terminal, click the dropdown by the +. Click Git Bash.
![Image](gitBash.png)

6. To remotely connect, use **$ ssh cs15lsp23zz@ieng6.ucsd.edu** in the terminal. Change the **zz** to match your account. (If terminal says "Connection to ieng6.ucsd.edu closed by remote host" or some other error, try **$ ssh cs15lsp23zz@ieng6-202.ucsd.edu**)
![Image](Login.png)

7. If it asks you "Are you sure you want to continue connecting (yes/no/[fingerprint])?" Type yes.
![Image](Yes.png)

8. Then, it will ask for your password. Type your password in. **Note: You cannot see your password when typing it in**
![Image](Password.png)

9. Once you are connected, your screen will look something like this.
![Image](LoggedIn.png)

## Step 3: Trying Commands

1. Type any command you would like to use into the console.
![Image](cmd.png)

2. An example command is **pwd** which will output your current working directory
![Image](pwd.png)

3. Other commands you could try are **cd *path*** to change the current directory, **cat *path1* *path2* ...** to print the contents one or files, and **ls *path*** to list the files and folders of given path.

4. To log out, use Ctrl D or run the command **exit**.     

![Image](logout.png)


