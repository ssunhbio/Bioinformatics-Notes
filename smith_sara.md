2/6/2026

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
