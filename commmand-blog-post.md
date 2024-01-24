# How to Use Basic Filesystem Commands!
When traversing the magical world of files and directories, sometimes you may only have access to your terminal (or perhaps you prefer to feel like you're coding in the 60s).  When doing
so, there are **very** important commands that you should know.

In this fantabulous blogpost, we will be showcasing how to use the following commands:
* `cd`
* `ls`
* `cat`

Commands such as these can, or in some cases must, have a path that must follow after it when typing it into the terminal.  Therefore, there are three possibilities when running the command:
* The command is run with no path following it
* The command is followed by a directory
* The command is followed by a file

Because this blogpost champions thorough scrutiny, we will be showing all three possibilities for the three commands, making a grand total of NINE examples.  Each example will be
provided with a picture of the terminal and a **short** explanation of the output it relates to.

*important note: we will assume that the workspace we will be utiziling has the following files and directories*
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/fc40f9df-6fc3-43c9-abe0-78d16a8aa549)


---

# Changing a Directory
Judging by the title, it may be clear what `cd` stands for.  Spoilers: it changes the working directory.  When in your terminal, the program uses your working directory to resolve any relative paths, and the `cd` command
aids in switching this working directory.  To help keep track of the current working directory, it is useful to use the `pwd` command to "Print the Working Directory."  These names all sort
of make sense.

## No Argument
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/574b5b77-e830-4b34-8d7b-61293db925b4)

By using the `pwd` command, we can see that the initial working directory is **/home**.  The `cd` command with no arguments appears to have no output, and using the `pwd` command again shows that the working directory has not changed locations.  However, it can be seen that something DOES happen if the working directory is not the **/home** directory.  
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/a70a9e53-db11-4c55-a3b3-2fd86811fe0e)

In actuality, the `cd` command with no argument takes your working directory to the **/home** directory, and it just wasn't apparent at first because we starting there in the first example.  The working dirctory was **/home/lecture1/messages** and the empty `cd` command takes the working directory back to **/home**.  This doesn't seem like an error, but rather just a function of convenience for the user if it is necessary to go back to the **/home**.  

## Directory Path
You may be wondering how I had the working directory changed to **/home/lecture1/messages** in my last example.  Well, this next example will showcase how!

![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/48027553-71b7-4009-b418-610f022dca2f)

Using the `pwd` command to see that we are starting from **/home**, typing the `cd` command followed by a space and the relative path we want to change the working directory to simply... changes the working directory to the absolute path we want to change it to.  Since I typed **lecture1/messages** after `cd`, it changed the working directory from **/home** to **/home/lecture1/messages**.  You can type the relative path you want to travel to, or you can type the full absolute path.  Either works!  No errors seem to have appeared in the example I showed.

## File Path
Some things get a little finicky when the absolute path you want to travel to is a file itself, and not a directory.
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/27850d98-5576-41db-8d79-939f5e4fe345)

Let's say we are starting in the **/home** directory again and we want to change the working directory to the file en-us.txt.  What we can try to do is use our handy `cd` command followed by the relative path of **lecture1/messages/en-us.txt**.  However, the command line spits out a sort of error message and reads the above.  The working directory can only be directories, so the command output instead spits out the relative path you're trying to access and tells you it is not a directory.  Files are not directories!!! Keep in mind that the working directory does not move to anywhere else as a result, still being at **/home**.  

---

# Listing Files and Folders of Path
Directories and files can only be accessed from a parent dirctory, and if you don't have access to a sidebar that shows the relative location of your files and directories, then it would be near impossible to know whether you can access certain files or not.  This is where the `ls` command comes in handy!  It has the beautiful feature of printing out all the files and directories of a certain path.

## No Argument
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/0c7b57f3-775a-4d76-819c-0a0baaf91d34)

