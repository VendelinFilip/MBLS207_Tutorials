# Tutorial 2 Introduction to the Command line
# MBLS207 - Bioinformatics

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
### 3.1. Listing files with `ls` and figuring out where you are with `pwd`
As mentioned above, the prompt shows you the directory that is currently your perspective of the **filesystem** from the command line (Figure 2). This is also called the **working directory**. Each time you open a new terminal window, you are logging onto the Unix system of your computer anew. You will be located in what is called your home directory (~). You are now viewing the filesystem from this directory. To specify a different location, we must provide the **path** of that location. A path can be absolute or relative. The **absolute path** is a complete and unambiguous description of where something is in relation to the **root directory** (/), the very base of the filesystem. In contrast, a **relative path** describes where a folder or file is in relation to our working directory.

The first command you will learn, and one you’ll use frequently, is ls (short for list). It prints out a list of files and directories contained within the working directory, or a specified directory.

![](../images/mbls207_tutorial2_2.png "Figure 2. A portion of the Unix filesystem structure in tree format. Folders (also called directories) are in green, files (also called documents) are in maroon, and Unix programs (also called commands) are in grey. The root directory is on the far left.")
**Figure 2. A portion of the Unix filesystem structure in tree format.** Folders (also called directories) are in green, files (also called documents) are in maroon, and Unix programs (also called commands) are in grey. The root directory is on the far left.

**MacOS and Linux (for Windows go to next paragraph)**

For comparison, open Finder (Mac) or the Linux equivalent and navigate to your home folder (Mac: `Go` → `Home` or `Shift+⌘+H` keyboard shortcut), so you can see its content. Now do the same by typing the command ls in your terminal window and compare the output with what you see in the familiar `Finder`. You should see the same folders and files in both. If you have set your computer to a different language than English, you will see the translated names in the GUI, but not in the terminal.

In the following examples, the bold characters are what you type, and the regular characters are what the system prints, and we may or may not show the prompt that begins each line. In place of `lucy` you’ll see your own username, and you will also see a different host name at the beginning of the line. This is your network identity, created when you first set up an account on your computer.

To see the contents of the `Desktop` folder while sitting in your home directory, type:
>host:~ lucy$ **ls Desktop**
or with the default Linux prompt:
>lucy@host:~$ **ls Desktop**

From now on the Linux prompt will only be shown too if the command is different. Without anything before `Desktop`, `ls` expects that `Desktop` is a directory within the working directory. This is a relative path to `Desktop`, because it is in relation to where you are now. Upon executing the command, you should see a list of whatever files are stored on your `Desktop` at the moment.

To see the absolute path of the working directory, use the command `pwd` (`p`rint `w`orking `d`irectory):
>host:~ lucy$ **pwd**

>/Users/lucy

On a Linux system you will see `/home/lucy` instead. Since you haven’t moved anywhere since starting the shell, you are seeing the absolute path of your home directory. Because `Desktop` is a folder within your home directory, and the absolute path to your home directory is `/Users/lucy` or `/home/lucy`, you could also list its contents with:
>host:~ lucy$ **ls /Users/lucy/Desktop**

or in Linux:
>lucy@host:~$ **ls /home/lucy/Desktop**

This command has the exact same results as the previous `ls Desktop` because it is showing the contents of the same folder, just specified in two different ways.

**Windows**

*Windows 10*

