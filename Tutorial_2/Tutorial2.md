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
>$ **cd /**
>
>$ **cd ~**
>
>$ **cd /**
>
>$ **cd**

You should find that `cd` and `cd ~` do the same thing, i.e., they take you back to your home directory. Typing `cd` is a very quick way to get there.

## 4. Basic manipulation of folders and files

### 4.1. Adding and removing directories with `mkdir` and `rmdir`
So far, we’ve discussed moving around the filesystem, but you have been a fly on the wall and have not actually done anything to affect the filesystem in your travels. One basic modification you can make to your filesystem is to add a directory – a task accomplished with the command `mkdir` (`m`a`k`e `dir`ectory).

The following sequence of commands will make a folder called `test` in the `sandbox` folder you installed along with the `examples` folder. While you do these operations, it is illustrative to have a graphical browser window open in `Finder` or `File Explorer` with the contents of the `pcfb/sandbox` folder showing. Go to the same directory in the terminal. You should have placed the `pcfb` folder in your home directory (note that it therefore will be in `/mnt/c/Users/lucy/pcfb/sandbox` or `/cygdrive/c/Users/lucy/pcfb/sandbox` for Windows users). The ls commands give a before and after view of the changes resulting from `mkdir`:

>host:sandbox lucy$ **ls**
>
>host:sandbox lucy$ **mkdir test**
>
>host:sandbox lucy$ **ls**

>test

>host:sandbox lucy$ **cd test**
>
>host:test lucy$ **ls**
>
>host:test lucy$ **cd ..**
>
>host:sandbox lucy$ **ls**

>test

After the `mkdir` command is issued, you find a new directory has been created called test. If you look at your sandbox folder using the `Finder / File Explorer` (remember that GUI you used to use?) you should also see it there, represented by a new folder of the same name. In the last few commands, you simply moved into the new directory, looked around (there was nothing there to see since you hadn’t put any files in it), and moved back out. Next you get rid of the empty directory with the command `rmdir` (`r`e`m`ove `dir`ectory):

>host:sandbox lucy$ **rmdir test**
>
>host:sandbox lucy$ **ls**

**Warning**

You can see that test is now gone. By default, `rmdir` is conservative in that it only removes empty directories. The equivalent to `rmdir` for deleting files is `rm`. Use caution with `rmdir` and even more so with `rm`. These commands are not like putting something in the `Trash`, where you can pull it out later. Files deleted this way are gone and cannot be recovered. We will explore `rm` later after we have built in a check to prevent accidents.

### 4.2. Creating and copying files: `touch` and `cp`

The following sections will deal with commands that help us to work with files, i.e., copy files to/from places, move files, rename files, remove files, and most importantly, look at files. First, we need to have some files to play with. The command `touch` will let us create a new, empty file. The `touch` command does other things too, but for now we just want a file to work with. If you still have the GUI open, you will see a new file appear.

>host:sandbox lucy$ **touch original.txt**
>
>host:sandbox lucy$ **ls**

>original.txt

The command to copy a file is `cp` (copy). It is followed by the file’s present name and location (known as the source) and the location where you would like the copy to end up (known as the destination). In the following example, the source is the file we’ve just created and the destination is an identical file but with a different name:
>host:sandbox lucy$ **cp original.txt duplicate.txt**
>
>host:sandbox lucy$ **ls**

>duplicate.txt original.txt

You can use `cp` to copy a file within the same directory, giving the new file a new name, as we just did. You can also copy a file to another directory, either giving it a new name or retaining the old name. If you only specify a path to a directory for the destination, without an actual filename, then the file will be copied to that directory with its original name.

Remember that the command option consisting of two periods (`..`) refers to the directory that contains the current working directory. Similarly, a single period (`.`) represents the current working directory itself, which is useful if you want to copy a file from elsewhere to the working directory. Let’s copy a file from the examples folder to the sandbox folder.

>$ **cp ../examples/reflist.txt .**
>
>$ **ls**

>duplicate.txt  original.txt  reflist.txt

When moving or copying a file, by default the shell will not warn you if a file or folder of the same name exists in the destination directory. If a file of the same name does exist, it will get “clobbered” – that is, deleted and replaced without warning or notification. You may not realize this until much later when you go looking for the original file. Later, you will see how to modify this behaviour.

### 4.3. Moving files:`mv`

The command for moving files is `mv` (move). You move files in the exact same way that you copy them, except that the original file disappears in the process. In the following example, you move the reflist.txt file to a new directory:
>$ **mkdir Temp**
>
>$ **mv reflist.txt Temp**
>
>$ **ls**

>Temp duplicate.txt original.txt

>$ **ls Temp**

>reflist.txt

The command `mv` is also used for renaming files, since renaming a file is equivalent to moving it to a new file with a different name in the same directory.

>$ **mv duplicate.txt duplicate_renamed.txt**
>
>$ **ls**

>Temp duplicate_renamed.txt original.txt

>$ **mv duplicate_renamed.txt Temp/duplicate.txt**
>
>$ **mv Temp Temp2**
>
>$ **mkdir Temp3**
>
>$ **mv Temp3 Temp2**
>
>$ **ls**

>Temp2 original.txt

>$ **ls Temp2**

>Temp3 duplicate.txt reflist.txt

You will see that with one command you can also both rename and move a file and that you can use `mv` also on folders. Note the difference in outcome between the `mv Temp Temp2` and `mv Temp3 Temp2` commands. Later, you will see how to quickly move or copy multiple files at once.

## 5. Powering up: shortcuts and options

### 5.1. Command line shortcuts

#### 5.1.1. Up arrow

It is not too soon to introduce two shell shortcuts that will save you a lot of typing. Try to get into the habit of using these, because they will not only save you time, but will also reduce the number of typographical errors you have to correct.

The first shortcut is the `↑` key. In most shells, the `↑` moves back through your previous command history. For example, if you type in a long command and hit `Enter`, only to realize that you were in the wrong directory for the command to do what you wish, you can easily move to the correct directory, press `↑` one or more times until you see the correct command, and then hit `Enter` again to execute the command. Try pressing the `↑` key now to step back through and see all the commands that you have done so far. Pressing the `↓` key will get you back to more recent commands and even show future commands that you haven’t typed yet.

Previous commands can also be edited before you re-execute them. If you enter a command but it has a typo somewhere in it, press `↑` to show it again, then use the `→` and `←` keys to move to the place where the error occurred, fix it and hit `Enter`. The cursor doesn’t have to be back at the end of line.

When typing or editing a command, you can use `Ctrl+A` to go directly to the start of the line, `Ctrl+E` to go to the end, `Ctrl+←/→` or `⌥+←/→` to go to the previous/next word, `Ctrl+W` to delete the word left of the cursor, `Ctrl+U` to delete everything left of the cursor and `Ctrl+K` to delete everything right of the cursor. Try these shortcuts with one of your previous commands. If you are in the middle of a command and wish to start over, typing `Ctrl+C` will clear the line. This key sequence is a universal way to interrupt a program or process.

#### 5.1.2. Tab

Another big time-saver is the `tab` key. This is in effect the auto-completion button for the command line. For example, go to the parent `pcfb` directory and start typing:
>$ **cd sand**

Then, press `tab`. The command line should fill in the remainder of the word `sandbox` and append a trailing slash. Now try this command:
>$ cd s *[tab]*

You should get a beep or a blank stare from your terminal. This is because there is more than one folder starting with `s` in the `pcfb` directory. The shell can’t tell if you are referring to the `sandbox`, or the `scripts` folder. To see what the choices are, press tab again. The terminal will return a list of the matches to what you have typed so far. If nothing shows up, check where you are and check for incorrect other characters at the beginning, to make sure you haven’t entered the start of a path that doesn’t exist.

Completion of directory and filenames is especially convenient when the name has a space in it. If you try to type a command with a space in it, such as `cd My Project`, the shell thinks that there are two different pieces of information (arguments) being sent to the `cd` command. Since you probably don’t have a directory called `My`, it returns an error.

When you use tab auto-completion in his context, the shell types the command with extra backslashes inserted before the spaces. Remember from the previous tutorial on searching and replacing with regular expressions that a backslash (`\`) modifies the interpretation of the character that follows. In this case, it causes the shell to interpret the space as part of the filename rather than as the separation between two filenames. You don’t need autocompletion to take advantage of `\`. You can also type it in yourself as part of the path.

Spaces can also be accommodated in file or directory names by using either single or double quotes to enclose the full path, including spaces. However, you cannot do so if you are
trying to use the tilde shortcut or wildcards (discussed later) as part of the path, since they won’t be expanded.

It is generally best to just AvoidUsingSpacesAltogether when naming data files and scripts. This will make things easier later on. Other punctuation marks in names (`?`,`;`,`/`) have special meanings at the command line, and should therefore be avoided as well. Underscores are acceptable to use.

### 5.2. Wildcards in path description

So far you have not done much that you could not have accomplished just as easily (or maybe more easily) with a graphical user interface. It is **wildcards** that makes the command line more powerful than a GUI for processing many files in one operation.

For example, to list all the files and folders that begin with `s` in the `pcfb` directory, as well as the contents of those directories, you could type:
>$ **ls ../s\***

To list just files ending in `.txt`, you could type:
>$ **ls ../examples/\*.txt**

You can use several wildcards in the path. So to list all files and directories that start with a `c` within all directories that you have installed from the book, you can type:

>$ **ls ../\*/c\***