If your working directory is **/home**, then the `ls` command prints out the only directory name in **/home**: lecture1.  It may seem that having no argument would always print out the contents of **/home**, similar to the empty command of `cd`.  However, if you change the working directory to **/home/lecture1**, then the `ls` command prints the files and directory names within lecture1.  The reasonable conclusion is that an empty `ls` command prints out the file and directory names of the current working directory.  This is not an error and seems to be an intentional shortcut for the user.

## Directory Path
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/72e34cbb-452e-4d4b-92cb-70f61b4aa104)

The working directory in this example is the directory **/home**, and typing in a relative path in the command line prints out the names of the files and directories in the resolved absolute path.  In the example, the names of the files in the messages directory were printed.  It can also be seen that doing so does not change the working directory, and it remains as **/home**.  No errors are present here.  This is the intended way to use the command `ls`, and is a quick and easy way to see an overview of any section of your workspace.

## File Path
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/5894491e-ed6a-4f71-8ef6-27925f527f77)

The results of typing the `ls` command followed by a file path has a relatively simple output, but the explanation in words can be a bit lengthy so try not to get lost in all the words.  The picture above does a great job in helping keep track of what I'm about to type.  In summary though, if you try to use the `ls` command on a relative path that leads to a file and not a directory, the output is exactly the relative path you type in the `ls` command.  In the first attempt starting in the **/home** directory, the `ls` command is typed with **lecture1/messages/en-us.txt**, and since it leads to a file, the output is simply **lecture1/messages/en-us.txt**.  To experiment with this, we change the directory to the messages and attempt to access the same file with just the relative path **en-us.txt**, since we are already in the working directory messages.  This spits out an output of just **en-us.txt**.  None of the `ls` commands changes the working directory.  In conclusion, we can see that the `ls` command typed with a file path does not just print of the absolute path of the file, but rather just what the user inputs as the relative path.  The `ls` command attempts to print out the files and directories of a given path, so it prints out the only thing present at the path of the file, so this is not necessarily an error.

---

# Concatenating File Contents
The `cd` and `ls` command both don't seem to be of any use for us when wanting to access files, so what can we use?  This is where the `cat` command comes in handy (short for concatenate).  This command prints the text within a file as an output.

## No Argument
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/8dfd8c33-7532-4ced-a7e7-42ebc23dda60)
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/e8c00181-4134-405d-9824-b6c19d89fefb)


The `cat` command with no argument brings about the oddest output we've witnessed so far.  If you are in the directory **/home** and type the cat command, the terminal "kicks you off" the command line and the terminal does not respond to any commands.  Typing control+C on Mac restores the terminal and puts you back on a command line.  This happens if the working directory contains files, such as the messages directory.  With a little experimenting, we can see that inputting text afterwards causes the terminal to return exactly what we type and enter.  It seems that instead of reading data from a given file, it reads the data from the keyboard's inputs directly.  It works multiple times, so this doesn't seem to be an error, and again, you can escape by doing control+C.

## Directory Path
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/91d7e90b-86eb-4282-baa8-946fc4786ebd)

In both commands run above, the working directory is **/home**.  Typing the `cat` command and following it by the relative (or absolute) path of the directory **lecture1** produces an output that tells the user that the path they typed "Is a directory."  Doing this for a directory containing files, such as messages, still produces a similar output.  In conclusion, typing the `cat` command with a relative path that resolves to a directory spits out an error message that tells the user that the relative path "Is a directory" and cannot print out anything else.

## File Path
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/df8878fe-01fd-4ca2-ae8f-2aaf42e2b988)

Onto the intended method of using the code, typing a relative path to a file after the `cat` outputs all of the text in the aforementioned file.  Even if the working directory is **/home**, as long as the correct relative path is typed, the terminal can print out the contents of any file it can access.  A cool property of the `cat` command is that it allows you to print multiple files at once.  By typing spaces between each file path you want to print, it prints out the files in the order typed and with a line break between each.  No errors here folks! This is the intended way to use the `cat` command.

---

# Conclusion
Thank you for reading my blogpost! I hope you learned something for the next time you want to traverse your next directory!
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/dd4c45c1-e8b8-45c2-882f-fa113b994340)
