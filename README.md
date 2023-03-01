# Bioinformatics-INBRE

Here you will learn everything from basic terminal commands to Python and R! Below will be some onboarding tutorials for each of the programs to get you started.

## Onboarding for Terminal (Bash Scripting)
### Logging in
To access Mana you must log into the shell. Password entry is Case sensitive and it may prompt you to complete a DuoPush
```
ssh <username>@uhhpc.its.hawaii.edu
```
Once you are done workign in the shell you can simply type ```exit``` and it will log you out.

### Navigating through the Cluster

Next we want to look at any files that we have stored in our system.
```
ls

ls -ltrh
```
Running ```ls``` will show you any files and directrories that you have. You can run ```ls``` with addtional code to give more information. ```l``` is long form (includes data information, owner permissions, and size). ```tr``` is sort by time and in reverse, so the newer files will be on the bottom. ```h``` is human readable so that files sizes are in KB, MB, GB.

You can also use ```ls``` to look into a directory without actually moving into one
```
# List the contents of your home directory
ls ~

# list contents of one directory up from where you are
ls .. 

# list the contents of the root directory
ls /

# list the contents of the t3\_2022 directory you made in your home directory

ls ~/t3_2022
```
When you first log in, you will automatically be in your home directory, but at any point you can check which working directory you are in with
```
pwd
```
This command will show the full patch that you are currently in. Do this often to make sure that you are workign in the correct directory.

If you are new, you probably do not have any files already created. To create a new file use
```
touch test.txt
```
This will create a new file in your current working directory. Bash will not add what file type it is to the end of the name, so here, adding .txt helps to identify the file type

To move around the cluster you use ```cd``` followed by a any path. If you enter ```cd``` on its own, you will be taken to the home directory.
```
cd /
```
This will tak you to your root directory. At any point you can return to your home directory by using
```
cd ~
```
You can also navigate to the directory above by using
```
cd ..
```
Chaining together such as, ../.. will take up you two directories, but always use ```pwd``` to double check where you are in your console 
In your home directory, you can make a new directory and navigate to it using
```
mkdir <name you would like to give it>
cd <name of directory>
```

### Moving, copying, and removing files

The move command - mv
```
mv <file name> <destination>
```
The copy comand - cp
```
cp <file name> <destination>
```
The remove command -rm
```
rm <file>
```
Be careful when using these commands because Linux/Terminal does not have a trashcan and there is no undo button. If something is deleted it is gone forever and it will not double check with you prior to deleting. ```cp``` and ```mv``` will overwirte the target destination with no warning on if it already exists.
```
# make a new directory
mkdir my_directory/

# move a file up one directory
mv my_file.txt ../

# move and rename a file
mv my_file.txt ../my_renamed_file.txt

# copy a file and rename
cp my_file.txt my_renamed_file.txt

# copy a file to a different directory without renaming
cp my_file.txt my_directory/

# remove a file
rm my_renamed_file.txt

# remove a directory with the -r option, recursive
rm -r my_directory/
```

### Finding help for a command

At any point you can as for help by typing ```--help``` after a command. For example, ```ls --help``` will give you information on how to use ```ls```. A lot of commands also have a lot of documentation and additional tutorials online.

### Editing files

There are many ways to view and editing text files but ```nano``` is the simplest. Let's test it out on the file that we made earlier
```
nano test.txt
```
Type some text into the file space and then hit ```ctrl + x``` to save and exit the editor. Prompts at the bottom of the editor will help guide you through the saving process.

You can view, but not edit, files using ```less```
```
less -S test.txt
```
Using ```-S``` will keep the information on a single line rather than wrapping at the end of the screen.

There are a few other ways that you can view files. ```head``` or ```tail``` at the start or end of the file can also help you view your document. If you want to view the entire document you can call
``` 
cat test.txt
```
But be careful doign this with larger files as it can take forever to complete this command. If this happens you can use ```ctrl + c``` to interupt the terminal.

### Searching through a file

**grep** is a tool that allows you to search through a file for a specified string. 
```
grep "my search string" file.txt

# have a zipped file?
zgrep "my search string" file.txt.gz

# count the number of lines that contain the search string.
grep -c "my search string" file.txt

# diplay the lines that don't contain the search term.
grep -v "my search string" file.txt
```
### Interactive sessions

To avoid working in the login node, where it might be too busy with everyone on, you move onto a compute node. To do this, you will use the ```salloc``` command. ```-A``` allows you to specify the project you are working wiht so that usage and priority can be properly monitored. ```-t``` specifies how long you wish to have the interactive session open for (format is DAYS-HOURS:MINUTES:SECONDS). This examples specifies the session to use 10GB of memory and 2 cores.
```
salloc -A <project name> -t 0-03:00 --mem=10G --cpus-per-tast=2
```
Once the session has been allocated and is running, you can begin entering commands on the command line using the resources you requested.

When you are done running the session you can enter ```exit``` to leave the interactive session and return to your login node. Calling ```exit``` again will log you out of Mana.

### Modules

Modules are pieces or collections of software that are installed on Mana. There are a lot of programs that are already installed and avalible for us to use. Instead of loading all of the software available each time that you log in, loading individual programs as you need is a lot easier.

Some basic commands for modules:
```
#see a (non-comprehensive) list of available modules
module avail
# search for a specific module and see info on how to load it, here the program bwa
module spider bwa
# load up the bwa module with it's dependcy gcc:
module load gcc/11.2.0 bwa/0.7.17
# See all loaded modules:
module list
# Reset modules to default
module reset
```