>../examples/chart.html ../examples/ctd.txt
>
>../examples/chart.php ../examples/ctd237e6.asc
>
>../examples/chart0.php ../examples/curlexamples.txt
>
>../examples/chartform.php ../scripts/compositioncalc1.py
>
>../examples/ctd.rtf ../scripts/compositioncalc2.py
>
>../examples/ctd:
>
>Marrus_ctdTib515.txt Marrus_ctdVen1777.txt o_ctdTib626.txt
>
>Marrus_ctdTib531.txt Marrus_ctdVen2243.txt o_ctdTib834.txt
>
>Marrus_ctdTib547.txt midwater.sql o_ctdTib965.txt
>
>Marrus_ctdTib596.txt midwater2.sql o_ctdTib985.txt
>
>Marrus_ctdVen1575.txt o_ctdTib598.txt o_ctdTib989.txt

Notice that the asterisk doesn’t include text beyond the path divider (`/`). Therefore, `ls ../\*c\*` is not equivalent to the command above. In fact, it will show the content of the `scripts` directory.

When using wildcards, if `ls` finds a file that matches, it lists the filename; if it finds a directory that matches, it lists the directory along with its contents.

Another wildcard is the question mark. Try to figure out its meaning:
>$ **touch fat fit feet**
>
>$ **ls f\*t**
>
>$ **ls f?t**
>
>$ **ls f??t**
