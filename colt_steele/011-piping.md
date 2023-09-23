## Piping

<img src="./diagrams/piping.png" width="80%" />

- Purpose of piping: Combining multiple commands to build a pipeline.
- Pipes are used to redirect a stream from one program to another program. We can take the output of one command and redirect it to the input of another.
- The pipe character `|` separates 2 commands. The output of the first command will be passed to the standard input of the second command.
    - Syntax: `command1 | command2`
- `rev` and `cat` and `less` accepts input via stdin
    - `date | rev`
    - `date | cat`
    - `ls -l /usr/bin | less`
- `ls /usr/bin | wc -l` counting the number of lines where `wc -l` accepts a stdin

## `>` vs `|`

- Both the `>` character and the `|` character are used to **redirect output**. They do it in different ways.
- `>` connects a command to some file.
- `|` connects a command to another command
- Using `>` and `|` together
    - `ls -a /usr/bin | wc -l > count.txt`

## `tr`

- `tr` command is used to translate or delete characters from a text stream, allowing for character-level transformations like replacing 1 character with another or removing specific characters.
- `cat msg | tr s S` replace all lowercase s with uppercase S
- `cat msg | tr a-z A-Z` replace all lowercase with uppercase
- `cat msg | tr -d s` delete all character 's'
- `cat data.txt | tr -d a-z` delete all lowercase alphabets
- `cat data.txt | tr -d [:alpha:]` delete all alphabets
- `cat data.txt | tr -d [:blank:]` remove all whitespaces
- `cat data.txt | tr -d :` remove colon
- `cat data.txt | tr -d [:alpha:] | tr -d : | tr -d [:blank:] > phones.txt` piping followed by saving output to a file

## Working with multiple pipes

- `cat file | head -7 | tail - 5`
- `ls -l /usr/bin | sort -k5hr | head -3 > largefiles.txt` finding the top 3 largest file sizes in `/usr/bin`
- `du -ha /usr/bin | sort -h | tail -3` sorting then finding the bottom 3 entries

## `tee` command

- `tee` command reads standard input and copies it both to standard output and to a file. This allows us to capture information part of the way through a pipeline, without interrupting the flow.
- `cat file1 file2 file3 | tee combo.txt | wc -w`
- `du -ha /usr/bin | sort -h | tee sizes | tail -3 | head -3`
- `ls -l /usr/bin | tee allfiles.txt | less`

## Assignment

- `ls PokeDex | wc -l` counting the number of files in that directory.
- `ls PokeDex | tr A-Z a-z | sort -n > all-pokemon.txt` convert all uppercase character to lowercase and then sort numerically.
- `cat all-pokemon.txt | head -18 | tail -3` printing lines 16 - 18
- `head -151 all-pokemon.txt | tr -d 0-9 | sort > original-151.txt` output the first 151 lines in all-pokemon.txt, remove all digits 0-9 using `tr`, sort the list alphabetically