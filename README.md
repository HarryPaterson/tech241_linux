<h1 style="text-align: center;">Linux</h1>

### Contents
* Linux and important commands
* Managing file ownership
* Managing file permissions
* Manging file permissions using numeric value
* Changing file permissions

### Linux and important commands
Linux is an open-source operating system that offers a command-line interface for interacting with the system. Here are some commonly used commands:

#### File and Directory Operations
* ls: List files and directories.
* cd: Change directory.
* pwd: Print working directory.
* mkdir: Create a new directory.
* rm: Remove files and directories.
* cp: Copy files and directories.
* mv: Move or rename files and directories.
#### File Manipulation
* cat: Display file content.
* head: Show the beginning lines of a file.
* tail: Display the end lines of a file.
* less: View file content interactively.
* touch: Create an empty file or update file timestamps.
##### File Permissions
* chmod: Change file permissions.
* chown: Change file ownership.
* chgrp: Change group ownership.

### Managing file ownership

Managing file ownership is important for several reasons:

Security: File ownership allows for fine-grained control over who can access and modify the file. By assigning ownership to specific users or groups, you can restrict or grant permissions accordingly, ensuring that sensitive files are only accessible to authorized individuals.

Accountability: File ownership helps track changes and identify the responsible party. When a file is owned by a specific user or group, it becomes easier to determine who made modifications or is responsible for the file's contents.

Collaboration: Ownership facilitates collaboration among users. By assigning ownership to a shared group, multiple users can work on a file or directory, allowing them to collaborate effectively while still maintaining control over access and permissions.

The command to view file ownership is ls -l. It displays detailed information about files and directories, including the owner and group ownership.

When a user creates a file or directory, it typically belongs to the user who created it. The ownership is set based on the default user and group assigned to the creating process. This helps maintain control and privacy over the user's own files.

By default, the owner does not receive execute (X) permissions when creating a file to prevent accidentally executing files that are not intended to be executed. This provides an additional layer of security and prevents potential security vulnerabilities.

The command to change the owner of a file or directory is chown. For example, chown newowner myfile.txt changes the owner of myfile.txt to newowner. The command can also be used with the -R option to recursively change ownership for all files and directories within a directory.

### Managing file permissions

Being the owner of a file does not necessarily mean you have full permissions on that file. The permissions on a file are independent of ownership. The owner can have specific permissions assigned to them, just like the group and other entities.

When you give permissions to the User entity, it means that the owner of the file has those permissions. For example, if you give read-only permissions to the User entity, the owner can read the file but cannot modify or execute it.

When you give permissions to the Group entity, it means that members of the group (to which the file belongs) have those permissions. For instance, if you give read and write permissions to the Group entity, any user who is part of that group can read and modify the file.

When you give permissions to the Other entity, it means that users who are neither the owner nor in the group associated with the file have those permissions. For example, if you give read, write, and execute permissions to the Other entity, any other user on the system can read, modify, and execute the file.

In the given scenario where the user is the owner of the file and the permissions are set to User: read-only, Group: read and write, Other: read, write, and execute, the user will have read-only permissions on the file. They can view the contents of the file but cannot modify it or execute it.

Analyzing the line rwxr-xr-- 1 tcboony staff 123 Nov 25 18:36 keeprunning.sh from the ls -l command:

-: The first character indicates the file type. In this case, it is a regular file.
rwxr-xr--: The next nine characters represent the file permissions. The first three characters (rwx) represent the permissions for the owner (tcboony), the middle three characters (r-x) represent the permissions for the group (staff), and the last three characters (r--) represent the permissions for others.
1: Indicates the number of hard links to the file.
tcboony: The owner of the file.
staff: The group associated with the file.
123: The file size in bytes.
Nov 25 18:36: The date and time of the last modification.
keeprunning.sh: The file name.
From the permissions section, the owner (tcboony) has read, write, and execute permissions (rwx). The group (staff) has read and execute permissions (r-x), and others have read-only permissions (r--).
### Managing file permissions with numeric value


In Linux, numeric values are assigned to each permission as follows:

Read permission is represented by the value 4.
Write permission is represented by the value 2.
Execute permission is represented by the value 1.
When assigning numeric values to permissions:

Read + write permissions are represented by the value 6 (4 + 2).
Read, write, and execute permissions are represented by the value 7 (4 + 2 + 1).
Read and execute permissions are represented by the value 5 (4 + 1).
The three-digit numeric values used to represent file or directory permissions in Linux follow a specific pattern:

The first digit represents the owner's permissions.
The second digit represents the group's permissions.
The third digit represents others' (or world's) permissions.
For example, the numeric value 644 represents the following permissions:

The owner has read and write permissions (6).
The group has read-only permissions (4).
Others (world) have read-only permissions (4).

### Changing file permissions
The chmod command is used to change file permissions in Linux.

To change permissions on a file, the end user must be the owner of the file or have superuser (root) privileges.

Examples of different ways to set permissions on a new file (testfile.txt):

Set User to read, Group to read + write + execute, and Other to read and write only:

Symbolic notation: chmod u=r, g=rwx, o=rw testfile.txt
Numeric notation: chmod 764 testfile.txt
Add execute permissions (to all entities):

Symbolic notation: chmod +x testfile.txt
Numeric notation: chmod a+x testfile.txt
Take write permissions away from Group:

Symbolic notation: chmod g-w testfile.txt
Numeric notation: chmod g-wx testfile.txt
Use numeric values to give read + write access to User, read access to Group, and no access to Other:

Numeric notation: chmod 640 testfile.txt
Note: The u represents User, g represents Group, o represents Other, and a represents all (User, Group, and Other) in symbolic notation. The permissions are represented by r for read, w for write, and x for execute. The numeric notation follows the format: owner permissions, group permissions, other permissions, where each permission is assigned a numeric value (read = 4, write = 2, execute = 1), and the values are summed up to represent the permissions.


