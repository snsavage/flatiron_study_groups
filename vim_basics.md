# Vim Basics
#flatiron school/teaching assistant#

# Vim Basics
- - - -

# What is Vim?
* A “modal” text editor.
* The mode determine the behavior of the keys.
* Moving an editing text can be done without using the mouse.
* You can keep your hands on the “home” row.

- - - -

# Warning!!!
## You may not want to learn Vim.

- - - -

# Vim Modes
* Normal Mode
* Insert Mode
* Visual
* Command Line

- - - -

# Opening Vim
```bash
$ vim
$ vim <filename>
$ vim .
```

- - - -

# Start Vim without `.vimrc`
```bash
$ vim -u NONE -N
```

- - - -

# Vim Tutor
30 Minute Interactive Vim Tutorial

```bash
$ vim tutor
```

- - - -

# Movement
* h moves the cursor one character to the left.
* j moves the cursor down one line.
* k moves the cursor up one line.
* l moves the cursor one character to the right.
* 0 moves the cursor to the beginning of the line.
* $ moves the cursor to the end of the line.
* w move forward one word.
* b move backward one word.
* G move to the end of the file.
* gg move to the beginning of the file.
* `. move to the last edit.

- - - -

# Commands can be Combined
`3h` -> Move left three.

- - - -

# Deleting
* d starts the delete operation.
* dw will delete a word.
* d0 will delete to the beginning of a line.
* d$ will delete to the end of a line.
* dgg will delete to the beginning of the file.
* dG will delete to the end of the file.
* u will undo the last operation.
* Ctrl-r will redo the last undo.

- - - -

# Searching
* /text search for text in the document, going forward.
* n move the cursor to the next instance of the text from the last search. This will wrap to the beginning of the document.
* N move the cursor to the previous instance of the text from the last search.
* ?text search for text in the document, going backwards.

- - - -

# Copying & Pasting
* v highlight one character at a time.
* V highlight one line at a time.
* Ctrl-v highlight by columns.
* p paste text after the current line.
* P paste text on the current line.
* y yank text into the copy buffer.

- - - -

# Saving & Quitting
* :w Save file.
* :w <filename> Save a new file.
* :q Quit Vim.
* :q! Quit without saving.

- - - -

# Websites
* [VIM Adventures](https://vim-adventures.com/)
* [Vimcasts - Free screencasts about the text editor Vim](http://vimcasts.org/)
* [Vim Golf](https://vimgolf.com/)
* [Graphical vi-vim Cheat Sheet and
  Tutorial](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)
* [Vim Cheat Sheet](https://vimcheatsheet.com/) (Currently unavailable.)

- - - -

# Articles
* [Vim 101: A Beginner’s Guide to Vim | Linux.com | The source for Linux
  information](https://www.linux.com/learn/vim-101-beginners-guide-vim)
* [100 Vim commands every programmer should
  know](https://www.catswhocode.com/blog/100-vim-commands-every-programmer-should-know)
* [Everyday Vim – A Basic Vim Commands Cheat
  Sheet](https://spin.atomicobject.com/2016/04/19/vim-commands-cheat-sheet/)

