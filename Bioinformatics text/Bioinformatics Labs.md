#####################################################
**Lab 1 (take home lab, 01/27/26)**
########################################################

\*\*Step 1. Sign up for a GitHub account \[here](https://github.com)\*\*

To sign up for a GitHub account as a student or faculty member at the University of New Hampshire (UNH), you should use your university email address to take advantage of educational benefits, such as the GitHub Student Developer Pack. Follow the instructions provided by GitHub.

\*\*Step 2. Download and install Visual Studio Code (VScode) from\*\* \[here](https://code.visualstudio.com/Download). If prompted, choose VS Code the Default Editor.

\*\*Step 3. Open VScode to install the \*\*Remote SSH\*\* extension from the Visual Studio Marketplace:\*\*

  1. Open up vscode and click the 'building blocks' icon on the left hand side of vscode

  2. In the upper left search bar, type 'Remote SSH'

  3. Click 'install'

  4. \*\*For Windows users only:\*\* Install Git from the \[GitHub Pull Requests and Issues extension](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github). Once you've installed the GitHub Pull Requests and Issues extension, you'll need to sign in. Follow the prompts to authenticate with GitHub and return to VS Code. NOTE: Most versions of MacOS will already have Git installed, and you can activate it through the terminal with git version. However, if you don't have Git installed for whatever reason, you can install the latest version of Git using one of several popular methods \[here](https://github.com/git-guides/install-git).

\*\*Step 4. Use VScode to establish a connection with RON HPC (High Performance Computing) server through vscode to set your password \[see here](https://code.visualstudio.com/docs/remote/ssh).\*\*

Note: If you have problems with this step, skip to step 6. For this step, go to the terminal drop down menu in VScode and select 'New Terminal'. In the terminal below, run the SSH command using your username and the network address (interet address for UNH's HPC) as shown below. Replace "username" with your actual USNH username (see example for my username below that).
  ```
  ssh username@ron.sr.unh.edu
  ```
  For me to connect I would instead use (do not use this yourself):

  ```
  ssh jtm1171@ron.sr.unh.edu
  ```
After you press enter, you'll be prompted for your password. Note that it likely won't show any indication that you're typing your password. If you mistype your password too many times in too short of a period, the server will block further connections. If this does happen, you can use the USNH VPN to bypass the block and try again. You don't normally need the VPN to connect to Ron though, whether at home or on campus.

If you experience an error connecting to Ron reporting that the host key doesn't match, this is because you likely had account on the previous version of the Ron server that was replaced last year.  To fix this error, you can remove the offending SSH host key with the following command (run this from your terminal window):

``` 
ssh-keygen -R ron.sr.unh.edu
``` 

After removing the key, the first time you connect to Ron, it will confirm that you want to save the new key. Respond 'yes' and it won't ask again.

Note: You only have to run this command if you're experiencing a host key error when connecting to Ron - please disregard if you're connecting to Ron successfully

Once connected, you will be using Bash (the shell).  If you're unfamiliar with using Bash or Linux commands in general, please review this tutorial video series. There are many videos, but you'll want to focus on videos \[1-10](https://nam12.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DIrl8VXxqs8o%26list%3DPLLV\_tmUM69VA4B0DKfNEBsaL9ARlpp\_\_W%26index%3D2\&data=05%7C02%7CJeffrey.Miller%40unh.edu%7C3753a6ba58c342aa545f08de5dd942c8%7Cd6241893512d46dc8d2bbe47e25f5666%7C0%7C0%7C639051384859528675%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C\&sdata=iwF0UJEwE%2Bgxw5hVeMMRGdmwJDls76KnLyi3UVrIXcw%3D\&reserved=0)

\*\*Step 5. Set up remote-ssh in VScode so that you can connect to RON without having to do these extra steps in the future:\*\*

  1. Open Remote-SSH from VScode's command palette: In VScode, open the 'command palette' by pressing 'CMD + Shift + P'. A little bar at the top of the screen should pop up. Begin to type 'Remote-SSH' and before you get too far, you should see 'Remote-SSH: Add New SSH Host...' option pop-up. Click it. If you are asked what the host operating system is, click \*\*LINUX\*\*

  2. Enter ssh connection command: Your command will be 'ssh' and your username (student id) will be entered into the dialog box as follows (just like above):

  ```
  ssh username@ron.sr.unh.edu
  ```
  But, replace "username" with your actual USNH username (see example for me below).

  ```
  ssh jtm1171@ron.sr.unh.edu
  ```

  After you press enter, you'll may be prompted for which config file to use. For now, select the first one in the list. You should see a dialog box that says 'host added!'

  3. Connect to the host: Once again, open Remote-SSH's commands from VScode's command palette by pressing 'CMD + Shift + P'. This time, you want 'Remote-SSH: Connect Current Window to Host...'. You will be prompted for your password. If this all works, congrats. You will have a much shorter Lab 1 this week. Steps 6 and 7 will be performed in lab as well.

\*\*Step 6. Fork the Gen711/811 Lab Repository\*\*

  1. Sign in to your GitHub account.

  2. From a from your GitHub account, you will need to \*\*fork\*\* this repository: https://github.com/jthmiller/gen711-811.git\*\* !\[fork image](../images/fork.png) Note: If you can't find the 'fork' button, you can try this \[shortcut](https://github.com/jthmiller/gen711-811/fork)

  3. In your web browser, navigate back to your own GitHub page. Login to GitHub if needed and click on your username in the top left of the screen to ensure that you are at your own github page. Then change the tab in the top left from 'Overview' to the 'Repositories'. If you forked 'gen711-811' in step 2, you should see 'gen711-811' listed in among your repositories. Click on it, and then click on the green '<> Code' dropdown button and copy the HTTPS address of your Clone (the address should look like https://github.com/jthmiller/gen711-811.git). We will use this address to run a command at RON to copy this directory there using the command line.

\*\*Step 7. Clone the gen711-811 github repo into your home directory on RON:\*\*

If you completed all other steps successfully and hope to leave lab a little earlier than most, try this final task. In VSCode, you should see a little box for typing ssh commands on the bottom right. In the terminal that is connected to RON, we will run the clone command. It should look something like this:

``` 
git clone https://github.com/YOURUSERNAME/gen711-811.git
``` 
This should have resulted in some indication that everything downloaded. If you'd like to confirm that it worked, you can use the 'ls' command. Simply type 'ls' into the terminal connected to RON, and you should see the directory listed. Good luck!
```
ls
```
<center><b> Important!<br>To get credit for lab 1, submit a link (canvas) to your GitHub page. </b></center>



##########################################################

**Lab 2 (1/30/26)**

**########################################################

\## Start this lab once you have access to RON through VScode

First, well will change a couple settings in VScode to make your life easier in the long run.

Tasks:

1\. Set 'ctrl+enter' key to send a line of code down to the terminal

2\. Test the keybinding

3\. Make a new lab notebook repository on github.

4\. Clone that repository to RON

\### To set the ctrl+enter run code shortcut:

1\. Open the keybindings file of VScode

\- Windows: File ==> preferences ==> Keyboard shortcuts

\- Mac: Code ==> Settings ==> Keyboard shortcuts

2\. Search for `workbench.action.terminal.runSelectedText` in the keybindings search bar

3\. Press the icon on the left to open a window with this message "Press desired key combination..." and make your choice. (I suggest Ctrl+Enter)

4\. Press enter to store your binding.

\### Next, test the new keybinding:

1\. hit ctrl+n to open a new document.

2\. In the new document, write `echo "Hello! I'm coding"`

3\. With your cursor next to `echo "Hello! I'm coding"`, press 'ctrl' and then 'enter' together

Did it send `echo "Hello! I'm coding"` to your terminal? What did it return?

\### Make repository on GitHub for your lab notebook on RON and your local computer

Now that you are connected to RON, lets make a lab notebook in your repo to be graded each week. The easiest way to do this is to first create a new repository on GitHub.com, and then clone that to your home directory on RON and your laptop.

1\. Login to GitHub with the credentials you made for Lab 1

2\. On your GitHub page, click 'Repositories'

3\. Click the green 'New' button

4\. In 'Repository Name', type 'Bioinformatics-Notes'  \*\*No spaces. Lets all keep the same simple name\*\*

5\. Flip the switch to 'on' for the 'Add README'

6\. Click 'Create repository'

\### Next, we will clone the repo on RON, and open up the folder with VScode (using the Remote SSH extension)

1\. Open up vscode

2\. Control + shift + 'p' to open command prompt (command + shift + p on apple)

3\. Start typing 'Connect to...' and the 'Connect current window to host' menu item will pop up. Select it

4\. If asked, connect to ron.sr.edu host

5\. Enter your RON username if prompted

6\. Enter your RON password when prompted

7\. Once you are successfully connected to RON and in your home directory, clone with the 'git clone' command:

```
cd $HOME

git clone https://github.com/<YOURGITHUBUSERNAME>/Bioinformatics-Notes.git

```

You should see an indication that it downloaded to your home directory

\### Next, we will open the directory you cloned in VScode to save the workspace, then make a lab notebook document that will synchronize on RON and your machine.

1\. In the VScode window that you have connected to RON, go to 'File --> Open folder'

2\. The command pallet in VScode should show your 'home directories' including the 'Bioinformatics-Notes' directory. Select it.

3\. If you did this correctly, you should now see the README file pop up on the left in the list of files. Click on it to open it.

4\. While we are at it, lets save your VScode workspace in the repo directory. Click 'File --> Save Workspace As...' and click on the 'Bioinformatics-Notes' directory to save the workspace there. The workspace file just lists your VScode preferences.This way, you can load this workspace each week to pick up where you left off.

5\. In vscode terminal, go to 'file' --> 'new text file'. Save this empty file as 'yourlastname\_yourfirstname.md'. Keep notes in this file as demonstrated by your instructor to get full attendance points. Add some short random text to this document to make sure that it is picked up.

Note: Text files saved with the '.md' after it will be interpreted at 'markdown' format. We will get into this soon.

\### Use SSH keys on RON so that you dont need passwords to push your lab notebook

1\. Generate an SSH key pair (if you don't have one) in your host's terminal using the command:

ssh-keygen -t ed25519 -C "jeffrey.miller@unh.edu"

\- You might see:

```
Enter file in which to save the key (/home/users/YOURUSERNAME/.ssh/id\\\_ed25519):
```

Hit enter to proceed

\- If you've done this already and re-runnig it, you might see

```
/home/users/YOURUSERNAME/.ssh/id\\\_ed25519 already exists.

Overwrite (y/n)?

```

Enter 'y' and hit return
Next, you might see

```
Enter passphrase (empty for no passphrase):

Enter same passphrase again:

```
Hit return for both. No passphrase is required.

You should see:

```
Your public key has been saved in /home/users/YOURUSERNAME/.ssh/id\\\_ed25519.pub

The key fingerprint is:

SHA256:gS9dqsZ2WtlQhQWDWKC81aoPG3OwkFp0e5kAKwzbhLA YOUREMAIL@unh.edu

The key's randomart image is:

+--\\\[ED25519 256]--+

|+.o   .+..o+o    |

|+= + ..o. .o     |

|E.+ = o o o      |

| o o = \\\* =       |

|  + + \\\* S        |

| o . \\\* o +       |

|.   \\\* \\\* + .      |

|     X +         |

|    . o          |

+----\\\[SHA256]-----+

```
2\. Add your public key to your GitHub account:

\- Copy the content of your public key file. Print it to the screen using `cat \~/.ssh/id\\\_ed25519.pub`

\- This should print the key to the terminal screen and look like this

``
SHA256:gS9dqsZ2WtlQhQWDWKC81aoPG3OwkFp0e5kAKwzbhLA YOUREMAIL@unh.edu
```
\- Go to your GitHub account's Settings (gear top right icon of your home GitHub page) > SSH and GPG keys.

\- Click New SSH key, give it a title (use Laptop to RON), paste the copied public key, and click Add SSH key.

3\. Change your repository's remote URL:

\- Change into your Gen711-811 repository with `cd \~/gen711-811`

\- In your repository's directory, check the current remote URL with `git remote -v` You should see the name of your fetch (download) and push (upload) access method. Set it to use ssh with:

```

git remote set-url origin git@github.com:YOURUSERNAME/REPOSITORY.git

```

Note: replace 'YOURUSERNAME' with your \*\*\*github username\*\*\*, and 'REPOSITORY' with the name of the repository. In this case, it is 'gen711-811'. This is what my command for me would look like:

```

git remote set-url origin git@github.com:jthmiller/gen711-811.git

```

\- my github username is jthmiller

\- the repo name is gen711-811

4\. Test the connection at RON with: `ssh -T git@github.com`

You should see a message confirming a successful connection like this:

```
Hi jthmiller! You've successfully authenticated, but GitHub does not provide shell access.
```
Now, subsequent push and pull operations from within VS Code will use SSH authentication without prompting for credentials.

\### Do the same for your lab notebook repository.

1\. Change your current directory to the lab notebook directory with `cd \~/YOURLABNOTEBOOKREPONAME`

2\. In your repository's directory, check the current remote URL with `git remote -v` You should see the name of your fetch (download) and push (upload) access method. It should also show your username and repo name.

3\. Set it to use ssh authentication with:

```
git remote set-url origin git@github.com:YOURUSERNAME/REPOSITORY.git
```
Note: replace 'YOURUSERNAME' with your \*\*\*github username\*\*\*, and 'REPOSITORY' with the name of the repository. In this case, it is whatever you nammed your notebook repo.

4\. \*\*NEW\*\* Set your username and email for Git at RON:

This last command should get you pushing to repos. Run these two commands:

```
git config --global user.name "YOUR\\\_GITHUB\\\_USERNAME"
```
hit enter, and then this one:

```
git config --global user.email "Jeffrey.miller@unh.edu"
```
Use your email. This should work without changing directories into the repository.

If you've done everything above correctly, new documents and changes should be tracked VScode and Git. To get your changes incorporated into your repository at GitHub, click on the github bubble fork (usually the third icon down on the left of VScode). Enter any random text you want into the 'Message' box, and then hit the commit button. This should upload your new files/changes to your GitHub repo.

Best practice is to use different authentication keys for different machines (e.g., work laptop vs. personal laptop). If one machine is compromised, you can revoke access for that specific key without affecting others. Go through this process again if you have another computer to work from.

\### Updating your copy of 'gen711-811' each week. (Will do as a class prior to lab 3)

If you forked gen711-811, the easiest method to get the updates each week is to log in to your GitHub in a browser, navigate to your copy of the 'gen711-811' repo. If there are updates to be had, you should see 'update fork' button.  This will bring the new files/changes to your GitHub repo, but not to your 'remote repo' of gen711-811 on RON. To pull the updates to your RON remote repo, open VScode, connect to RON (as above). Once you've connected to RON, go to 'File --> Open Folder'. Scroll down to and click 'gen711-811'. Click the bubble fork on the left. Near the 'Changes' meun, you should see '...'. If you click on it, you should see a 'fetch' option. Let me know if you see an error as a result.

\### Generate ssh-keys to log into RON from VScode without usernames and passwords (Will do as a class prior to lab 3)

\### Do this if you'd preffer not to type your username and password each time you log into RON.

The process is much like the process for generating ssh keys for the connection between RON and GitHub

First, open 'terminal' on your mac. We are going to use the terminal to generate the keys and restrict the permissions on the private key file.

 <details><summary>For Mac and Linux</summary>

Run the following shell command, replacing the path to your private key if necessary:

```
cd \~/.ssh

ssh-keygen -t ed25519 -b 4096

chmod 400 \~/.ssh/id\\\_ed25519

```

\- Next, share the public key with the Ron server

```
ssh-copy-id USERNAME@ron.sr.unh.edu

```
Test your ssh connection
```
ssh username@RON.sr.unh.edu

```
If that doesn't work, we can try:
```

cat \~/.ssh/id\\\_rsa.pub | ssh username@ron.sr.unh.edu "mkdir -p \~/.ssh \\\&\\\& cat >> \~/.ssh/authorized\\\_keys"

```

<br>

</details> <!-- end for mac-->

<br>

<details><summary>For Windows</summary> 

Open PowerShell by searching for it in the Start menu.

Type ssh and press Enter. If you see usage information, the client is installed. If not, you may need to install it via Windows "Optional features" in Settings.

In the PowerShell window, run the following command to generate a new, secure Ed25519 key pair, replacing "your\_email@example.com" with your email address for identification:

```
sh-keygen -t ed25519 -C "your\\\_email@example.com"
```
Run the following command in PowerShell to grant explicit read access to your username:

```
icacls "privateKeyPath" /grant :R
```
Enter file in which to save the key: Press Enter to accept the default location (C:\\Users\\your\_username\\.ssh\\id\_ed25519).

Enter passphrase (empty for no passphrase): It is recommended to enter a secure passphrase for an extra layer of security. You will be prompted to enter it again to confirm. If you prefer to use the key without a password prompt, press Enter twice to leave it empty.

Start the ssh-agent service. In powershell, type:

```
Start-Service ssh-agent

```
Set the service to start automatically on startup (optional but recommended):

```
Set-Service -Name ssh-agent -StartupType 'Automatic'

```
Add your private key to the ssh-agent:

```
ssh-add \~/.ssh/id\\\_ed25519 USERNAME@ron.sr.unh.edu

```

Test your ssh connection

```
ssh username@RON.sr.unh.edu

```
</details> <!-- end for Windows-->


**#########################################################
**LAB 3 2/6/2026**
**########################################################

\## The key points here are:

\- The shell gives you the ability to work more efficiently by using keyboard commands rather than a GUI.

\- Useful commands for navigating your file system include: ls, pwd, and cd.

\- Most commands take options (flags) which begin with a -.

\- Tab completion can reduce errors from mistyping and make work more efficient in the shell.

\# Navigating Files and Directories

\- How can I perform operations on files outside of my working directory?

\- What are some navigational shortcuts I can use to make my work more efficient?

\# Part 2 (lab 3)

\## Objectives:

\- Use a single command to navigate multiple steps in your directory structure, including moving backwards (one level up).

\- Perform operations on files in directories outside your working directory.

\- Work with hidden directories and hidden files.

\- Interconvert between absolute and relative paths.

\- Employ navigational shortcuts to move around your file system.


\## More navigation

\- We got an idea for moving around using cd and the name of the folder to move into.

\- But how to we go back out? We dont see the folder we are in.

\- We have a special command to tell the computer to move us back or up one directory level.

\### Your Notes Here:

Separate notes by an empty line, or they'll get pasted together.

\- Using a dash is helpful for lists

1\. And numbers for lists

The pound sign is used for 'sections'. A single pound (or hashtag) in front of a word makes it appear bigger/bold to show a new section. See below

\# My Notes:

To change directories, use 'cd' and then hit tab two times to see directories in my current directory.

First command is print working directory (pwd). Within a directory, there might be more directories, or files in files. A directory tracked by git hub is a repository.

To make a list of files in the directory, use ls. BASH commands have options, and the options will allow you to specify things.

Flavors of ls:

1\. ls-F - will show slashes to indicate if there are files, so you can determine if you want to change directories down or not.

2\. man ls - manual for ls options. q will bring you back out of the manual.

3\. ls -lrth prints extra information about the directories (when it was made, who owns it, etc.)

cd commands will let you navigate your directories:

1\. cd ../ will step you back one level.

2\. cd \~ shorthand for your home directory.

An absolute path starts all the way back to the base or root of the computer vs a short cd (ex. /home/users/sen97/gen711-811/shell\_data)

If you have an unclosed quote or parentheses, you can press ctrl+c to get out of it. It also works for ending active processes.

In some cases we don't want to open up a whole file, because its huge, we just want to see the first few lines. So we can use the head command.

The echo command will tell you details about the variable you put in (ex. $home)

The History command will show you your coding history.

grep will search through a file and return only the lines you are searching for. If you include the ^ symbol, it will tell the search to look for the thing you are looking for at the begining of the line.

To redirect the output to a file, we can use the greater than symbol after your prompt (ex. grep "^@" SRR097977.fastq > headerlines.txt).

Pipe special character | Pipes an output to a different command, so we can count with word count, or wc, and add -l to tell it to count the number of lines.  If you just do wc alone, it will print lines, words, characters. Can also use ls | grep '^c' to search for  something (remember, ^ is "starts with").

The command less will let you scroll through the whole file.

`### Complete the questions below when intrstructed. Push the changes to this document to recive credit for attending the lab

\#### 1. What are 3 ways to change directories to your home directory from the  untrimmed\_fastq directory?

1\. cd $HOME

2\. cd ../ (repeat until you get to the home)

3\. cd \~

4\. cd /home/users/sen97 (absolute path)

\#### 2. How many programs in /bin

2\. Do each of the following tasks from your current directory using a single ls command for each:

    $ cd /bin (I used | wc -l to count)

    - List all of the files in /bin that start with the letter ‘c’.

    $  ls c\*

    - List all of the files in /bin that contain the letter ‘a’.

    $  ls \*a\*

    - List all of the files in /bin that end with the letter ‘o’.

    $ ls \*o

    - Bonus: List all of the files in /bin that contain the letter ‘a’ or the letter ‘c’.

    $ ls \*\[ac]\*

\#### Answers here

Start with the letter c \_94\_

Start with the letter a \_49\_

Start with the letter o \_16\_

Contain the letter ‘a’ or the letter ‘c’ \_926\_

Contain the letter a \_644\_

End with the letter o \_34\_

\#### What command/commands would you use to find the line number in your history for the command that listed all the '.fastq' files using the absolute path. Paste your answer below.

history

**######################################################
**Lab 4 - 2/13/26**

**######################################################


::::::::::::::::::::::::::::::::::::::: objectives

\- View, search within, copy, move, and rename files. Create new directories.

\- Use wildcards (`\\\*`) to perform operations on multiple files.

\- Make a file read only.

\- Use the `history` command to view and repeat recently used commands.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions


\- How can I view and search file contents?

\- How can I create, copy and delete files and directories?

\- How can I control who has permission to modify a file?

\- How can I repeat recently used commands?

::::::::::::::::::::::::::::::::::::::::::::::::::

\### EXERCISE 1: NAVIGATION PRACTICE

Navigate to your untrimmed\_fastq directory in one command

ANSWER: cd gen711-811/shell\_data/untrimmed\_fastq

\### EXERCISE 2: WILDCARDS

What would the output look like if the wildcard could \*not\* be matched? Compare the outputs

ANSWER:  ls: cannot access '\*h': No such file or directory

\### EXERCISE 3: NAVIGATING PRACTICE

Navigate to your home directory. From there, list the contents of the untrimmed\_fastq directory.

ANSWER: ls gen711-811/shell\_data/untrimmed\_fastq

:::::::::::::::::::::::::::::::::::::::  challenge

\## Notes

ls -laF: Who made the file

ls /usr/bin/

ls /usr/bin/\*sh : limit to names starting with

cat - print file to screen

less: show the contents of a file. Within less, use / and what you are searching for to move around, q to quitq

head and tail will give you the first or last few lines of a fastq, with -n and a number (so -3) will give you three lines.

mkdir backup back ups directory

cp makes a copy of the file cp SRR098026.fastq SRR098026-backup.fastq (second name is name of backup)

mv \*backup.fastq backup/ moved anything with the file name backup to our backup folder

\## Relative path resolution

Using the filesystem diagram below, if `pwd` displays `/Users/thing`,

what will `ls ../backup` display?

!\[alt text](image.png)

1\. `../backup: No such file or directory`

2\. `2012-12-01 2013-01-08 2013-01-27`

3\. `2012-12-01/ 2013-01-08/ 2013-01-27/`

4\. `original pnas\\\_final pnas\\\_sub`

!\[](fig/filesystem-challenge.svg){alt='File System for Challenge Questions'}

:::::::::::::::  solution

\## Solution

1\. No: there \*is\* a directory `backup` in `/Users`.

2\. No: this is the content of `Users/thing/backup`,

  but with `..` we asked for one level further up.

3\. No: see previous explanation.

  Also, we did not specify `-F` to display `/` at the end of the directory names.

4\. Yes: `../backup` refers to `/Users/backup`.

ANSWER: Yes

:::::::::::::::::::::::::

\### EXERCISE 4: FINDING HIDDEN DIRECTORIES

First navigate to the shell\_data directory. There is a hidden directory within this directory. Explore the options for ls to find out how to see hidden directories. List the contents of the directory and identify the name of the text file in that directory.

Hint: hidden files and folders in Unix start with ., for example .my\_hidden\_directory

What is the hidden file name in the hidden directory?

ANSWER: ls -a .hidden

\### EXERCISE 5: HISTORY

Find the line number in your history for the command that listed all the .sh files in /usr/bin. Rerun that command.

ANSWER: history

!189 (! lets you rerun a number from history linked to a command)

\### EXERCISE 6: FILE CONTENTS

Print out the contents of the \~/shell\_data/untrimmed\_fastq/SRR097977.fastq file. What is the last line of the file?

C:CCC::CCCCCCCC<8?6A:C28C<608'\&\&\&,'$

\### EXERCISE 7: PATHS

From your home directory, and without changing directories, use one short command to print the contents of all of the files in the \~/shell\_data/untrimmed\_fastq directory.

ls gen711-811/shell\_data/untrimmed\_fastq

\### EXERCISE 8: LESS (SEQUENCE TTTTTq)

What are the next three nucleotides (characters) after the first instance of the sequence quoted above?

CTC

\### File Permissions Help

The first part of the output for the `-l` flag gives you information about the file's current permissions. There are ten slots in the permissions list. The first character in this list is related to file type, not permissions, so we'll ignore it for now. The next three characters relate to the permissions that the file owner has, the next three relate to the permissions for group members, and the final three characters specify what other users outside of your group can do with the file. We're going to concentrate on the three positions that deal with your permissions (as the file owner).

!\[](fig/rwx\_figure.svg){alt='Permissions breakdown'}

Here the three positions that relate to the file owner are `rw-`. The `r` means that you have permission to read the file, the `w` indicates that you have permission to write to (i.e. make changes to) the file, and the third position is a `-`, indicating that you don't have permission to carry out the ability encoded by that space (this is the space where `x` or executable ability is stored, we'll talk more about this later.

\### EXERCISE 9

Starting in the shell\_data/untrimmed\_fastq/ directory, do the following:

Make sure that you have deleted your backup directory and all files it contains.

Create a backup of each of your FASTQ files using cp. (Note: You’ll need to do this individually for each of the two FASTQ files. We haven’t learned yet how to do this with a wildcard.)

Use a wildcard to move all of your backup files to a new backup directory.

Change the permissions on all of your backup files to be write-protected.

\### EXERCISE 10: PROGRAMS

After loading a conda environment, where is the program 'fastqc' stored?

:::::::::::::::::::::::::::::::::::::::: keypoints

\- You can view file contents using `less`, `cat`, `head` or `tail`.

\- The commands `cp`, `mv`, and `mkdir` are useful for manipulating existing files and creating new directories.

\- You can view file permissions using `ls -l` and change permissions using `chmod`.

\- The `history` command and the up arrow on your keyboard can be used to repeat recently used commands.

::::::::::::::::::::::::::::::::::::::::::::::::::



**##################################################**

**Lab 5**

**##################################################**

\---

title: "Lab 5"

author: "Jeffrey Miller"

date: "2026 Feb 20"

output: pdf\_document

\---

\### Today

1\. Review

2\. Permissions

3\. Conda environments

4\. Running Fastqc

5\. Redirection (if there is time)

:::::::::::::::::::::::::::::::::::::::: keypoints

\- You can view file permissions using `ls -l` and change permissions using `chmod`.

\- The `history` command and the up arrow on your keyboard can be used to repeat recently used commands.

\- Conda environments simplify reporducability, dependencies and sharing environments.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: review

\- You can view file contents using `less`, `cat`, `head` or `tail`.

\- The commands `cp`, `mv`, and `mkdir` are useful for manipulating existing files and creating new directories.



\### Quality scores. Highest score for a base is 41

Quality encoding: !"#$%\&'()\*+,-./0123456789:;<=>?@ABCDEFGHIJ

                   |         |         |         |         |

Quality score:    01........11........21........31........41



::::::::::::::::::::::::::::::::::::::::::::::::::



\*Warm ups: What is the last read in the SRR2584863\_1.fastq file? How confident are you in this read?

ANSWER: GGGTAGGTATTACTCAGGACGAGGCGGTCGTGCCAC

Not very confident, the end of the sequence is low (3-5)

How big are your fastqs? (Hint: Look at the options for the ls command to see how to show file sizes.)

\- hint, it involves 'ls'. See if you can do it using a relative and absolute path

\- another hint: There is an option to make it easy to read the file size. Use one of the two methods to find it

A:

\### EXERCISE 5.1

Starting in the shell\_data/untrimmed\_fastq directory, do the following:

Make sure that you have deleted your backup directory and all files it contains.

Create a backup of each of your FASTQ files using cp. (Note: You’ll need to do this individually for each of the two FASTQ files. We haven’t learned yet how to do this with a wildcard.)

Use a wildcard to move all of your backup files to a new backup directory.

Paste the code you used to do each step between the \\'\\'\\' below:

```

rm -Rf backup

```

\### File Permissions Help

The first part of the output for the `-l` flag gives you information about the file's current permissions. There are ten slots in the

permissions list. The first character in this list is related to file type, not permissions, so we'll ignore it for now. The next three

characters relate to the permissions that the file owner has, the next three relate to the permissions for group members, and the final

three characters specify what other users outside of your group can do with the file. We're going to concentrate on the three positions

that deal with your permissions (as the file owner).

!\[](fig/rwx\_figure.svg){alt='Permissions breakdown'}

Here the three positions that relate to the file owner are `rw-`. The `r` means that you have permission to read the file, the `w`

indicates that you have permission to write to (i.e. make changes to) the file, and the third position is a `-`, indicating that you

don't have permission to carry out the ability encoded by that space (this is the space where `x` or executable ability is stored, we'll

talk more about this later).

\### EXERCISE 5.2

Change the permissions on all of your backup files to be write-protected.

```
chmod ug+rwx SRR097977.fastq

```

How do you know they are write protected?

A:


\### EXERCISE 5.3: CONDA ENVIRONMENTS AND PROGRAMS

After loading a conda environment, where is the program 'fastqc' stored?

```

Replace this with code

```

\### Explore the fastqc output. Which samples failed at least one of FastQC’s quality tests? What test(s) did those samples fail?

:::::::::::::::::::::::::::::::::::::::: keypoints

\- Use `which` for commands/programs to see where they are installed

\- You can view file permissions using `ls -l` and change permissions using `chmod`.

\- The `history` command and the up arrow on your keyboard can be used to repeat recently used commands.

\- Explain what a conda environment is, and how to activate and deactivate it

::::::::::::::::::::::::::::::::::::::::::::::::::

unzip

**#########################################################
**Lab 7**
**########################################################

author: "Jeffrey Miller"

date: "2026 Mar 6th"

\---

\# Today: Writing Scripts and Working with Data

\- Discuss group projects

\- Transfer plots and results to/from RON

\- Downloading files directly to RON

\## Instructions for Group projects

See an example of the final github product of the final projects \[here](https://github.com/jthmiller/gen711-811-example)

Instructions for starting group projects can be found \[here](https://github.com/jthmiller/gen711-811-example/blob/main/Group-Project-Git\_instructions.md)

```bash

wget ftp://ftp.ensemblgenomes.org/pub/release-37/bacteria/species\\\_EnsemblBacteria.txt

```
or
```bash

$ cd

$ curl -O ftp://ftp.ensemblgenomes.org/pub/release-37/bacteria/species\\\_EnsemblBacteria.txt

```
\# Part A
::::::::::::::::::::::::::::::::::::::: objectives

\- Why study \*E. coli\*?

\- Understand the data set.

\- What is hypermutability?
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

\- What data are we using?

\- Why is this experiment important?

::::::::::::::::::::::::::::::::::::::::::::::::::

\## Background

We are going to use a long-term sequencing dataset from a population of \*Escherichia coli\*.



\- \*\*What is \*E. coli\*?\*\*

  - \*E. coli\* are rod-shaped bacteria that can survive under a wide variety of conditions including variable temperatures, nutrient availability, and oxygen levels. Most strains are harmless, but some are associated with food-poisoning.



!\[](fig/172px-EscherichiaColi\_NIAID.jpg){alt='Wikimedia'}



<!-- https://species.wikimedia.org/wiki/Escherichia\\\_coli#/media/File:EscherichiaColi\\\_NIAID.jpg -->



\- \*\*Why is \*E. coli\* important?\*\*

  - \*E. coli\* are one of the most well-studied model organisms in science. As a single-celled organism, \*E. coli\* reproduces rapidly, typically doubling its population every 20 minutes, which means it can be manipulated easily in experiments. In addition, most naturally occurring strains of \*E. coli\* are harmless. Most importantly, the genetics of \*E. coli\* are fairly well understood and can be manipulated to study adaptation and evolution.



\## The data



\- The data we are going to use is part of a long-term evolution experiment led by \[Richard Lenski](https://en.wikipedia.org/wiki/E.\_coli\_long-term\_evolution\_experiment).



\- The experiment was designed to assess adaptation in \*E. coli\*. A population was propagated for more than 40,000 generations in a glucose-limited minimal medium (in most conditions glucose is the best carbon source for \*E. coli\*, providing faster growth than other sugars). This medium was supplemented with citrate, which \*E. coli\* cannot metabolize in the aerobic conditions of the experiment. Sequencing of the populations at regular time points revealed that spontaneous citrate-using variant (\*\*Cit+\*\*) appeared between 31,000 and 31,500 generations, causing an increase in population size and diversity. In addition, this experiment showed hypermutability in certain regions. Hypermutability is important and can help accelerate adaptation to novel environments, but also can be selected against in well-adapted populations.



\- To see a timeline of the experiment to date, check out this \[figure](https://en.wikipedia.org/wiki/E.\_coli\_long-term\_evolution\_experiment#/media/File:LTEE\_Timeline\_as\_of\_May\_28,\_2016.png), and this paper \[Blount et al. 2008: Historical contingency and the evolution of a key innovation in an experimental population of \*Escherichia coli\*](https://www.pnas.org/content/105/23/7899).



\### View the metadata



We will be working with three sample events from the \*\*Ara-3\*\* strain of this experiment, one from 5,000 generations, one from 15,000 generations, and one from 50,000 generations. The population changed substantially during the course of the experiment, and we will be exploring how (the evolution of a \*\*Cit+\*\* mutant and \*\*hypermutability\*\*) with our variant calling workflow. The metadata file associated with this lesson can be \[downloaded directly here](files/Ecoli\_metadata\_composite.csv) or \[viewed in Github](https://githuwgb.com/datacarpentry/wrangling-genomics/blob/main/episodes/files/Ecoli\_metadata\_composite.csv). If you would like to know details of how the file was created, you can look at \[some notes and sources here](https://github.com/datacarpentry/wrangling-genomics/blob/main/episodes/files/Ecoli\_metadata\_composite\_README.md).



This metadata describes information on the \*Ara-3\* clones and the columns represent:



| Column           | Description                                     |

| ---------------- | ----------------------------------------------- |

| strain           | strain name                                     |

| generation       | generation when sample frozen                   |

| clade            | based on parsimony-based tree                   |

| reference        | study the samples were originally sequenced for |

| population       | ancestral population group                      |

| mutator          | hypermutability mutant status                   |

| facility         | facility samples were sequenced at              |

| run              | Sequence read archive sample ID                 |

| read\\\_type        | library type of reads                           |

| read\\\_length      | length of reads in sample                       |

| sequencing\\\_depth | depth of sequencing                             |

| cit              | citrate-using mutant status                     |

:::::::::::::::::::::::::::::::::::::::  challenge
\### Challenge

Based on the metadata, can you answer the following questions?

1\. How many different generations exist in the data?



   ANSWER: 50000



\##MY NOTES:#################################



to get file --> wget "url"



to open file in terminal --> less Ecoli\_metadata\_composite.csv



to rename a file --> mv Ecoli\_metadata\_composite.csv.1 Ecoli\_metadata\_composite.csv



to delete a file --> rm Ecoli\_metadata\_composite.csv.1



To get total column count --> head -n1 Ecoli\_metadata\_composite.csv | tr ',' '\\n' | wc -l



To get rows count --> wc -l Ecoli\_metadata\_composite.csv



less -s Ecoli\_metadata\_composite.csv



extract just one column -->

cut -f6 -d',' Ecoli\_metadata\_composite.csv



to multi-select for the same code --> highlight it, then control+d will find it repeatidly, then can delete.



to focus on one column, then sort it and pull out unique values to count how many there are -->

cut -f6 -d',' Ecoli\_metadata\_composite.csv | sort | uniq -c



to find everything that starts with a value --> grep^



$ is short for end of line

2\. How many rows and how many columns are in this data?



   ANSWER : 63 rows, 12 Columns



3\. How many citrate+ mutants have been recorded in \*\*Ara-3\*\*?



   ANSWER: 10



4\. How many hypermutable mutants have been recorded in \*\*Ara-3\*\*?



   ANSWER: 6

::::::::::::::::::::::::::::::::::::::: objectives



\- Explain how a FASTQ file encodes per-base quality scores.

\- Interpret a FastQC plot summarizing per-base quality across all reads.



::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: questions



\- How can I describe the quality of my data?



::::::::::::::::::::::::::::::::::::::::::::::::::



\## Bioinformatic workflows



When working with high-throughput sequencing data, the raw reads you get off of the sequencer will need to pass

through a number of  different tools in order to generate your final desired output. The execution of this set of

tools in a specified order is commonly referred to as a \*workflow\* or a \*pipeline\*.



An example of the workflow we will be using for our variant calling analysis is provided below with a brief

description of each step.



!\[](fig/variant\_calling\_workflow.png){alt='workflow'}



1\. Quality control - Assessing quality using FastQC

2\. Quality control - Trimming and/or filtering reads (if necessary)

3\. Align reads to reference genome

4\. Perform post-alignment clean-up

5\. Variant calling



```bash

mkdir -p \~/gen711-811/data/untrimmed\\\_fastq/

cd \~/gen711-811/data/untrimmed\\\_fastq

```

Download the files (do not use unless instructed.See faster option)

```

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/004/SRR2589044/SRR2589044\\\_1.fastq.gz

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/004/SRR2589044/SRR2589044\\\_2.fastq.gz

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/003/SRR2584863/SRR2584863\\\_1.fastq.gz

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/003/SRR2584863/SRR2584863\\\_2.fastq.gz

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/006/SRR2584866/SRR2584866\\\_1.fastq.gz

curl -O ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR258/006/SRR2584866/SRR2584866\\\_2.fastq.gz

```

\### Faster option

If your workshop is short on time or the venue's internet connection is weak or unstable, learners can

avoid needing to download the data and instead use the data files provided in the '/tmp/Gen711-811\_data/' directory. Run fastqc on all of these files



For each input FASTQ file, FastQC has created a `.zip` file and a



`.html` file. The `.zip` file extension indicates that this is

actually a compressed set of multiple output files. We will be working

with these output files soon. The `.html` file is a stable webpage

displaying the summary report for each of our samples.



We want to keep our data files and our results files separate, so we

will move these

output files into a new directory within our `results/` directory.



```bash

$ mkdir -p \~/gen711-811/results/fastqc\\\_untrimmed\\\_reads

$ mv \\\*.zip \~/gen711-811/results/fastqc\\\_untrimmed\\\_reads/

$ mv \\\*.html \~/gen711-811/results/fastqc\\\_untrimmed\\\_reads/

```

Download the html files to view them.

\# Part B

::::::::::::::::::::::::::::::::::::::: objectives

\- Clean FASTQ reads using Trimmomatic.

\- Select and set multiple options for command-line bioinformatic tools.
::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions



\- How can I get rid of sequence data that does not meet my quality standards?



::::::::::::::::::::::::::::::::::::::::::::::::::



\## Cleaning reads



In the previous episode, we took a high-level look at the quality

of each of our samples using FastQC. We visualized per-base quality

graphs showing the distribution of read quality at each base across

all reads in a sample and extracted information about which samples

fail which quality checks. Some of our samples failed quite a few quality metrics used by FastQC. This does not mean,

though, that our samples should be thrown out! It is very common to have some quality metrics fail, and this may or may not be a problem for your downstream application. For our variant calling workflow, we will be removing some of the low quality sequences to reduce our false positive rate due to sequencing error.



We will use a program called

\[Trimmomatic](https://www.usadellab.org/cms/?page=trimmomatic) to

filter poor quality reads and trim poor quality bases from our samples.



\## Trimmomatic options



Trimmomatic has a variety of options to trim your reads. If we run the following command, we can see some of our options.



```bash

$ trimmomatic

```



Which will give you the following output:



```output

Usage: 

\&nbsp;      PE \\\[-version] \\\[-threads <threads>] \\\[-phred33|-phred64] \\\[-trimlog <trimLogFile>] \\\[-summary <statsSummaryFile>] \\\[-quiet] \\\[-validatePairs] \\\[-basein <inputBase> | <inputFile1> <inputFile2>] \\\[-baseout <outputBase> | <outputFile1P> <outputFile1U> <outputFile2P> <outputFile2U>] <trimmer1>...

\&nbsp;  or: 

\&nbsp;      SE \\\[-version] \\\[-threads <threads>] \\\[-phred33|-phred64] \\\[-trimlog <trimLogFile>] \\\[-summary <statsSummaryFile>] \\\[-quiet] <inputFile> <outputFile> <trimmer1>...

\&nbsp;  or: 

\&nbsp;      -version

```



This output shows us that we must first specify whether we have paired end (`PE`) or single end (`SE`) reads.

Next, we specify what flag we would like to run. For example, you can specify `threads` to indicate the number of

processors on your computer that you want Trimmomatic to use. In most cases using multiple threads (processors) can help to run the trimming faster. These flags are not necessary, but they can give you more control over the command. The flags are followed by positional arguments, meaning the order in which you specify them is important.

In paired end mode, Trimmomatic expects the two input files, and then the names of the output files. These files are described below. While, in single end mode, Trimmomatic will expect 1 file as input, after which you can enter the optional settings and lastly the name of the output file.



| option         | meaning                                                                                                      |

| -------------- | ------------------------------------------------------------------------------------------------------------ |

| \\<inputFile1>   | Input reads to be trimmed. Typically the file name will contain an `\\\_1` or `\\\_R1` in the name.                                          |

| \\<inputFile2>   | Input reads to be trimmed. Typically the file name will contain an `\\\_2` or `\\\_R2` in the name.                                          |

| \\<outputFile1P> | Output file that contains surviving pairs from the `\\\_1` file.                                                          |

| \\<outputFile1U> | Output file that contains orphaned reads from the `\\\_1` file.                                                           |

| \\<outputFile2P> | Output file that contains surviving pairs from the `\\\_2` file.                                                          |

| \\<outputFile2U> | Output file that contains orphaned reads from the `\\\_2` file.                                                           |



The last thing trimmomatic expects to see is the trimming parameters:



| step           | meaning                                                                                                      |

| -------------- | ------------------------------------------------------------------------------------------------------------ |

| `ILLUMINACLIP`               | Perform adapter removal.                                                                                     |

| `SLIDINGWINDOW`               | Perform sliding window trimming, cutting once the average quality within the window falls below a threshold. |

| `LEADING`               | Cut bases off the start of a read, if below a threshold quality.                                             |

| `TRAILING`               | Cut bases off the end of a read, if below a threshold quality.                                               |

| `CROP`               | Cut the read to a specified length.                                                                          |

| `HEADCROP`               | Cut the specified number of bases from the start of the read.                                                |

| `MINLEN`               | Drop an entire read if it is below a specified length.                                                       |

| `TOPHRED33`               | Convert quality scores to Phred-33.                                                                          |

| `TOPHRED64`               | Convert quality scores to Phred-64.                                                                          |



We will use only a few of these options and trimming steps in our

analysis. It is important to understand the steps you are using to

clean your data. For more information about the Trimmomatic arguments

and options, see \[the Trimmomatic manual](https://www.usadellab.org/cms/uploads/supplementary/Trimmomatic/TrimmomaticManual\_V0.32.pdf).



However, a complete command for Trimmomatic will look something like the command below. This command is an example and will not work, as we do not have the files it refers to:



```bash

$ trimmomatic PE -threads 4 SRR\\\_1056\\\_1.fastq SRR\\\_1056\\\_2.fastq  \\\\

\&nbsp;             SRR\\\_1056\\\_1.trimmed.fastq SRR\\\_1056\\\_1un.trimmed.fastq \\\\

\&nbsp;             SRR\\\_1056\\\_2.trimmed.fastq SRR\\\_1056\\\_2un.trimmed.fastq \\\\

\&nbsp;             ILLUMINACLIP:SRR\\\_adapters.fa SLIDINGWINDOW:4:20

```



In this example, we have told Trimmomatic:



| code           | meaning                                                                                                      |

| -------------- | ------------------------------------------------------------------------------------------------------------ |

| `PE`               | that it will be taking a paired end file as input                                                            |

| `-threads 4`               | to use four computing threads to run (this will speed up our run)                                            |

| `SRR\\\_1056\\\_1.fastq`               | the first input file name                                                                                    |

| `SRR\\\_1056\\\_2.fastq`               | the second input file name                                                                                   |

| `SRR\\\_1056\\\_1.trimmed.fastq`               | the output file for surviving pairs from the `\\\_1` file                                                                |

| `SRR\\\_1056\\\_1un.trimmed.fastq`               | the output file for orphaned reads from the `\\\_1` file                                                                 |

| `SRR\\\_1056\\\_2.trimmed.fastq`               | the output file for surviving pairs from the `\\\_2` file                                                                |

| `SRR\\\_1056\\\_2un.trimmed.fastq`               | the output file for orphaned reads from the `\\\_2` file                                                                 |

| `ILLUMINACLIP:SRR\\\_adapters.fa`               | to clip the Illumina adapters from the input file using the adapter sequences listed in `SRR\\\_adapters.fa`                     |

| `SLIDINGWINDOW:4:20`               | to use a sliding window of size 4 that will remove bases if their phred score is below 20                    |



:::::::::::::::::::::::::::::::::::::::::  callout



\## Multi-line commands



Some of the commands we ran in this lesson are long! When typing a long

command into your terminal, you can use the `\\\\` character

to separate code chunks onto separate lines. This can make your code more readable.





::::::::::::::::::::::::::::::::::::::::::::::::::



\## Running Trimmomatic



Now we will run Trimmomatic on our data. To begin, navigate to your `untrimmed\\\_fastq` data directory:



```bash

$ cd \~/gen711-811/data/untrimmed\\\_fastq

```



We are going to run Trimmomatic on one of our paired-end samples.

While using FastQC we saw that Nextera adapters were present in our samples.

The adapter sequences came with the installation of trimmomatic, so we will first copy these sequences into our current directory.



\### NOTE: This next step will proably not work. Think about using the 'which' command and see if you can find out where these adaptors are



```bash

$ cp \~/.miniconda3/pkgs/trimmomatic-0.38-0/share/trimmomatic-0.38-0/adapters/NexteraPE-PE.fa .

```



We will also use a sliding window of size 4 that will remove bases if their

phred score is below 20 (like in our example above). We will also

discard any reads that do not have at least 25 bases remaining after

this trimming step. Three additional pieces of code are also added to the end

of the ILLUMINACLIP step. These three additional numbers (2:40:15) tell

Trimmimatic how to handle sequence matches to the Nextera adapters. A detailed

explanation of how they work is advanced for this particular lesson. For now we

will use these numbers as a default and recognize they are needed to for Trimmomatic

to run properly. This command will take a few minutes to run.



```bash

$ trimmomatic PE SRR2589044\\\_1.fastq.gz SRR2589044\\\_2.fastq.gz \\\\

\&nbsp;               SRR2589044\\\_1.trim.fastq.gz SRR2589044\\\_1un.trim.fastq.gz \\\\

\&nbsp;               SRR2589044\\\_2.trim.fastq.gz SRR2589044\\\_2un.trim.fastq.gz \\\\

\&nbsp;               SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:NexteraPE-PE.fa:2:40:15

```



```output

TrimmomaticPE: Started with arguments:

\&nbsp;SRR2589044\\\_1.fastq.gz SRR2589044\\\_2.fastq.gz SRR2589044\\\_1.trim.fastq.gz SRR2589044\\\_1un.trim.fastq.gz SRR2589044\\\_2.trim.fastq.gz SRR2589044\\\_2un.trim.fastq.gz SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:NexteraPE-PE.fa:2:40:15

Multiple cores found: Using 2 threads

Using PrefixPair: 'AGATGTGTATAAGAGACAG' and 'AGATGTGTATAAGAGACAG'

Using Long Clipping Sequence: 'GTCTCGTGGGCTCGGAGATGTGTATAAGAGACAG'

Using Long Clipping Sequence: 'TCGTCGGCAGCGTCAGATGTGTATAAGAGACAG'

Using Long Clipping Sequence: 'CTGTCTCTTATACACATCTCCGAGCCCACGAGAC'

Using Long Clipping Sequence: 'CTGTCTCTTATACACATCTGACGCTGCCGACGA'

ILLUMINACLIP: Using 1 prefix pairs, 4 forward/reverse sequences, 0 forward only sequences, 0 reverse only sequences

Quality encoding detected as phred33

Input Read Pairs: 1107090 Both Surviving: 885220 (79.96%) Forward Only Surviving: 216472 (19.55%) Reverse Only Surviving: 2850 (0.26%) Dropped: 2548 (0.23%)

TrimmomaticPE: Completed successfully

```



:::::::::::::::::::::::::::::::::::::::  challenge



\## Exercise



Use the output from your Trimmomatic command to answer the

following questions.



1\) What percent of reads did we discard from our sample?



   ANSWER: 0.23%



2\) What percent of reads did we keep both pairs?



   ANSWER: 79.96%





::::::::::::::::::::::::::::::::::::::::::::::::::



You may have noticed that Trimmomatic automatically detected the

quality encoding of our sample. It is always a good idea to

double-check this or to enter the quality encoding manually.



We can confirm that we have our output files:



```bash

$ ls SRR2589044\\\*

```



```output

SRR2589044\\\_1.fastq.gz       SRR2589044\\\_1un.trim.fastq.gz  SRR2589044\\\_2.trim.fastq.gz

SRR2589044\\\_1.trim.fastq.gz  SRR2589044\\\_2.fastq.gz         SRR2589044\\\_2un.trim.fastq.gz

```



The output files are also FASTQ files. It should be smaller than our

input file, because we have removed reads. We can confirm this:



```bash

$ ls SRR2589044\\\* -l -h

```



```output

-rw-rw-r-- 1 dcuser dcuser 124M Jul  6 20:22 SRR2589044\\\_1.fastq.gz

-rw-rw-r-- 1 dcuser dcuser  94M Jul  6 22:33 SRR2589044\\\_1.trim.fastq.gz

-rw-rw-r-- 1 dcuser dcuser  18M Jul  6 22:33 SRR2589044\\\_1un.trim.fastq.gz

-rw-rw-r-- 1 dcuser dcuser 128M Jul  6 20:24 SRR2589044\\\_2.fastq.gz

-rw-rw-r-- 1 dcuser dcuser  91M Jul  6 22:33 SRR2589044\\\_2.trim.fastq.gz

-rw-rw-r-- 1 dcuser dcuser 271K Jul  6 22:33 SRR2589044\\\_2un.trim.fastq.gz

```



We have just successfully run Trimmomatic on one of our FASTQ files!

However, there is some bad news. Trimmomatic can only operate on

one sample at a time and we have more than one sample. The good news

is that we can use a `for` loop to iterate through our sample files

quickly!



We unzipped one of our files before to work with it, let's compress it again before we run our for loop.



```bash

gzip SRR2584863\\\_1.fastq 

```



```bash

for infile in \\\*\\\_1.fastq.gz

do

\&nbsp; base=$(basename ${infile} \\\_1.fastq.gz)

\&nbsp; trimmomatic PE ${infile} ${base}\\\_2.fastq.gz \\\\

\&nbsp;              ${base}\\\_1.trim.fastq.gz ${base}\\\_1un.trim.fastq.gz \\\\

\&nbsp;              ${base}\\\_2.trim.fastq.gz ${base}\\\_2un.trim.fastq.gz \\\\

\&nbsp;              SLIDINGWINDOW:4:20 MINLEN:25 ILLUMINACLIP:NexteraPE-PE.fa:2:40:15 

done

```



Go ahead and run the for loop. It should take a few minutes for

Trimmomatic to run for each of our six input files. Once it is done

running, take a look at your directory contents. You will notice that even though we ran Trimmomatic on file `SRR2589044` before running the for loop, there is only one set of files for it. Because we matched the ending `\\\_1.fastq.gz`, we re-ran Trimmomatic on this file, overwriting our first results. That is ok, but it is good to be aware that it happened.



```bash

$ ls

```



```output

NexteraPE-PE.fa               SRR2584866\\\_1.fastq.gz         SRR2589044\\\_1.trim.fastq.gz

SRR2584863\\\_1.fastq.gz         SRR2584866\\\_1.trim.fastq.gz    SRR2589044\\\_1un.trim.fastq.gz

SRR2584863\\\_1.trim.fastq.gz    SRR2584866\\\_1un.trim.fastq.gz  SRR2589044\\\_2.fastq.gz

SRR2584863\\\_1un.trim.fastq.gz  SRR2584866\\\_2.fastq.gz         SRR2589044\\\_2.trim.fastq.gz

SRR2584863\\\_2.fastq.gz         SRR2584866\\\_2.trim.fastq.gz    SRR2589044\\\_2un.trim.fastq.gz

SRR2584863\\\_2.trim.fastq.gz    SRR2584866\\\_2un.trim.fastq.gz

SRR2584863\\\_2un.trim.fastq.gz  SRR2589044\\\_1.fastq.gz

```



:::::::::::::::::::::::::::::::::::::::  challenge



\## Exercise



We trimmed our fastq files with Nextera adapters,

but there are other adapters that are commonly used.

What other adapter files came with Trimmomatic?







\## Solution Output



```output

NexteraPE-PE.fa  TruSeq2-SE.fa    TruSeq3-PE.fa

TruSeq2-PE.fa    TruSeq3-PE-2.fa  TruSeq3-SE.fa

```



:::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::::::::::::::::



We have now completed the trimming and filtering steps of our quality

control process! Before we move on, let's move our trimmed FASTQ files

to a new subdirectory within our `data/` directory.



```bash

$ cd \~/gen711-811/data/untrimmed\\\_fastq

$ mkdir ../trimmed\\\_fastq

$ mv \\\*.trim\\\* ../trimmed\\\_fastq

$ cd ../trimmed\\\_fastq

$ ls

```



```output

SRR2584863\\\_1.trim.fastq.gz    SRR2584866\\\_1.trim.fastq.gz    SRR2589044\\\_1.trim.fastq.gz

SRR2584863\\\_1un.trim.fastq.gz  SRR2584866\\\_1un.trim.fastq.gz  SRR2589044\\\_1un.trim.fastq.gz

SRR2584863\\\_2.trim.fastq.gz    SRR2584866\\\_2.trim.fastq.gz    SRR2589044\\\_2.trim.fastq.gz

SRR2584863\\\_2un.trim.fastq.gz  SRR2584866\\\_2un.trim.fastq.gz  SRR2589044\\\_2un.trim.fastq.gz

```



:::::::::::::::::::::::::::::::::::::::  challenge



:::::::::::::::  solution



\## Solution



In your terminal window do:



```bash

$ fastqc \~/gen711-811/data/trimmed\\\_fastq/\\\*.fastq\\\*

```

Then take a look at the html files in your browser.



Remember to replace everything between the `@` and `:` in your scp

command with your AWS instance number.



After trimming and filtering, our overall quality is much higher,

we have a distribution of sequence lengths, and more samples pass

adapter content. However, quality trimming is not perfect, and some

programs are better at removing some sequences than others. Because our

sequences still contain 3' adapters, it could be important to explore

other trimming tools like \[cutadapt](https://cutadapt.readthedocs.io/en/stable/) to remove these, depending on your

downstream application. Trimmomatic did pretty well though, and its performance

is good enough for our workflow.







:::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::::::::::::::::



:::::::::::::::::::::::::::::::::::::::: keypoints



\- The options you set for the command-line tools you use are important!

\- Data cleaning is an essential step in a genomics workflow.



::::::::::::::::::::::::::::::::::::::::::::::::::



::::::::::::::::::::::::::::::::::::::::::::::::::



**########################################################
**PRACTICAL**
**#######################################################

\## Gen711/811 Practical Exam 2023 (40 scaled points)



\## NAME: MYNAME



Instructions:  

\- Make sure to paste all the commands that you use below each of the tasks.  

\- Some tasks require you to copy your output here. All output that you paste is less than 10 lines.   

\- Do not spend too much time on a single prompt. It's important to get to all prompts.    

\- If you get stuck and do not know how to proceed: specifically ask for the answer.  

\- Help will get you to the next step, but you will lose points for that prompt.  

\- Questions on clarification of the question does not result in the loss of points.  

\- Replace MYNAME with your first and last name.   

\- Download the practical into your gen711/811 folder as indicated at the begining of class. 

\- Keep the '.md' extension until you turn it in. 

\- Right before you upload it, save it as a '.txt' document MYNAME\_practical.txt. 

\- Save the document to your lab folder so that you know where it is when you need to upload it.

\- Document must be uploaded before 5pm to get credit. 



Hints: 

\- Remember, if you want to re-run a command, but change it slightly to try to fix it, hit the up arrow and edit the last command that you ran. 

\- When typing out commands, filenames, or paths, hit the tab button a couple time to see if it autocompletes for you



\### 1. Paste the command(s) below that you used get practical exam pasted into vscode. (2 point)



\### 2. From your home directory, make a new directory to hold fastq files called 'analysis' (2 points)



cd

mkdir Analysis



\### 3. Copy the fastq files /tmp/gen711\_2023/Sample1.fastq and /tmp/gen711\_2023/Sample2.fastq directly into the 'analysis' directory without changing your current directory. (2 points, partial credit if you need to change directories first)

For todays practice practical, use SRR fastqs instead



cp /home/users/sen97/gen711-811/shell\_data/untrimmed\_fastq/SRR098026.fastq /home/users/sen97/Analysis



cp /home/users/sen97/gen711-811/shell\_data/untrimmed\_fastq/SRR097977.fastq /home/users/sen97/Analysis



\### 4. Use an absolute path to change your current working directory to the 'analysis' folder/directory. (2 points, partial credit for using a relative path)



cd /home/users/sen97/Analysis



\### 5. The fastq file you just copied is data from the UNH genome center. This is the first time you've ever seen these FASTQs. To confirm that the format of the FASTQs look ok, view one of the two files and paste the top 4 lines of the file below. (4 points) 



head -4 SRR097977.fastq 



@SRR097977.1 209DTAAXX\_Lenski2\_1\_7:8:3:710:178 length=36

TATTCTGCCATAATGAAATTCGCCACTTGTTAGTGT

+SRR097977.1 209DTAAXX\_Lenski2\_1\_7:8:3:710:178 length=36

CCCCCCCCCCCCCCC>CCCCC7CCCCCCACA?5A5<



\### 6. You've decided that you want to make a seperate file of the reads to BLAST them at NCBI to make sure they belong to the species that you seqiuenced. However, your blast program is written to accept FASTA files rather than FASTQ files (FASTA files only contain the header line above the read, and the read itself). You will need to make a 'FASTA' file from each FASTQ file. Before you make the new files, pipe the output to a command that that allows you to see just the first lines of the output. (5 points)  



grep -A1 '^@' SRR097977.fastq --no-group-separator | head



\#### Hints: 

\### FASTA only needs 2/4 lines that are in a FASTQ: 1) the header line that starts with '@' and 2) the sequence right after the header. However, the base call quality scores could contain '@' as well, which might lead to unwanted matches. 

\### You can use the info in the header line to be very specific about what you are trying to match. 

\### Add the '--no-group-separator' option to the other options of your command to keep the '--' out of the output



\### 7. Redirect the output of your command (command in 6 that is converting the format of the FASTQ into FASTA) into new files. Give the new file the same names, but uses the '.fasta' extension rather than the '.fastq' extension of the original file name. (5 points)



grep -A1 '^@' SRR097977.fastq --no-group-separator > SRR097977.fasta 

grep -A1 '^@' SRR098026.fastq --no-group-separator > SRR098026.fasta



\### 8. How many reads have 15 or more uncalled bases (NNNNNNNNNNNNNNN) in both samples? Count the number of reads in both WITHOUT making a new file. (4 points)



grep NNNNNNNNNNNNNNN SRR098026.fasta SRR097977.fasta | wc -l



\### 9. Make a new directory called 'to\_blast' in your current directory. Then, move the two fasta files into this new 'to\_blast' directory (4 points)



mkdir to\_blast | mv \*fasta to\_blast



\### 10. Without changing directories, what command could you use to confirm that the files made it into the 'to\_blast' folder. (2 points)



ls to\_blast



\### 11. What is the 100th line in the Sample1.fasta file? (hint: the 'head' command is one way to do this- but you may need to specify an option) (2 points)



head -100 SRR097977.fasta | tail -1

GCGGAGCTGGTGATTGGCGAACTGCTGCTGCTATTT



\### 12. Run md5sum on Sample1.fasta (md5sum Sample1.fasta). Then, run it again, but redirect the output to a new file called 'my\_md5sums.txt'.  (2 points)



md5sum SRR097977.fasta > my\_md5sums.txt



\### 13. Next, run the md5sum command on Sample2.fasta and add it the the end of 'my\_md5sums.txt'. (2 points)



md5sum SRR098026.fasta >>  my\_md5sums.txt



\### 14. Lastly, add your name to the end of 'my\_md5sums.txt' file. (2 points)



echo "Sara Smith" >> my\_md5sums.txt



\### Extra credit: Run fastqc on one of the fastq files, and one of the fasta files. Did they both run? Why or why not?  (2 points)

