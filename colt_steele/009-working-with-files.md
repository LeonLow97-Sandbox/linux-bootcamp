# Working with Files

## `cat` command

- The `cat` command concatenates and prints the contents of files.
- `cat <filename>` reads the contents of a file and print them out.
    - e.g., `cat index.html`
- `cat <file1> <file2>` can concatenate and print out contents of multiple files.

## `less` command

- The `less` command displays the contents of a file, one page at a time. We can navigate forwards and backwards through the file, which is especially useful with very large files.
- `less <filename>`
- When viewing a file using `less`
    - press `space` or `f` to go to the next page of the file.
    - press `b` to go back to the previous page.
    - press `Enter` or `Down arrow` to scroll by 1 line.
    - to search, type forward `/` followed by a pattern
    - press `q` to quit

## `tac` command

- `tac` (cat spelled backwards) will concatenate and print files in reverse. It prints each line of a file, starting with the last line. Can think of it as printing in reverse "vertically".
- `tac <filename>`
- For Mac, use `tail -r <filename>`

## `rev` command

- `rev` prints the contents of a file, reversing the order of each line. Think of it as a "horizontal" reverse.
- `rev <filename>`