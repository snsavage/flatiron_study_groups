# Command Line Basics


## Moving Around
```bash
$ pwd           # /Users/snsavage
$ cd .          # Change directory.
$ cd ~							# Change directory to home.
$ cd ..							# Up one directory.
$ cd /							# Root directory.
$ cd ~/Development/flatiron		# Change to given directory.
```

`<tab>` to autocomplete.

## Special Characters
* `.` - Current Directory
* `..` - Up One Directory
* `~` - User’s Home Directory
* `*` - Wildcard

## Listing Files
```bash
$ ls 					# List files and directories.
$ ls -a				# Include hidden files and directories.
$ ls -l 				# Lists in long format.
$ ls -lah				# All files and directors.  Human readable.
$ ls -t				# Orders by time last modified. 
```

## Working with Files & Directories

### Creating Files & Directories
```bash
$ touch <filename>			# Create a file.
$ touch README.md
$ touch example/README.md
$ mkdir <directory>			# Create directory.
$ mkdir -p one/two/three		# Create parent directories.
$ open <filename>				# Open with associated application.
```

### Moving & Copying
```bash
$ mv <filename> <directory>/			# Moves file to directory.
$ mv <filename> <directory>/<new filename>	# Moves and changes name.
$ cp <filename> <new filename>		# Copy file.
```

`mv` can also be used to rename files.

### Removing
```bash
$ rm <filename>			# Remove file
$ rm -rf <directory>		# Remove directory and ALL child directoies!
```

## Grep 
Grep stands for “global regular expression print”.

```bash
$ grep <pattern> <file>			# Search for pattern in file.
$ grep -i <pattern> <file>		# Case insensitive.
$ grep -r	<pattern> <file>		# Search recursively.
```

## Readline
* Arrow Up & Down - Move through command history.
* `<Ctrl-a>` - Move to the start of the current line.
* `<Ctrl-e>` - Move to the end of the line.
* `<Alt-f>` - Move forward to the end of the next word.
* `<Alt-b>` - Move back to the start of the current or previous word.
* `<Ctrl-u>` - Kill (cut) backwards to the start of the line.

## Miscellaneous
```bash
$ env					# Print environment.
$ history				# List previous commands (might be OS X specific).
$ ps 					# Displays a list of running processes.
$ sudo <commond> 		# Gives authority for running a command.
$ man <command>		# Manual pages.
$ tree				# List director and file structure.  Must install first.
```

Type `Control-C` to exit most programs.

## Resources
* [List of Command Line Commands | Codecademy](https://www.codecademy.com/articles/command-line-commands)
* [explainshell.com - match command-line arguments to their help text](https://explainshell.com/)
* [Readline Cheat Sheet](http://readline.kablamo.org/emacs.html)
* [Getting to Know the Command Line | David Baumgold](https://www.davidbaumgold.com/tutorials/command-line/)
* [Tree — BrewFormulas](http://brewformulas.org/Tree)
* [Introduction to Linux | edX](https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-1)
