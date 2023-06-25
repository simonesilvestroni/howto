# Environment variables

Environmental variables are defined for the current shell and become inherited by any running command or process. They can determine anything from the default shell, the `PATH`, the users home directory, to the terminal emulation type, current working directory, where a history file is located, language and localization settings, and going further to include shell variables, which include everything from customizations to the bash prompt, colorized ls output, and changes to terminal appearance, to aliases, and much more. 

## Displaying Current Environment & Shell Variables in bash on macOS

To quickly **get a list of environmental variables**, you can use the following command with bash:

```bash
printenv
```

To list environmental variables in zsh, use the following command:

```bash
env
```

Or optionally:

```bash
echo $ENV_VAR
```

If you want to see a **complete list of shell variables**, the `set` command can be issued as well:

```bash
set
```

The output of these commands can be lengthy so you may wish to pipe the output through the less or more commands.

## Setting Environmental Variables in Mac OS X Command Line with bash

Because the Mac defaults to using bash shell, you can set environmental variables in the user directories `.bash_profile`, for an active user account the path to that file is locate at:

```bash
~/.bash_profile
```

If you changed your shell or you aren’t sure what shell you’re using, you can always check by issuing the `echo $SHELL` command, which will display which shell is in use. We’re going to assume you’re still using the OS X default bash shell, thus we’ll add new environment variables by modifying .bash\_profile with nano – you can use vi, emacs, or another text editor if you’d like, but we’ll cover nano for it’s simplicity.

Start by opening `.bash_profile` within the nano text editor:

```bash
nano .bash_profile
```

You can add environmental variables and shell variables onto new lines, if there is already data within the `.bash_profile `file, just be sure to add new variables to a new blank line by using the arrow keys and the return key as necessary.

Let’s take an example and say we’re going to set the `JAVA_HOME` and `JRE_HOME` environmental variables within `.bash_profile` by adding the following to new lines of the file:

```bash
export JAVA_HOME=$(/usr/libexec/java_home)
export JRE_HOME=$(/usr/libexec/java_home)
```

Assuming we’re now finished, save changes made to `.bash_profile` by hitting <kbd>CTRL + O</kbd> (that’s an o as in otter), then exit out of nano by hitting <kbd>CTRL + X</kbd>.

Changes and additions made to environmental variables will require the shell to be restarted or a new shell to spawn.

## Setting Temporary Environmental Variables in OS X

It’s worth mentioning that you can also set temporary environmental variables in bash by using the ‘export’ command by itself, though these will only persist for as long as the current bash shell remains active. For example, if you wanted to add a temporary path to `~/bin/` you could use the following command:

```bash
export PATH=$PATH:~/bin
```

Again, the `export` command run by itself and not contained within `.bash_profile` will only be a temporary setting and the environmental variable will not persist unless you add it to the `.bash_profile`.

If you’re actually looking to add a new `PATH` for usage, you should almost certainly add it to `.bash_profile` by placing the appropriate export command into the file.

Going beyond bash shell, if you changed your Terminal app default shell away from bash to tcsh, zsh, sh, ksh, fish, or any of the other alternate shells out there, you’ll simply need to modify the appropriate profile or `rc` file for that specific shell (`.tschrc`, .`cshrc`, `.profile`, etc).

---

#macOS #Bash #CommandLine