2/6/2026

## The key points here are:
- The shell gives you the ability to work more efficiently by using keyboard commands rather than a GUI.
- Useful commands for navigating your file system include: ls, pwd, and cd.
- Most commands take options (flags) which begin with a -.
- Tab completion can reduce errors from mistyping and make work more efficient in the shell.

# Navigating Files and Directories
- How can I perform operations on files outside of my working directory?
- What are some navigational shortcuts I can use to make my work more efficient?

# Part 2 (lab 3)
## Objectives:
- Use a single command to navigate multiple steps in your directory structure, including moving backwards (one level up).
- Perform operations on files in directories outside your working directory.
- Work with hidden directories and hidden files.
- Interconvert between absolute and relative paths.
- Employ navigational shortcuts to move around your file system.

## More navigation
- We got an idea for moving around using cd and the name of the folder to move into. 
- But how to we go back out? We dont see the folder we are in.
- We have a special command to tell the computer to move us back or up one directory level.

### Your Notes Here: 
Seperate notes by an empty line, or they'll get pasted together.

- Using a dash is helpful for lists
1. And numbers for lists

The pound sign is used for 'sections'. A single pound (or hashtag) in front of a word makes it appear bigger/bold to show a new section. See below

# My Notes:

To change directories, use 'cd' and then hit tab two times to see directories in my current directory. 

First command is print working directory (pwd). Within a directory, there might be more directories, or files in files. A directory tracked by git hub is a repository. 

To make a list of files in the directory, use ls. BASH commands have options, and the options will allow you to specify things.
Flavors of ls:  
1. ls-F - will show slashes to indicate if there are files, so you can determine if you want to change directories down or not.
2. man ls - manual for ls options. q will bring you back out of the manual.
3. ls -lrth prints extra information about the directories (when it was made, who owns it, etc.)

cd commands will let you navigate your directories:
1. cd ../ will step you back one level.  
2. cd ~ shorthand for your home directory.

An absolute path starts all the way back to the base or root of the computer vs a short cd (ex. /home/users/sen97/gen711-811/shell_data)

If you have an unclosed quote or parentheses, you can press ctrl+c to get out of it. It also works for ending active processes.  

In some cases we don't want to open up a whole file, because its huge, we just want to see the first few lines. So we can use the head command.

The echo command will tell you details about the variable you put in (ex. $home)
 
The History command will show you your coding history.  

grep will search through a file and return only the lines you are searching for. If you include the ^ symbol, it will tell the search to look for the thing you are looking for at the begining of the line.  

To redirect the output to a file, we can use the greater than symbol after your prompt (ex. grep "^@" SRR097977.fastq > headerlines.txt).

Pipe special character | Pipes an output to a different command, so we can count with word count, or wc, and add -l to tell it to count the number of lines.  If you just do wc alone, it will print lines, words, characters. Can also use ls | grep '^c' to search for  something (remember, ^ is "starts with").

The command less will let you scroll through the whole file.  

`### Complete the questions below when intrstructed. Push the changes to this document to recive credit for attending the lab

#### 1. What are 3 ways to change directories to your home directory from the  untrimmed_fastq directory?
1. cd $HOME
2. cd ../ (repeat until you get to the home)
3. cd ~
4. cd /home/users/sen97 (absolute path)

#### 2. How many programs in /bin 
2. Do each of the following tasks from your current directory using a single ls command for each:

    $ cd /bin (I used | wc -l to count)

    - List all of the files in /bin that start with the letter ‘c’.

    $  ls c*

    - List all of the files in /bin that contain the letter ‘a’.

    $  ls *a*

    - List all of the files in /bin that end with the letter ‘o’.

    $ ls *o

    - Bonus: List all of the files in /bin that contain the letter ‘a’ or the letter ‘c’.

    $ ls *[ac]*

#### Answers here
Start with the letter c _94_
Start with the letter a _49_
Start with the letter o _16_
Contain the letter ‘a’ or the letter ‘c’ _926_
Contain the letter a _644_
End with the letter o _34_

#### What command/commands would you use to find the line number in your history for the command that listed all the '.fastq' files using the absolute path. Paste your answer below.
history