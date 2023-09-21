# Shortcuts and History

## Shortcuts

- `CTRL + L` same as `clear`
- `CTRL + A` move to start of line
- `CTRL + E` move to end of line
- `CTRL + B` move left
- `CTRL + F` move right
- `OPTION + B` move left by 1 word (use `ALT` for Windows)
- `OPTION + F` move right by 1 word
- `CTRL + T` swaps the current character with the one before.
- `OPTION + T` swaps the current word with the one before.
- `CTRL + K` kill from current cursor location until the end of the line.
- `CTRL + U` kill from current cursor location until the beginning of the line.
- `CTRL + D` kill the current character of the cursor
- `OPTION + D` kill the text from the current cursor location through tht end of the work
- `CTRL + W` to kill the text from the current cursor through the beginning of the word.

### Reviving Text (Yanking)

- When we kill text using commands like `CTRL + K`, `CTRL + U`, the killed text is stored in a memory area known as the kill-ring.
- `CTRL + Y` to retrieve the most recently killed text.

## History

- Bash keeps a record of the commands we have previously entered.
    - Can see the actual file at ~/.bash_history
    - `nano ~/.bash_history`
- `history` shows history of commands
- `history | less` pipe the output to less
- `history !<line_number>` to find the command in `history` by specifying the line number in `history`.
- `history -c` to clear entire history but don't really need.

### Searching History

- To find an earlier command by searching using a small portion of the command that you remember.
- `CTRL + R` to enter 'reverse-i-search'. As you start typing, bash will search the history and show you the best match. Hit `CTRL + R` again to cycle through potential matches.

### Check limit in .bash_history file

- echo $HISTFILESIZE
- echo $HISTSIZE