If you are using WSL or Cygwin, the root directory in the terminal is in a somewhat odd place compared with the filesystem. The root directory corresponds to a Windows directory deeply hidden somewhere in `C:\Users\<username>\AppData\...` for WSL and `C:\cygwin` for Cygwin. Conversely, the Windows root directory `C:\` is available from the shell environment as `/mnt/c` (WSL) or `/cygdrive/c` (Cygwin).

*Windows 11*

In the newest Windows version, the root directory of the terminal is shown in the filesystem (File Explorer) as a separate folder (Linux).

In the following examples, the bold characters are what you type, and the regular characters are what the system prints, and we may or may not show the prompt that begins each line. In place of `lucy` you’ll see your own username, and you will also see a different host name at the beginning of the line. This is your network identity, created when you first set up an account on your computer. 

Type the command `ls` in your terminal window and you will see that there is not much to see in the Ubuntu or Cygwin home directory yet. We will copy the example files to here later on.
>lucy@host:~$ **ls**

With the Cygwin prompt it will look like this:
>lucy@host ~

>$ **ls**

From now on the Cygwin prompt will only be shown if the command is different.

To see the absolute path of the working directory, use the command `pwd` (`p`rint `w`orking `d`irectory):
>lucy@host:~$ **pwd**

>/home/lucy

Since you haven’t moved anywhere since starting the shell, you are seeing the absolute path of your home directory. To see the contents of another directory than the working directory you provide the path to that directory behind the ls command. For comparison, open File Explorer and navigate to your `Documents` folder, so you can see its content. Now do the same by typing the following command in your terminal window and compare the output with what you see in the familiar `File Explorer`. You should see the same folders and files in both. Note that instead of `lucy` you should fill in your **Windows** username. This can be seen in `File Explorer` by checking the content of the directory `C:\Users`.
>lucy@host:~$ **ls /mnt/c/Users/lucy/Documents**

or with Cygwin:
>lucy@host ~

>$ **ls /cygdrive/c/Users/lucy/Documents**

### 3.2. How to move around with `cd`

**MacOS and Linux (for Windows go to next paragraph)**

To move to another directory, use the command `cd` (`c`hange `d`irectory). Move inside your `Desktop` directory by typing
>host:~ lucy$ **cd Desktop**

>host:Desktop lucy$

Notice that the prompt changes from `host:~ lucy$` to `host:Desktop lucy$`, showing the name of the new working directory. On a Linux system the path component of the prompt will be expanded, showing the complete path.

You will need to keep in mind that capitalization generally counts in all types of Unix. Getting the capitalization of a command wrong can be as bad as misspelling it. This capitalization behaviour is hard to predict, though, so you should not rely on it to distinguish similarly named files.
To see the contents of the `Desktop` directory, but this time from within the directory, you can now type `ls` by itself:
>host:Desktop lucy$ **ls**

From here, if you type `ls Desktop`, you will generate an error, because there is no `Desktop` folder within your `Desktop` folder (unless you have created one).
>host:Desktop lucy$ **ls Desktop**

>ls: Desktop: No such file or directory

The same error happens when you try this, but for a different reason:
>host:Desktop lucy$ **ls /Desktop**

>ls: /Desktop: No such file or directory

To move back towards the root in the directory structure (see Figure 2), more specifically to the parent directory of the working directory, use the command:
>host:Desktop lucy$ **cd ..**

Make sure to include a space between the `cd` and the two dots. This command won’t return any feedback after the prompt. However, since the prompt by default shows a shortened version of your current working directory, it will again change your new location.

The two dots in the command indicate the folder that contains the current folder. This is just another type of relative path. This will always move you from the current working directory to the directory which contains it – unless, of course, you are in the root directory, which is absolute and contained by nothing.

The `..` symbol can be used in conjunction with other directory names. This allows you to
move with a single command from one directory to another that is sister to it in the hierarchy. For example, if you want to go from your `Desktop` directory to your `Documents` folder, this is equivalent to backing out one level and then moving one level into a different but parallel directory relative to where you started (see Figure 2). First, go back to the `Desktop` folder and then go in one command to the `Documents` folder:
>host:~ lucy$ **cd Desktop**
>
>host:Desktop lucy$ **pwd**

>/Users/lucy/Desktop

>host:Desktop lucy$ **cd ../Documents**
>
>host:Documents lucy$ **pwd**

>/Users/lucy/Documents

From `Documents` you can type `cd ..` to go back to the home directory again. Note that you can use `..` more than once in a command. For example, `cd ../..` will send you back two directories in one step.
>host:Documents lucy$ **cd ..**
>
>host:~ lucy$ **pwd**

>/Users/lucy

>host:~ lucy$ **cd ../..**
>
>host:/ lucy$ **pwd**

>/

**Windows**

To move to another directory, use the command cd (change directory). Move inside your Windows home directory by typing:
>lucy@host:~$ **cd /mnt/c/Users/lucy**

>lucy@host:/mnt/c/Users/lucy$

or

>lucy@host ~
>
>$ **cd /cygdrive/c/Users/lucy**

>lucy@host /cygdrive/c/Users/lucy
>
>$

Notice that the prompt changes from `lucy@host:~$` to `lucy@host:/mnt/c/Users/lucy$`, showing the name of the new working directory.

You will need to keep in mind that capitalization generally counts in all types of Unix. Getting the capitalization of a command wrong can be as bad as misspelling it. This capitalization behaviour is hard to predict, though, so you should not rely on it to distinguish similarly named files.

To see the contents of the `Desktop` folder while sitting in your home directory, type:
>lucy@host:/mnt/c/Users/lucy$ **ls Desktop**

Without anything before `Desktop`, `ls` expects that `Desktop` is a directory within the working directory. This is a relative path to `Desktop`, because it is in relation to where you are now. Upon executing the command, you should see a list of whatever files are stored on your `Desktop` at the moment.

Because `Desktop` is a folder within your Windows home directory, and the absolute path to your Windows home directory is `/mnt/c/Users/lucy`, you could also list its contents with:
>lucy@host:/mnt/c/Users/lucy$ **ls /mnt/c/Users/lucy/Desktop**

This command has the exact same results as the previous `ls Desktop` because it is showing the contents of the same folder, just specified in two different ways.

Move inside your `Desktop` directory by typing
>lucy@host:/mnt/c/Users/lucy$ **cd Desktop**

To see the contents of the `Desktop` directory, but this time from within the directory, you can now type `ls` by itself:
>lucy@host:/mnt/c/Users/lucy/Desktop$ **ls**

From here, if you type `ls Desktop`, you will generate an error, because there is no `Desktop` folder within your Desktop folder (unless you have created one).
>lucy@host:/mnt/c/Users/lucy/Desktop$ **ls Desktop**

>ls: Desktop: No such file or directory

The same error happens when you try this, but for a different reason:
>lucy@host:/mnt/c/Users/lucy/Desktop$ **ls /Desktop**

>ls: /Desktop: No such file or directory

To move back towards the root in the directory structure (see Figure 2), more specifically to the parent directory of the working directory, use the command:
>lucy@host:/mnt/c/Users/lucy/Desktop$ **cd ..**

Make sure to include a space between the `cd` and the two dots. This command won’t return any feedback after the prompt. However, since the prompt by default shows a shortened version of your current working directory, it will again change your new location. 

The two dots in the command indicate the folder that contains the current folder. This is just another type of relative path. This will always move you from the current working directory to the directory which contains it – unless, of course, you are in the root directory, which is absolute and contained by nothing.

The `..` symbol can be used in conjunction with other directory names. This allows you to move with a single command from one directory to another that is sister to it in the hierarchy. For example, if you want to go from your `Desktop` directory to your `Downloads` folder, this is equivalent to backing out one level and then moving one level into a different but parallel directory relative to where you started (see Figure 2).

First, go back to the `Desktop` folder and then go in one command to the `Downloads` folder:
>lucy@host:/mnt/c/Users/lucy$ **cd Desktop**
>
>lucy@host:/mnt/c/Users/lucy/Desktop$ **cd ../Downloads**

>lucy@host:/mnt/c/Users/lucy/Downloads$

From `Downloads` you can type `cd ..` to go back to the home directory again. Note that you can use `..` more than once in a command. For example, `cd ../..` will send you back two directories in one step.
>lucy@host:/mnt/c/Users/lucy/Downloads$ **cd ..**
>
>lucy@host:/mnt/c/Users/lucy$ **cd ../..**
>
>lucy@host:/mnt/c$ **cd ../..**

>lucy@host:/ $

### 3.3. Signifying the home directory with ~
A shortcut for referring to your home directory is the tilde symbol (~). This is also shown in the prompt, when you are in your home directory. So, for instance, no matter where you are on the system, you can type the following command to jump straight to the Documents folder in your home directory (this of course only works if you have a Documents directory there, so it won’t work for Windows users; be patient, we’ll add some files in your Ubuntu home directory later on):
>host:/ lucy$ **cd ~/Documents**

This is equivalent to typing the absolute path, specified all the way from root:
>host:Documents lucy$ **cd /Users/lucy/Documents**

See what happens when you try the following commands (use the pwd command after each
one to confirm the results):
>$ cd /
>
>$ cd ~
>
>$ cd /
>
>$ cd

You should find that `cd` and `cd ~` do the same thing, i.e., they take you back to your home directory. Typing `cd` is a very quick way to get there.

## 4. Basic manipulation of folders and files

### 4.1. Adding and removing directories with `mkdir` and `rmdir`
So far, we’ve discussed moving around the filesystem, but you have been a fly on the wall and have not actually done anything to affect the filesystem in your travels. One basic modification you can make to your filesystem is to add a directory – a task accomplished with the command `mkdir` (`m`a`k`e `dir`ectory).

The following sequence of commands will make a folder called `test` in the `sandbox` folder you installed along with the `examples` folder. While you do these operations, it is illustrative to have a graphical browser window open in `Finder` or `File Explorer` with the contents of the `pcfb/sandbox` folder showing. Go to the same directory in the terminal. You should have placed the `pcfb` folder in your home directory (note that it therefore will be in `/mnt/c/Users/lucy/pcfb/sandbox` or `/cygdrive/c/Users/lucy/pcfb/sandbox` for Windows users). The ls commands give a before and after view of the changes resulting from `mkdir`:
