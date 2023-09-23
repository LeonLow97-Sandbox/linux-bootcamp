# Finding Things

- Finding files on our machine.

## `locate` command

- Have to install in ubuntu but it comes preinstalled in mac.
- `sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist`
- update locate db
    - `sudo /usr/libexec/locate.updatedb`
    - a cron job is ran daily to update the locate db.
- The `locate` command performs a search of pathnames across our machine that match a given substring and then prints out any matching names.
- `locate` command is fast because it uses a pre-generated database file rather than searching the entire machine.
- For example, `locate chick` will perform a search for all files that contain chick in their name.
    ```
    ❯locate chick
    /home/colt/chicken.txt
    /home/colt/demo/chick123
    /home/colt/chickenNuggets
    /home/chickachickaboomboom
    ```

## `locate` options

- The `-e` option will only print entries that actually exist at the time locate is ran.
- The `-i` option tells locate to ignore casing. (`locate -i`)
- The `-l` or `--limit` option will limit the number of entries that locate retrieves
    - e.g., `locate -l3` retrieve 3 entries

## `find` command

- The `find` command is more powerful. Unlike `locate`, `find` does not use a database file.
- By default, `find` on its own will list every single file and directory nested in our current working directory.
- Run `find` on ubuntu and `find .` on mac to see all the files in the current working directory.
- `find . | wc -l` count the number of files
- `find golang-api/` provide a specific folder and print all the files and directories inside the `golang-api` directory (including nested folders).

## `find` by type

- Can tell `find` to only find by file type: only print files, directories, symbolic link, etc using the `-type` option.
- `find -type f` on ubuntu and `find . -type f` on mac to limit the search to files.
- `find -type d` on ubuntu and `find . -type d` on mac to limit the search to directories.

## `find` by name

- Can provide a specific pattern for `find` to use when matching filenames and directories with the `-name` option Need to close our pattern in quotes.
- To find all files in our Desktop that end in the .txt extension, run `find ~/Desktop -name "*.txt"`
- Use the `-iname` option for a case insensitive search
    - `find ~/Desktop -iname "*.txt"`

## Counting results with `find`

- Can pipe the output of `find` to other commands like word count.
- Use the `-l` option to count the number of lines (each result from the find is its own line).
- `find -name "*.html" | wc -l`
- `find -iname "*.html" | wc -l` for case insensitive search

## `find` by size

- Can use the `-size` option to find files of a specific size.
- `find -size +1G` find all files larger than 1 gigabyte
- `find -size -50M` find all files under 50 megabytes
- `find -size 20k` find all files that are exactly 20 kilobytes

## `find` by owner

- Use the `-user` option to match files and directories that belong to a particular user.
- `find -user leonlow` username leonlow

## `Timestamps`

- `mtime` or modification time, is when a file was last modified AKA when its contents last changed.
    - `ls -l`. doesn't include renaming file
- `ctime` or change time, is when a file was last changed. This occurs anytime `mtime` changes but also when we rename a file, move it, or alter permissions.
    - `ls -lc`.
- `atime`, or access time, is updated when a file is read by an application or a command like `cat`.
    - `ls -lu` (doesn't work for mac unfortunately).

## creating files with different timestamp creation

- [bash] `touch last_week -d "1 week ago"`
- [zsh] `touch -t MMDDhhmm <filename>` where
    - MM = month from 01-12
    - DD = day from 01-31
    - hh = hour from 00-23
    - mm = minute from 00-59
- [zsh] `touch -t YYYYMMDDhhmm.ss last_month`
    - YYYY = 4 digit year
    - ss = seconds from 00-59
- `zsh` commands
    - `touch -t $(date -v -1w "+%Y%m%d%H%M.%S") last_week` for 1 week ago
    - `-1w` (1 week ago)
    - `-1m` (1 month ago)
    - `-1y` (1 year ago)
    - `-1H` (1 hour ago)
    - `-1M` (1 minute ago)
    - `-1S` (1 second ago)

## `find` by time

- [bash] `find -mmin +30`
- [zsh] `find . -mmin +30` finding files that were modified more than 30 minutes ago
- `find . -amin +30`
- `find . -cmin -1`
- `find . -mtime -5` files modified less than five 24-hour periods
- `find . -mtime +10` files modified more than ten 24-hour periods

## Logical Operators

- Can also use the `-and`, `-or` and `-not` operators to create more complex queries.
- `-and` is usually not used because it is implied in commands.
- [bash]
    - `find -name "*chick*" -or -name "*kitty*"`
    - `find -type f -not -name "*.html"`
    - `find -cmin -60 -not -name "*.log"`
- [zsh]
    - `find . -name "*chick*" -or -name "*kitty*"`
    - `find . -type f -not -name "*.html"` find files that do not have the extension .html
    - `find . -cmin -60 -not -name "*.log"` find files that have been modified within the last 60 minutes and do not have ".log" file extension. Helps to identify recently modified files that are not log files within the specified time frame.
    - Can also use `!` instead of `-not`