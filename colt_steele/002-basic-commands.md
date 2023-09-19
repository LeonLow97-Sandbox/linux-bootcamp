# Basic Commands

| Commands | Description                       |
| :------: | --------------------------------- |
|  `date`  | Get today's date                  |
|  `cal`   | Current month's Original Calender |
|  `ncal`  | Current month's New calender, can also get the entire year, `ncal 2021`, `ncal july 1969`      |
|`clear`|Clears the terminal|
|`echo <argument>`|prints the argument|

## Arguments

- Passing arguments (values) to commands.
- Syntax: `command argument`

## Options

- Each command typically supports a host of options that we can choose to use when executing the command.
- These options modify the behavior of the command in predefined ways.
- Syntax:
    - `command -option`
    - e.g., `ncal -h` (turn of highlighting of today's date)

### Combining Options

- `ncal -3 -h` (turn of highlighting and shows previous 3 months)
- `ncal -3 -h -j` or `ncal -3 -hj` or `ncal -3hj`

### Long Form Options

- Some options also support equivalent long format options that are **usually full words** and are prefixed with `2 dashes` instead of 1.
- e.g., `date -u` can be written as `date --universal`

### Options with Parameters

- Some options require us to pass in an additional value
- e.g., `ncal -A 1` (display a certain number of months after a specific date) or `ncal -B2` (2 months before)
- e.g., `ncal -A1 -B1`
- Providing arguments
    - `ncal -M -A1 -B1 july 1969`