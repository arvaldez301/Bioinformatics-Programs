# Bioinformatics-INBRE

Here you will learn everything from basic terminal commands to Python and R! Below will be some onboarding tutorials for each of the programs to get you started.

## Onboarding for Terminal (Bash Scripting)

To access Mana you must log into the shell. Password entry is Case sensitive and it may prompt you to complete a DuoPush
```
ssh <username>@uhhpc.its.hawaii.edu
```
Next we want to look at any files that we have stored in our system.
```
ls

ls -ltrh
```
Running ls will show you any files and directrories that you have. You can run ls with addtional code to give more information. l is long form (includes data information, owner permissions, and size). tr is sort by time and in reverse, so the newer files will be on the bottom. h is human readable so that files sizes are in KB, MB, GB.

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

To move around the cluster you use cd followed by a any path. If you enter cd on its own, you will be taken to the home directory.
```
cd /
```
This will tak you to your root directory. At any point you can return to your home directory by using
```
cd ~
```
In your home directory, you can make a new directory and navigate to it using
```
mkdir <name you would like to give it>
cd <name of directory>
```
