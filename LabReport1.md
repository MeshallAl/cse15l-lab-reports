CSE 15L Lab Report 1
---

In this lab report I will go over how to connect remotely to your CSE 15L specific account through VScode. 

**1. Installing Visual Studios Code**

Before connecting remotely you are going to need to install Visual Studios Cods (VScode). To do this, all you need to do is go to the VScode website by
searching up "vscode" in your browser or clicking this link ([VScode](https://sdacs.ucsd.edu/~icc/index.php)). Follow the instructions and download the VScode version for your specific machine. Once installed
launch the app and you should see a screen like below.

![image](https://user-images.githubusercontent.com/130005669/230739124-f4977cda-0c52-4472-9b2a-685edf60be51.png)


**2. Setting and Installing Git**

Visual Studios Code is a great tool for numerous tasks. For our task you will also need another tool named git (more specifically git-bash). Similar to VScode, use 
this link ([Git](https://gitforwindows.org/)) to download git. Follow the instructions and install git to your computer. Once installed, you will need to configure you VScode inorder to use it.
In VScode open the terminal by using the menu prompts or pressing (Ctrl +  \`). Then press (Ctrl + Shift + p) and type Select Defult 
Profile. Click on Git Bash. Now in the terminal click the + symbol drop down menu and select bash.

![image](https://user-images.githubusercontent.com/130005669/230739154-ee3e90ee-6d4d-48c3-98dd-95b2737165ff.png)


**3. Accessing your Account Details**

In order to access your account remotely you will first need to know your account details. Click on this link ([Here](https://sdacs.ucsd.edu/~icc/index.php) and log in. Then scroll down and find the account
that contains "cse15l-sp23". This is your account ID for this course. Copy it and click on it. You will be prompted to change the password. Follow the instructions
until it asks for your username. Paste your ID and then continue to follow the instructions. By the end you will now know your account ID and password.

**4. Connecting Remotely**

Now we have all we need to connect. Open up VScode and open the terminal. Make sure it set at bash. Then in the terminal write ssh followed by your account ID. 
like so (ssh *username/ID*@ieng6.ucsd.edu). You will then be prompted to enter your password. (**Note:** you will not be able to see what you input. It will appear
as nothing has been written, but you are writing).

![Screenshot 2023-04-08 121801](https://user-images.githubusercontent.com/130005669/230739065-a21242d9-a8cc-4fac-9dae-7e36939699d8.jpg)


**5. Trying Out Some Commands**

You are now connected to your account remotely. By writing a few simple commands you can access all that you need. You can use command "ls" to list what is in the 
directory. Some other commands include (cd, pwd, cat, cp)

![image](https://user-images.githubusercontent.com/130005669/230739296-f8fb6eb7-21a4-456a-b91b-c68e62176118.png)

Now you know how to remotely connect to your account whenever you need to. 




