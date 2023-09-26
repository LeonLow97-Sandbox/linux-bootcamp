# Custom Commands

- Basic Steps:
    1. Write a script in a file and save it
    2. Make the script executable using `chmod`
    3. Verify that the shell can find your script

## Shebang
- The first line of our script should read `#!/bin/bash`
    - `#!` is called the shebang, and it is used to tell the OS which interpreter it should use when parsing this file. like "use bash to interpret this file"
- After the shebang, we need to include the path to the Bash binary `/bin/bash`. This is not Bash specific. If we wanted to write a python script, we would include the path to the python binary.
- Can add comments using `#`
- **Python Shebang**
    1. Run `which python` to find the location of Python interpreter currently in your system's PATH.
    2. Copy that path and paste in the executable file (e.g. pyhi) as `#!/usr/bin/python3` (from step 1)
    3. Start writing python scripts in pyhi file and run `pyhi`
    4. If you see any permission denied issue, the `x` executable permission is probably not enabled.
        - `chmod +x pyhi` or `chmod u+x pyhi` for just the user

```bash
#!/bin/bash
#this is a comment
echo "hello world"
```

## Executing the script

- `bash ~/scripts/hello` this is executing the script in the long way by running `bash pathToFile`. not convenient and will be better if we can run the script anywhere on our machine.

## Running bash from anywhere on our machine

- When we run a command like `pwd`, the shell starts looking for the executable pwd program in the list of directories stored in the `PATH` variable.
- It starts looking in the first location and then keeps looking if it doesn't find it.
    - The `:` in the list of directories is the separator.

```zsh
➜  ~ echo $PATH
/Users/leonlow/bin:/Library/Frameworks/Python.framework/Versions/3.10/bin:/opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/usr/local/go/bin:/usr/local/share/dotnet:~/.dotnet/tools:/Applications/Postgres.app/Contents/Versions/latest/bi
```

- If we want the shell to find our own programs, we need ot make sure we put them in a folder that is in the `PATH` variable.
- A common place to pur user-defined programs is in a bin folder location in the user's home directory. E.g., `/Users/leonlow/bin` but first create it with `mkdir` and transfer any executable files inside that `bin` folder.
- If that directory is not part of your path, can add it by putting `PATH="$HOME/bin:$PATH"` in the .bashrc file. If don't have `.bashrc` file, just run `PATH="$HOME/bin:$PATH"` in terminal and after that ensure the path to bin is set by using `echo $PATH`.
- The next step is to make the file containing our script in the `bin` folder executable.
    - `chmod a+x filename` or `chmod +x filename` will grant executable permissions to everyone.

## Weather Program

```bash
#!/bin/bash

case $1 in
-h | --help)
        echo "WELCOME TO WEATHER HELP"
        echo "-3 for next 3 days of weather"
        ;;
-3)
        curl "wttr.in"
        ;;
-l | --location)
        curl "wttr.in/$2"
        ;;
*)
        curl "wttr.in?m1"
        ;;
esac
```