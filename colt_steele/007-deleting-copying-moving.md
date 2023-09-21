# Deleting, Copying and Moving

## `rm`

- `rm` command is used to remove files from our machine.
- `rm <filename>`, e.g., `rm app.js`
- `rm <filename1> <filename2>` remove multiple files at once
- `rm ~/<filename>` remove with path
- NOTE: `rm` DELETES FILES, there is no undo or recycling bin to retrieve them from. Gone forever.

## Deleting directories/folders

- `rm -d <foldername>` or `rmdir <foldername>` removing empty folder/directory
- `rm -r <foldername>` removes folders with files or other nested folders/files.
- `rm -ri <foldername>` removes folders with prompt
```
➜  Desktop rm -ri Horses
examine files in directory Horses? y
remove Horses/starbucks.txt? y
remove Horses? y
```

## `mv`

- `mv` to move files and directories from one locatino to another
- `mv <source> <destination>`
- e.g., `mv jiewei.txt starbucks`
- `mv starbucks/jiewei.txt ~/Desktop` moving with paths
- `mv <file1> <file2> <foldername>` moving multiple files at once
- `mv <foldername1> <foldername2>` moving a folder into another folder. Ensure that the destination folder exists otherwise it will rename the source folder instead.
    - `mv <foldername1> <foldername2> <destinationfolder>` can also move multiple folders.
- `mv <foldername> ..` move the current folder to the parent directory.

## Renaming with `mv`

- Using the `mv` command to rename files and folders.
- If we specify a single file as the source and a single file as the destination, it will rename the file.
- NOTE: If we specify a single folder as the source and the destination doesn't yet exist, it will rename the folder. If the destination folder does exist, it will move our source folder into the destination folder.
- `mv <current> <newname>` works with files and directories
- `mv index.js ~/Desktop/linux_test/app.js` rename and moving the file. in this example, renamed index.js to app.js

## Copying with `cp`

- `cp <source> <destination>` create copies of files and folders.
- `cp index.js ~/Desktop` copy with path
- `cp app.js index.js starbucks` copy multiple files into a directory
- `cp -r starbucks/ macdonalds` copying a directory with files into another directory using `-r` flag to specify recursive copying as the source directory could contain nested files/folders.