# Linux Day 2

### Contents

* File Operations
* Package Management
* Directory Navigation
* File & Directory Manipulation


### File Operations

1. `cat chicken-joke.txt`: Display the contents of the "chicken-joke.txt" file.
2. `cat chicken-joke.txt | grep chicken`: Display lines containing the word "chicken" in the "chicken-joke.txt" file.
3. `cat chicken-joke.txt | grep had`: Display lines containing the word "had" in the "chicken-joke.txt" file.
4. `cat chicken-joke.txt | grep a`: Display lines containing the letter "a" in the "chicken-joke.txt" file.

### Package Management

5. `apt install tree`: Install the "tree" package using the apt package manager.
6. `sudo apt install tree`: Install the "tree" package with administrative privileges.
7. `tree`: Display a directory tree structure.
8. `sudo apt update -y`: Update the package lists with administrative privileges.

### Directory Navigation

9. `cd /`: Change the current directory to the root directory.
10. `ls`: List the contents of the current directory.
11. `cd bin`: Change the current directory to the "bin" directory.
12. `cd ..`: Move up one level in the directory structure.
13. `cd home`: Change the current directory to the "home" directory.
14. `cd adminuser`: Change the current directory to the "adminuser" directory. .
18. `cd ~`: Change the current directory to the home directory.

## Shell Scripting

61. `touch provision.sh`: Create a new file named "provision.sh".
62. `tree`: Display a directory tree structure.
63. `ls -l`: List the files in the current directory with detailed information.
64. `nano provision.sh`: Open the "provision.sh" file in the nano text editor.
67. `chmod +x provision.sh`: Add execute permissions to the "provision.sh" file.
69. `chmod o-x`: Remove execute permissions from the "provision.sh" file for other users.
70. `./provision.sh`: Execute the "provision.sh" script.


### Additional Notes

- `cat`: Command used to display the contents of a file.
- `grep`: Command used to search for patterns in files or output.
- `apt`: Package management command used in Debian-based Linux distributions.
- `sudo`: Command used to execute a command with administrative privileges.
- `tree`: Command used to display a directory tree structure.
- `~`: Tilde symbol representing the user's home directory.
- `printenv`: Command used to print the current environment variables.
- `echo $MYNAME`: Command used to print the value of the "MYNAME" environment variable.
- `export MYNAME=HARRY`: Command used to set the value of the "MYNAME" environment variable to "HARRY".
- `.bashrc`: The Bash configuration file located in the user's home directory.
- `source .bashrc`: Command used to reload the Bash configuration file.