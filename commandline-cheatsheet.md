#### Shell Prompt Explanation
Entering or running a command refers to typing a given command and pressing [Enter]. To close a terminal window, either click on the [X] in the upper right corner of the screen or enter the exit command at the shell prompt.   

The shell prompt within a terminal window looks something like this:

```[student@localhost.localdomain student]$```  

There are any number of symbols that can be used to indicate the end of the shell prompt, and you can customize what your prompt looks like. However, there are two symbols that you will see more often than any others, "$" and "#". The first symbol, "$", is the last character in the prompt when you are logged in as a normal user. The shell prompt for a normal user looks something like this:

```[student@localhost.localdomain student]$```

The second symbol, "#", is the last character in the prompt when you are logged in as root. This is true whether you logged in as root from the initial screen or if you executed the ```su -``` or ```sudo -i``` commands to become root. The shell prompt for root looks something like this:

```[root@localhost.localdomain root]#```  

This slight difference can help remind you what privileges you currently have. Also take note the usernames have changed as well.

The one constant in this case is the hostname or machine name in the shell prompt. In the above examples this is represented by "@localhost.localdomain". Pay attention to this portion of the prompt when working with ssh (remoting) as it may alleviate any confusion of the machine a command will be entered and ran on.

The second instance of the user name (ex. ...root]# or student]$) is actually representing the current directory the shell prompt is in. In that case of root it's current working directory would be the root home directory located in ```/root``` and in the case of the student user it's current working directory would be located in the default location for all users (except root) in the ```/home``` directory under it's own perspective directory ```/home/student```. You can also check the current working directory by use the ```pwd``` command.

#### Print Working Directory  
Print the name of the current working directory  
```[student@korora~]$ pwd```

#### List of Files and Directories  
To see the list of files and directories  
```[student@korora~]$ ls <options> <arguments>```

ls Options | Explanation
---- | ----
```-l``` | Long list including attributes
```-a``` | All files and directories including hidden
```-d``` | For a particular file or directory
```-R``` | Recursive to see the tree structure

### Creation of files

Files can be created by using any of the three methods given below:
* Cat command
* Touch command
* Vi editor

#### Cat (Concatenation) Command
Creating and displayed text files  
```[student@korora~]$ cat <option> <arguments><filesname>```

To create a file  
```[student@korora~]$ cat > <filename>```  

To view the contents of a file  
```[student@korora~]$ cat <filename>```

To append or add to an existing file   
```[student@korora~]$ cat >> <filename>```

To combines the data of two or more files into a third file  
```[student@korora~]$ cat <first file> <second file> >> <third file>```   

#### Touch Command
To create a zero byte file  
```[student@korora~]$ touch <filename>```

To create multiple zero byte files  
```[student@korora~]$ touch <first file> <second file> <third file>```

To change the time stamp of a file or directory  
```[student@korora~]$ touch <directory or filename>```

#### Vi Editor  
##### To create a file
```[student@korora~]$ vi <filename>```

#### Creating Directories  
To create a directory  
```[student@korora~]$ mkdir <directory name>```  

To create multiple directories   
```[student@korora~]$ mkdir <first dir> <second dir> <third dir>```

To create nested directories   
```[student@korora~]$ mkdir -p <first dir>/<second dir>/<third dir>```  

#### Navigation of Directories
To change the directory   
```[student@korora~]$ cd <path of the directory>```

To change directory one level back   
```[student@korora~]$ cd ..```

To change directory two levels back   
```[student@korora~]$ cd ../..```

To change to the last working directory   
```[student@korora~]$ cd -```

To change to the users home directory  
```[student@korora~]$ cd```

#### To view the manual page of a command
```[student@korora~]$ man <command>```

#### Copying
To copy a file or directory   
```[student@korora~]$ cp <options> <source file> <destination>```  

cp Options | Explanation
---- | ----
```-r``` | Recursive (to copy the directory along with its contents)
```-v``` | Verbose
```-p``` | Copy with permissions
```-b``` | make a backup of each existing destination marking the end of the file name with ~

#### Moving and Renaming   
To move a file or directory to a different location   
```[student@korora~]$ mv <source file or directory> <destination>```

Rename a file or directory  
```[student@korora~]$ mv <old name> <new name>```

#### Deleting
To remove or delete an empty directory  
```[student@korora~]$ rmdir <directory name>```

To remove or delete a file or directory   
```[student@korora~]$ rm <option> <file or directory name>```

rm Options | Explanation
---- | ----
-r | Recursive (directory along with contents)
-f | forcefully

#### Time related commands
To see the date   
```[student@korora~]$ date```

To see the calendar  
```[student@korora~]$ cal```  

#### File Viewing Commands
To view the contents of a file with the ability to scroll and search  
```[student@korora~]$ less <file name>```

To view the top lines of a file (10 lines by default)  
```[student@korora~]$ head <filename>```  
```[student@korora~]$ head -n5 <filename>```

To view the bottom line of a file (10 lines by default)  
```[student@korora~]$ tail <filename>```  
```[student@korora~]$ tail -n3 <filename>```

#### File Investigation
To get character, word, and line count of a text file   
```[student@korora~]$ wc <options> <filenames>```   

wc Options | Explanation     
---- | ----
```-l``` | Prints the number of lines in a file.
```-w``` | Prints the number of words in a file.
```-c``` | Displays the count of bytes in a file.
```-m``` | Prints the count of characters from a file.
```-L``` | Prints only the length of the longest line in a file.


#### VI editor modes
VI editor has three modes of operations
* Command Mode
* Insert mode
* Ex Mode (Extended Command Mode)

Insert Mode | Explanation  
---- | ----
```I``` | Insert the text at the current cursor position.
```l``` | Insert the text in beginning of a line
```a``` | Adds the text after the current cursor position
```A``` | Adds the text at the end of a line
```o``` | Insert the text one line below current cursor position
```O``` | Insert the text one line above current cursor position

Ex mode | Explanation  
---- | ----
```:q``` | Quit without saving
```:q!``` | Quit forcefully without saving
```:w``` | Write (save)
```:wq``` | Save and quit
```:wq!``` | Save and quit forcefully
```:se nu``` | sets line numbers
```:se nonu``` | Remove line numbers
```:84``` | The cursor goes to line 84

Command Mode | Explanation  
---- | ----
```dd``` | Deletes a line
```ndd``` (ex. 5dd) | Deletes ‘n’ lines
```yy``` | Copies a line
```nyy``` (ex. 5yy)| Copies ‘n’ lines
```p``` | Put (pastes the deleted or copied text)
```u``` | Undo(you can undo 1000 times)
```G``` | Moves the cursor to the last line of the file
