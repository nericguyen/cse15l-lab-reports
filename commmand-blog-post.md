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

*side note: we will assume that the workspace we will be utiziling has the following files and directories*
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/fc40f9df-6fc3-43c9-abe0-78d16a8aa549)


---

# Changing a Directory
Judging by the title, it may be clear what `cd` stands for.  Spoilers: it changes the working directory.  When in your terminal, the program uses your working directory to resolve any relative paths, and the `cd` command
aids in switching this working directory.  To help keep track of the current working directory, it is useful to use the `pwd` command to "Print the Working Directory."  These names all sort
of make sense.

## No Argument
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/574b5b77-e830-4b34-8d7b-61293db925b4)
By using the `pwd` command, we can see that the initial working directory is the root **/home**.  The `cd` command with no arguments appears to have no output, and using the `pwd` command again shows that the working directory has not changed locations.  However, it can be seen that something DOES happen if the working directory is not the root **/home** directory.  
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/a70a9e53-db11-4c55-a3b3-2fd86811fe0e)
In actuality, the `cd` command with no argument takes your working directory to the root **/home** directory, and it just wasn't apparent at first because we starting there in the first example.  The working dirctory was **/home/lecture1/messages** and the empty `cd` command takes the working directory back to **/home**.  This doesn't seem like an error, but rather just a function of convenience for the user if it is necessary to go back to the root.  

## Directory Path
You may be wondering how I had the working directory changed to **/home/lecture1/messages** in my last example.  Well, this next example will showcase how!
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/48027553-71b7-4009-b418-610f022dca2f)
Using the `pwd` command to see that we are starting from **\home**, typing the `cd` command followed by a space and the relative path we want to change the working directory to simply... changes the working directory to the absolute path we want to change it to.  Since I typed **lecture1/messages** after `cd`, it changed the working directory from **\home**
to **/home/lecture1/messages**.  Be sure not to include the current root you're working in.  For example, notice how I omitted **/home** from my command line.  You have to type the relative path you want to travel to, not the full absolute path.  No errors seem to have appeared in the example I showed.

## File Path
Some things get a little finicky when the absolute path you want to travel to is a file itself, and not a directory.
![image](https://github.com/nericguyen/cse15l-lab-reports/assets/149546505/27850d98-5576-41db-8d79-939f5e4fe345)
Let's say we are starting in the **/home** root again and we want to change the working directory to the file en-us.txt.  What we can try to do is use our handy `cd` command followed by the relative path of **lecture1/messages/en-us.txt**.  However, the command line spits out a sort of error message and reads the following above.  The working directory can only be directories, so the command output instead spits out the relative path you're trying to access and tells you it is not a directory.  Keep in mind that the working directory does not move to anywhere else as a result, still being at **/home**
