# Grep

- The `grep` command searches for patterns in each file's contents.
- `grep` will print each line that matches a pattern we provide.
- For example, `grep "chicken" animals.txt` will print each line from the animals.txt file that contains the pattern "chicken".

## `grep` command

- `grep "technology" technology_essay.txt`
- `grep -i "The" technology_essay.txt` use the `-i` option to make the search case insensitive
- `grep -iw "The" technology_essay.txt` use the `-w` option to ensure that grep only matches the exact word, rather than fragments located inside of other words.

## Recursive search

- Use the `-r` option to perform a recursive search which will include all files under a directory, subdirectories and their files, and so on.
- If we don't specify a starting directory, `grep` will search the current working directory.
- `grep -r "transactions"`
- `grep -r "beneficiaries" ~/Projects` provided a path to run recursive `grep` from.
- `grep -r "parm[ae]san" MealDiary/` find either 'parmasan' or 'parmesan' with recursive `grep`

## `grep` options

- `grep "myself" -c -i SongOfMyself.txt` use the `-c` option to count the number of 'myself' words in the file
- `grep "grass" SongOfMyself.txt -iB1` shows the line before the `grep` result with `-B1` flag to indicate one line before
    - `-A2` to indicate showing 2 lines after
    - `-B10` to indicate showing 10 lines before
    - `-C1` to indicate showing 1 line before AND after
- `grep "6" SongOfMyself.txt -wn` to show the line number with `-n` option flag
- `grep "wagon" SongOfMyself.txt -m2` use the `-m` flag followed by a number to indicate the number of search results that are returned from `grep`.