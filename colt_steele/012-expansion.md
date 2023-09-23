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

## Tilde Expansion

- `~` tilde expansion feature allows you to refer to a user's home directory followed by the username or by default, the current user's home directory.
- `~username` it represents the home directory of the specified user.
    - `~leonlow` refers to the home directory of the user "leonlow".

## Character Classes

- Can also use predefined named character classes.
- `[:alpha:]` alphabetic characters, upper and lower.
- `[:digit:]` digits 0-9
- `[:lower:]` lower case letters
- `[:upper:]` upper case letters
- `[:blank:]` blank characters: space and tab
- `[:punct:]` punctuation characters
- `[:alnum:]` alphanumeric characters (alpha + digit)
- e.g., `echo [[:upper:]]*` matches any file that starts with an uppercase.
- `echo *[[:digit:]]*` any file with a number in the filename

## Brace Expansion

- Brace expansion is used to generate arbitrary strings. It will generate multiple strings based on a pattern.
- We provide a set of strings inside of curly braces `{}`, as well as optional surrounding prefixes and suffixes.
- The specified strings are used to generate all possible combinations with the optional prefixes and suffixes.
- `touch page{1,2,3}.txt` creates 3 text files as shown below
    - `page1.txt page2.txt page3.txt`
- `touch {Mon,Tue,Wed,Thu,Fri}_Planner.txt`
- `touch {Mon,Tue,Wed,Thu,Fri}_{AM,PM}.txt`

## Ranges

- Can provide a numeric range, which will be used to generate a sequence with `..`
- Can provide a 3rd value which defines the interval for the range.
- `mkdir jan{1..31}`
- `echo {2..10..2}` range with a step interval of 2
    - `2 4 6 8 10`
- `mkdir -p {Mon,Tue,Wed,Thu,Fri,Sat,Sun}/{Breakfast,Lunch,Dinner}` creating nested directories with the `-p` option flag.
- `echo {x,y{1..5},z}` nested brace expansion
    - `x y1 y2 y3 y4 y5 z`
- `echo {Mon,Tue{1..10}_{AM,PM},Wed}`
- `touch group-{a..e}.txt`