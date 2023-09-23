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