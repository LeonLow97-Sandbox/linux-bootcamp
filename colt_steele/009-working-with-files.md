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

## `head` command

- `head` prints a portion of a file, starting from the beginning of the file. By default, it prints the first 10 lines of a file.
- `head <filename>`
- `head -n <noOfLines> <filename>` can also specify a number of lines for head to print using the `-n` option (or `--lines`) followed by an integer.
  - e.g., `head -n 21 index.html`
  - Shorter syntax: `head -21 index.html`
- `head -c 8 filename.txt` provide a number of bytes to print out, rather than lines using the `-c` option.

## `tail` command

- `tail` command works similarly to the head command, except it prints from the END of a file. By default, it prints the last 10 lines of a file.
- `tail <filename>`
- `tail -n <noOfLine> <filename>`
- `tail -c <noOfBytes> <filename>`
- `tail -f <filename>` displays the contents of a file in real-time as new lines are added to it. Useful for monitoring log files or any other type of file where you want to see updates as they occur.

## `wc` command

- The word count command can tell us the number of words, lines or bytes in files.
- `wc index.txt` 3 numbers - the lines, words, and bytes in a file.
- `wc -l students.txt`
  - use `-l` number of lines
  - use `-w` number of words
  - use `-c` number of bytes
  - use `-m` number of characters

## `sort` command

- The `sort` command outputs the sorted contents of a file (it does not change the file itself). By default, it will sort the lines of a file alphabetically.
- `sort filename.txt`
- `sort -r filename.txt` sort in reverse
- `sort -n filename.txt` sort numerically (asc)
- `sort -nr filename.txt` sort numerically (desc)
- `sort -u filename.txt` sort and return unique values.

## `sort` advance command

- Can specify a particular "column" that we want to sort by, using the `-k` option followed by a field number.
- In the example below, `sort data.txt -nk 2` tells sort to use the numeric sort and to sort using the 2nd field.

```zsh
➜  linux_test cat prices.txt
racecar 49.00
chocolate 19.99
pencil 0.50
house 199.99
pizza 5.00
fish 13
➜  linux_test sort -n -k2 prices.txt
pencil 0.50
pizza 5.00
fish 13
chocolate 19.99
racecar 49.00
house 199.99
➜  linux_test sort -n -k2 -r prices.txt
house 199.99
racecar 49.00
chocolate 19.99
fish 13
pizza 5.00
pencil 0.50
```
