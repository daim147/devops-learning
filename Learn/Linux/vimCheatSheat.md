# Vim Cheat Sheet

This is command mode editor for files. Other editors in Linux are emacs, gedit
vi editor is most popular

It has 3 modes:

1. Command Mode
2. Insert Mode
3. Extended Command Mode

By default, it opens in command mode. To enter insert mode, press `i`. To enter extended command mode, press `:`

## Basic Navigation

- `gg` - Go to beginning of file
- `G` - Go to end of file
- `w` - Move cursor forward one word
- `b` - Move cursor backward one word
- `nw` - Move cursor forward n words (e.g., `5w`)
- `nb` - Move cursor backward n words (e.g., `5b`)
- `0` - Move to beginning of line
- `$` - Move to end of line
- `h` - Move left
- `j` - Move down
- `k` - Move up
- `l` - Move right
- `:n` or `:20` - Go to line number n (e.g., line 20)

## Editing Modes

- `i` - Insert mode (before cursor)
- `a` - Insert mode (after cursor)
- `A` - Insert mode (end of line)
- `o` - Insert mode (new line below)
- `O` - Insert mode (new line above)
- `Esc` - Exit insert mode and return to normal mode

## Copy & Paste (Yank)

- `yy` or `VY` - Copy (yank) entire line
- `nyy` - Copy n lines (e.g., `5yy`)
- `p` - Paste below cursor
- `P` - Paste above cursor
- `dd` - Cut entire line
- `ndd` - Cut n lines (e.g., `5dd`)

## Deleting & Undoing

- `x` - Delete character under cursor
- `X` - Delete character before cursor
- `dw` - Delete word
- `dd` - Delete line
- `ndd` - Delete n lines
- `d$` - Delete to end of line
- `d0` - Delete to beginning of line
- `u` - Undo last change
- `U` - Undo all changes on line
- `Ctrl+r` - Redo changes

## Extended Mode (Colon Mode)

- `Esc+:w` - Save changes
- `Esc+:w!` - Force save changes
- `Esc+:q` - Quit without saving
- `Esc+:q!` - Force quit without saving
- `Esc+:wq` - Save and quit
- `Esc+:wq!` - Force save and quit
- `Esc+:x` - Save and quit
- `Esc+:X` - Set/remove password for file
- `Esc+:se nu` - Show line numbers
- `Esc+:se nonu` - Hide line numbers

## Search & Replace

- `/pattern` - Search forward for pattern
- `?pattern` - Search backward for pattern
- `n` - Repeat search forward
- `N` - Repeat search backward
- `:%s/old/new/g` - Replace all occurrences in file
- `:s/old/new/g` - Replace all occurrences in line

## Visual Mode

- `v` - Start visual mode
- `V` - Start linewise visual mode
- `Ctrl+v` - Start visual block mode
- `y` - Copy selection
- `d` - Delete selection
- `>` - Indent right
- `<` - Indent left

## Windows & Tabs

- `:sp filename` - Open filename in horizontal split
- `:vsp filename` - Open filename in vertical split
- `Ctrl+w h/j/k/l` - Navigate between windows
- `:tabnew filename` - Open filename in new tab
- `gt` - Next tab
- `gT` - Previous tab

## Miscellaneous

- `.` - Repeat last command
- `ZZ` - Save and quit
- `ZQ` - Quit without saving
- `:help` - Open help
- `:set number` - Show line numbers
- `:set nonumber` - Hide line numbers

## Reviewing Changes in Vim

To review changes in Vim, you can use several built-in features and plugins. Here are some methods to help you review changes:

### 1. Using Vim's Built-in Features

#### Undo and Redo

- **Undo**: To undo changes, press `u`.
- **Redo**: To redo changes, press `Ctrl-r`.

#### Viewing Undo History

- **Undo Tree**: Vim has an undo tree that allows you to navigate through different states of your file.
  - To view the undo tree, you can use the `:undolist` command.
  - To navigate through the undo tree, you can use `:earlier` and `:later` commands.

### 2. Using Diff Mode

If you have two versions of a file and want to compare them, you can use Vim's diff mode.

#### Open Files in Diff Mode

```bash
vimdiff file1 file2
```

or within Vim:

```vim
:vert diffsplit file2
```

### 3. Using Plugins

If you are using Git, the vim-fugitive plugin is very powerful for reviewing changes.
Install `vim-fugitive`: You can install it using a plugin manager like vim-plug.

First need to install Plug

```base
Plug 'tpope/vim-fugitive'
```

View Git Diff: Within Vim, you can use the following commands:

- `:Gdiff` - Open the Git diff for the current file.
- `:Gstatus` - Open the Git status window to stage or view changes.
- `:Gblame` - Open the Git blame view to see who changed each line.
- `:Gcommit` - Open the Git commit window to write a commit message.
- `:Gpush` - Push changes to the remote repository.
- `:Gpull` - Pull changes from the remote repository.
- `:Glog` - View the Git log.
- `:Ggrep` - Search the Git repository.
- `:Gmove` - Move or rename a file in Git.
- `:Gdelete` - Delete a file in Git.
- `:Gread` - Read a file from the Git repository.
- `:Gwrite` - Write the current file to the Git repository.
- `:Gbrowse` - Open the current file in the Git repository in a web browser.
- `:Gedit` - Open a file from the Git repository.
- `:Gbrowse` - Open the current file in the Git repository in a web browser.

#### vim-signify or vim-gitgutter

These plugins show a visual representation of changes in the gutter (the left side of the editor).

Install vim-signify:

```vim
Plug 'mhinz/vim-signify'
```

Install vim-gitgutter:

```vim
Plug 'airblade/vim-gitgutter'
```
