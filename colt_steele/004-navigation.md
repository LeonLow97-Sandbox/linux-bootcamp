# Navigation

## Root directory

- **root directory (folder)** is the starting point for the file system. 
- we call it the root, but its actual directory name is "/"
- `cd /`
- `open /` to open the folder.

## Home directory

- `/home` contains a home folder for each user on the system.
- `cd ~` to go to the current logged in user's working directory
- `open ~`

## `pwd`

- `pwd` print working directory command ("where am i"), will print the path of your current working directory, starting from the root.

## `ls`

- `ls`: list the contents of your current working directory.
- `ls /Users/leonlow`: list the contents in the specific directory.

#### `ls` options

- `ls -l` returns long format of the contents
- `ls -a` returns all files, including hidden files which begin with a `.` like `.git`
- `ls -la`
- `ls -lah` for more readable file size

## `cd`

- `cd` is used to change the current working directory, moving into another directory.
- `cd <directory>`
    - `cd /Users/leonlow`
- `.` represents the current directory
- `cd ..` to return to the parent directory

## Relative Paths

- Relative paths are paths that specify a directory/file relative to the current directory.

## Absolute Paths

- Absolute paths are paths that start from the root directory (they start with a `/`).
- `cd /Users/leonlow/desktop/Music`