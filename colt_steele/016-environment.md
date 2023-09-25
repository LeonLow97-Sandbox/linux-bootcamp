# Environment

- The shell maintains a set of information during a shell session, known as **the environment**. It is just a series of key-value pairs that define properties like:
    - home directory
    - working directory
    - name of the shell
    - name of the logged in user

## Environment Variables

- Environment variables are **case sensitive**.
- `printenv` or `env` view the environment variables and their current values
- `printenv | less`
- `printenv | grep USER`

## Parameter Expansion

- If ew write out the name of an environment, variable prefixed with a dollar sign `$`, the shell will replace it with the actual value.
- `echo $USER` retrieve a single value from the environment
- `echo $PWD` retrieve current working directory
- `echo $OLDPWD` retrieve the previous location

## Defining Variables & Export

- To define a variable, use the syntax: `variable=value`
- Built-in variables are uppercase, so it's a common convention to lowercase custom variables to prevent confusion.
- `$me=jiewei`
- `$person="Harry Potter"` use quotes if value has spaces
- `echo $me`
- `export animal=giraffe` **temporarily** stores in the global environment variable in that **current terminal window**.
- `person=jiewei`, can run `export person` after to save the key-value in the environment.

## Aliases

- Can define our own commands using the `alias` keyword.
- `alias ll='ls -al'` defining an alias called `ll` which is equivalent to running `ls -al`. To execute it, run `ll`.
- Can define aliases in `.bashrc` or `.bash_aliases` file in home directory `~`. These alias only last for the single shell session
    - To start up the alias, run `source ~/.bashrc`

## Startup Files

- When we log in, the shell reads information from startup files.
- First, the shell reads from global config files that effect the environment for all users.
- Then, the shell reads startup files for specific user.
- The specific files the shell reads from depends on the type of session: login vs non-login shell sessions.
- For **login** sessions:
    - `/etc/profile`: global config for all users
    - `~/.bash_profile`: user's personal config file
    - `~/.bash_login`: read if bash_profile isn't found
    - `~/.profile`: used of previous two aren't found
- For **non-login** sessions (typical session when you launch the terminal via the GUI):
    - `etc/bashrc`: global config for all users
    - `~./bashrc`: specific settings for each user. This is where we can define our own settings and configuration.