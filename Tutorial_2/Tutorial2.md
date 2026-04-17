# Tutorial 2 Introduction to the Command line
# MBLS207 - Bioninformatics

## 1. Introduction 

In this tutorial you will get familiar with a different way to interact with your computer: through the command line.

**Note**

Go through the text and follow the instructions. You are encouraged to work in small groups during the tutorial. Be careful with typing. We recommend not copy-pasting from this website: sometimes symbols or fonts will not copy well, and the command line will only interpret exactly the text you submit.

**Setting up the environment and example files**

If you don’t have it yet, first create a folder called `MBLS207`.
- If you are doing this with **Mac**, feel free to create it in your favourite computer location. We recommend doing this in a high-level folder (as opposed to deeply nested), such as in your Desktop.
- From **Windows**, if you are accessing through the Ubuntu app, you should be able to see your Linux filesystem at the bottom side of the left column within Explorer – click there and create the folder within your Linux home (`/home/<your-username>`).
Within `MBLS207`, create a folder called `Tutorial2`.

Now, download from Blackboard the file called “example_files” and unzip it here. From now on, before opening an example file, copy that file to the `sandbox` folder.

**Accessing and setting up the terminal**

Depending on your operating system you may have to make your computer ready to use the command line. Certain parts of the tutorial are different for different operating systems.

**Linux**

Your computer is also ready to go. The paths mentioned in the tutorial will be slightly different on your machine.

**MacOS**

Your computer is ready to go. Find the `Terminal` program and launch it. If you don’t have a link on your Desktop or Dock yet, we suggest creating one.

**Windows**

You can install Ubuntu as an app inside of Windows. Go to the Windows store, search for Ubuntu 22.04 and install it. Try to open the app to see if it works (it shouldn’t contain any errors).
In some cases, you need to change some settings to get it working. Try to follow these instructions:

<https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-thelinux-kernel-update-package>

An alternative option is to install a virtual machine. You can follow these instructions:

<https://dev.to/florianfelsing/how-to-run-an-ubuntu-vm-on-windows-11-4oef>.

You can install Ubuntu 20.04 or 22.04

## 2. Starting the shell and getting oriented
### 2.1. Starting your terminal session
On Windows, launch the `Ubuntu` app, which will open the `Ubuntu` terminal. On Linux/Mac, open the `Terminal` app.

A new session will start, and the opened window displays a greeting on the first line and a prompt and cursor on the second line (Figure 1). A prompt is a sign on a computer screen that shows that the computer is ready for you to type something. The prompt will probably contain the name of your machine, the name of the current directory (‘~’, you will learn more on that later) and your username. The command line, as the prompt and cursor are known, is displayed within the terminal window by a program called a **shell**. Shells are customizable and powerful – and at times they can seem frustratingly simple-minded. You can issue short commands or write simple scripts that do amazing things, but you can also wipe out a chunk of your hard disk with a few ill-chosen punctuation marks. The shell assumes that you mean what you say, and rarely gives you the chance to opt out of a command you issue or to undo the results.

There are many different shell programs, but the most widely used is `bash`, which will also be used in the course.

It’s time to try your first command. To check that you are set up to use the bash shell, at the prompt in the open terminal window type the following:
>echo $SHELL

The terminal will respond by printing out the name of the active shell, which should be `/bin/bash`. If the active shell is not `bash` but for example `zsh`, which is the default shell on the latest macOS versions, try the following command to make bash the default shell:
>chsh -s /bin/bash

![](../images/mbls207_tutorial2_1.png "Figure 1. A portion of the Terminal window in MacOS and Ubuntu (via Windows subsystem for Linux), showing the greeting, prompt and cursor.")
**Figure 1. A portion of the `Terminal` window in MacOS and Ubuntu (via Windows subsystem for Linux), showing the greeting, prompt and cursor.**

### 2.2.  Ending your terminal session
To end your session, type `exit`. You can just close the window, but this is a bit like unplugging your computer without turning it off first: if there are any programs still running in the terminal window, they will come unceremoniously to a halt. Closing the window is also not an option when you log in to a different computer from within your terminal.

## 3. Navigating your computer from the shell
### Listing files with `ls` and figuring out where you are with `pwd`
As mentioned above, the prompt shows you the directory that is currently your perspective of the **filesystem** from the command line (Figure 2). This is also called the **working directory**. Each time you open a new terminal window, you are logging onto the Unix system of your computer anew. You will be located in what is called your home directory (~). You are now viewing the filesystem from this directory. To specify a different location, we must provide the **path** of that location. A path can be absolute or relative. The **absolute path** is a complete and unambiguous description of where something is in relation to the **root directory** (/), the very base of the filesystem. In contrast, a **relative path** describes where a folder or file is in relation to our working directory.

The first command you will learn, and one you’ll use frequently, is ls (short for list). It prints out a list of files and directories contained within the working directory, or a specified directory.

