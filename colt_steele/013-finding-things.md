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