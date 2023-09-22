# Redirection

<img src="./diagrams/redirection1.png" width="80%" />
<img src="./diagrams/redirection2.png" width="80%" />

- Redirection describes the ways we can alter the source of standard input, and the destinations for standard output and standard error.

## Standard Streams

- The 3 standard streams are **communication channels** between a computer program and its environment.
    - Standard Input
    - Standard Output
    - Standard Error

### Standard Output

- Standard output is a place to which a program or command can send information.
- The information could go to a screen to be displayed, to a file, or even to a printer or other devices.

### Standard Input

- Standard input is where a program or command gets its input information from. By default, the shell directs standard input from the keyboard.
- The input information could come from a keyboard, a file, or even from another command.

### Standard Error

- Commands and programs also have a destination to send error messages: standard error.
- By default, the shell directs standard error information to the screen for us to read, but we can change that destination if needed.

## redirecting output

- The redirect output symbol `>` tells the shell to redirect the output of a command to a specific file instead of the screen.
- NOTE: `>` symbol must occur after any options and arguments.
- Syntax: `command > filename`
- `date > output.txt` output date to a file called output.txt
- `echo "moo" > cow.js` redirects the output of echo
- `ls -l > files.txt` saves the output of `ls -l` to a file.