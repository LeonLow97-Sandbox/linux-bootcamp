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

## Moving Directories