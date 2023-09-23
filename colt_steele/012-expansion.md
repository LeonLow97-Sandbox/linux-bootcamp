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

## Arithmetic Expansion

- The shell will perform arithmetic via expansion using the `$((expression))` syntax. Inside the parentheses, we can write arithmetic expressions using:
    - `+` addition
    - `-` subtraction
    - `*` multiplication
    - `/` division
    - `**` exponential
    - `%` modulo (remainder operator)
- `echo $((10/3))` returns 3
- `echo $((3**3-2))` returns 25

## Command Substitution

- Can use the `$(command)` syntax to display the **output of another command**.
- `echo "today is $(date)"`
- `echo today is $(date)`
- echo today is `date` also works with backticks around commands.
- `touch todos-$(date +"%m-%d-%y").txt` making a file with current date in the format month-day-year

## Quoting

- `echo look at         me` our large whitespace is ignored because the shell performs something called work splitting.
- `echo holy $cow` we only see "holy" printed out because the shell thinks we are referencing a variable called cow. It can't find a value for cow, so it substitutes an empty string instead.

```zsh
➜  Desktop echo look at           me
look at me
➜  Desktop echo holy $cow
holy
```

## Double Quotes

- If we wrap text in double quotes, the shell will respect our spacing and will ignore special characters. But it will not ignore dollar sign `$`, backslash `\` and backtick `.
    - `echo "look at       me"` --> output: look at       me

- Pathname expansion, brace expansion and word splitting will be ignored. However, command substitution and arithmetic expansion is still performed because dollar signs still have meaning inside double quotes.
    - `echo "{1..9}"` --> output: {1..9}

## Single Quotes

- Use single quotes to suppress all forms of substitution.
- `echo "$((2+2)) is 4"` --> output: 4 is 4
- `echo '$((2+2))' is 4` --> output: $((2+2)) is 4

## Escaping

- To selectively prevent expansion or substitution for specific characters, we can prefix them with a single backslash.
- We can use this to reference special characters that normally have meanings inside of filenames.
- `echo "$5.00"` --> output: .00
- `echo "\$5.00"` --> output: $5.00 (or just do `echo '$5.00'`)

## Assignment

- [Link](https://plum-poppy-0ea.notion.site/Expansion-Exercise-added25bbf314060a226a81c09921892)
- Commands Used:

```zsh
touch {morning,afternoon}-day-{1..30}
touch todos-$(date +"%m-%d-%y").txt
ls *9
ls *1?
ls afternoon*7
mv morning* Mornings
mkdir -p Year/{Winter,Spring,Summer,Fall}/{Yard,House}
touch {Winter,Spring,Summer,Fall}/{Yard,House}/{todos,done}.txt
```