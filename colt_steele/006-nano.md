# Nano

- Nano is a simple text editor that we can access right from the terminal.
- Far more accessible than other popular command-line editors like vim and emacs.
- Nano includes all the basic text editing functionality you would expect: search, spellcheck, syntax highlighting, etc.

## Nano Commands

- `nano <filename>` open file using nano
- `CTRL O` (Write Out) + `ENTER` to write and save file
- `CTRL X` to exit nano
- `nano <filename_inexistant>` can create and open file that does not exist

## Searching

- Use `CTRL + W` and then enter a search phrase to search FORWARD in the file from your current cursor location.

## Replace 

- Use `CTRL + \` key. When pressed, it will ask for the text that you want to search for, so type the text in and then press the `ENTER` key. After that, enter the text that you want to replace it with.

## Spell check

- Can use spellchecking inside of Nano, but we have to enable it first in the Nano config file located at `/etc/nanorc`. (not available in macOS).