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
- `grep -o "\$[1-9]" prices.txt` the `-o` option tells grep to print out the matches, rather than the entire line containing each match.

## Regex Crash Course

- Can provide regular expressions to `grep`.
- Regular expressions helps us match complex patterns, but the syntax does differ from what we have seen so far.

|  REGEX   | Description                                |
| :------: | ------------------------------------------ |
|   `.`    | matches any single character               |
|   `^`    | matches the start of a line                |
|   `$`    | matches the end of a line                  |
| `[abc]`  | matches any character in the set           |
| `[^abc]` | matches any character NOT in the set       |
| `[A-Z]`  | matches character in a range               |
|   `*`    | repeat previous expression 0 or more times |
|   `\`    | escape meta-characters                     |

## `grep` with regex

- `grep 'p....' SongOfMyself.txt -w` returns the words that start with 'p' followed by 4 characters
- `grep "^I" SongOfMyself.txt -w -n` returns the words that start with `I` with line number
- `grep ")$" SongOfMyself.txt -c` returns the number of lines that end with `)`
- `grep "2[1-6]" SongOfMyself.txt` or `grep "2[123456]" SongOfMyself.txt` returns the entries that begin with '2' end followed by any digit 1-6.
- `grep "2[^1-6]" SongOfMyself.txt` returns the entries that begin with '2' and does NOT have digits 1-6 that follow.
- `grep "G[aeiou]" SongOfMyself.txt` returns the entries that begin with 'G' followed by 'a','e','i','o' or 'u'

## `grep` with `-E` option (extended regex)

- `grep` with the `-E` option enables extended regular expressions in the search pattern, allowing for more complex pattern matching, including the use of meta-characters like `+`, `?`, `|`, `()` and `{}`.
- It makes `grep` interpret the pattern as an extended regular expression, expanding its capabilities for pattern matching in text files.
- `grep "birds\?" -w SongOfMyself.txt` or `grep "birds?" -wE SongOfMyself.txt` with `-E` option finds 'birds' or 'bird', so the 1 character 's' is optional because of the `?` after 's'.
- `grep "[aeiou]{2}" -E SongOfMyself.txt` returns the words that contain 2 consecutive vowels.
- `grep "[aeiou]{2,4}" -E SongOfMyself.txt` returns the words that contain 2-4 consecutive vowels.

## Piping to `grep`

- Common use case is to use `grep` to filter a large chunk of data.
- `ps aux | grep "sql"` outputs a huge list of all processes with `ps aux`  running on our machine (`ps -aux` on ubuntu). We pipe that data to grep and then filter it down to only the processes that include `sql`
- `man grep | grep "count" -i` passing `man grep` to find the word 'count' with `grep`
- `find ~ -name "*.txt" ! -empty -type f -exec grep -n "purple" '{}' ';'` use the `-l` to show the file location
- `find ~ -name "*.txt" ! -empty -type f -exec grep -n "purple" '{}' ';'` use the `-n` option to give line number
- `grep -rE 'https?://[^[:space:]]+' ~/ -I` to find any matching patterns for url like https://github.com/golang/go/issues/19113