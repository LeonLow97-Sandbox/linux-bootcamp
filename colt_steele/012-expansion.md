# Expansion

## Wildcard Characters (aka globbing patterns)

- Can use special wildcard characters to build patterns that can match multiple filenames at once.
- The asterisk `*` character represents zero or more characters in a filename.
    - `ls *.html` matches any files that end with .html like index.html and login.html
    - `cat blue*` matches any files that start with "blue" like blue.html or bluewords.js
    - `ls -l *at*` matches any files that have the characters 'at'

## `?` Wildcard

- The `?` wildcard character represents any **single** character.
- `ls app.??` matches any files named "app" that end with 2 character file extensions like "app.js" or "app.py" but not "app.css"
- `ls pic?.png` matches "pic1.png", "pic2.png", "picA.png" or "picx.png" but not "pic34.png"

## Range Wildcards

- Inside of square brackets `[]`, we can specify a range of characters to match.
- `ls pic[123].png` matches only "pic1.png", "pic2.png", and "pic3.png".
- `ls file[0-9]` matches file0, file1, file2, file3, up to file9.
- `ls [A-F]*` matches any files that begin with a capital A, B, C, D, E or F.
- `echo app[2-4].css`
- `echo [A-H]*[ps]` matches any files that begin with A to H and ends with p or s.

## Negating Ranges

- Inside of square brackets `[]`, we can specify a range of characters to NOT match, using a caret `^`.
- `ls [^a]*` matches any files that do NOT start with 'a'
- `echo [^Cc]*` matches any files that start with 'C' or 'c'.