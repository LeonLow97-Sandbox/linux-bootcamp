# Creating Files and Folders

## `touch`

- To create a new file from the command line.
- `touch <filename>`
- `touch ../<filename>` can also create a file to parent directory.
- `touch ~/<filename>`
- `touch <filename1> <filename2>` can make multiple files at once.
- `touch "my website"` create filename with space (not recommended)
- `\` escape character in shell

## `file`

- The `file` command can be used to determine the file type.
- `file <filename.extension>`
- `file <filename>` it also works if there is no file extension, or if the file extension is wrong. it will derive the file type from the body of the document.

## `mkdir`

- `mkdir`: To create new directories.
- `mkdir <foldername>`
- `mkdir ../<foldername>`
- `mkdir -p folder1/folder2/folder3` making nested folders