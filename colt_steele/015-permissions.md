# Permissions

## Multiple Users

- Unix and unix-like systems are **multiuser** operating systems.
- More than 1 person can be using the same computer at the same time (though this is tough logistically with only 1 display and keyboard).
- Way back when computers were expensive, a university might only have 1 computer, but dozens of terminals sprinkled across campus.

## Permission Denied

- As regular users, we do not have permission to write or even read ever file on the machine.
- E.g., try to read the file `/etc/sudoers` with the command `cat /etc/sudoers` and you will get the "permission denied" message

## Groups

- On unix systems, a single user may be the owner of files and directories, meaning that they have control over their access.
- Additionally, users can belong to groups which are given access to particular files and folders by their owners.

## User & Group IDs

- When a new user account is made, it is assigned a user ID. The user is also assigned a group ID.
- We can use the `id` command to view user and group ids.
- User IDs are stored in `/etc/passwd`, and the group IDs are in `/etc/group`.

## File Attributes

- When you type `ls -l`, you might see 10 characters at the start like `drwxr-xr-x` or `-rw-r--r--`. These are the **file attributes**.
- These characters tell us the type of the file, the read, write, and execute permissions for the file's owner, the file's group owner and everyone else.
- **First character** indicates the **type of the file**.
  - `-`: regular file
  - `d`: directory
  - `c`: character special file (try `ls -l /dev`)
  - `l`: symbolic link (try `ls -l /dev`), made using `ln -s <filename> <newfile>`

<img src="./diagrams/permissions1.png" width="80%" />

## Permissions

| Character | Effect on Files                                                                           | Effect on Directories                                                                                                          | \   |
| :-------: | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ | --- |
|    `r`    | file can be read                                                                          | directory's contents can be listed                                                                                             |
|    `w`    | file can be modified                                                                      | directory's contents can be modified (create new files, rename files/folders) but only is the executable attribute is also set |
|    `x`    | file can be treated as a program to be executed                                           | allows a directory to be entered or `cd` into                                                                                  |
|    `-`    | file cannot be read, modified, or executed depending on the location of the `-` character | directory contents cannot be shown, modified or `cd` into depending on the location of the `-` character                       |
