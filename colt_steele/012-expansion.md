# Expansion

## Wildcard Characters (aka globbing patterns)

- Can use special wildcard characters to build patterns that can match multiple filenames at once.
- The asterisk `*` character represents zero or more characters in a filename.
    - `ls *.html` matches any files that end with .html like index.html and login.html
    - `cat blue*` matches any files that start with "blue" like blue.html or bluewords.js
    - `ls -l *at*` matches any files that have the characters at