# Getting Help

## `man`

- `man` pages, short for manual pages, are a built-in form of documentation available on nearly al UNIX-like operating systems.
- The specific contents vary from 1 operating system to another, but at a bare minimum the man pages include information on commands and their usage.
- e.g., `man ncal` to view manual for `ncal`
- When in the manual:
    - Hit `f` or spacebar to scroll down 1 page.
    - Hit `b` to scroll up 1 page.
    - Hit `h` to see help.
    - Hit `/` and type whatever you want to search like `-w` and hit enter. It is like a `CTRL + F` in regular searching.


### `man` pages synopsis

- Anything listen inside of square brackets is OPTIONAL.
    - `ncal [-3lbhJeoSM][-A number][-B number][-d yyyy-mm][year]`
- An ellipsis indicates that 1 or more of the proceeding operand are allowed.
    - `echo [OPTION]... [STRING]...`
    - e.g., `echo hello leon how are you`
- Some commands do require certain arguments in order to run.
    - e.g., `cp [OPTION]... SOURCE DEST`
    - `SOURCE` indicates that we must pass 1 source, and `DEST` indicates that we must pass 1 destination. Those 2 arguments are required.

## `type` command

- Tells us the type of the command
- Syntax: `type command`
- 4 types of commands:
    1. An executable program, usually stored in /bin, /usr/bin, or /usr/local/bin. These are compiled binary files (bin).
    2. A built-in shell command. These commands are part of the shell (bash in our case). E,g., `type cd`
    3. A shell function
    4. An alias

## `which` command

- Tell us where a command is located or to find the exact location of an executable
- Syntax: `which command`
    - e.g., `which ncal`

## `help`

- used for commands that are shell built-in commands
- `help cd`

## `whoami`, `who`

- `whoami`: prints out the username
- `who -b`: prints out last reboot time