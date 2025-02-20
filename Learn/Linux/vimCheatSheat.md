# Vim Cheat Sheet

## Table of Contents

- [Vim Cheat Sheet](#vim-cheat-sheet)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Basic Navigation](#basic-navigation)
- [These commands are used to move the cursor around the file in command mode.](#these-commands-are-used-to-move-the-cursor-around-the-file-in-command-mode)
  - [Working with Buffers](#working-with-buffers)
- [Buffers are Vim's way of handling files in memory.](#buffers-are-vims-way-of-handling-files-in-memory)
  - [Editing Modes](#editing-modes)
- [These commands switch between different editing modes.](#these-commands-switch-between-different-editing-modes)
  - [Copy \& Paste (Yank)](#copy--paste-yank)
- [These commands are used for copying, cutting, and pasting text.](#these-commands-are-used-for-copying-cutting-and-pasting-text)
  - [Deleting \& Undoing](#deleting--undoing)
- [Commands for deleting text and undoing changes.](#commands-for-deleting-text-and-undoing-changes)
  - [Extended Mode (Colon Mode)](#extended-mode-colon-mode)
- [Commands entered by pressing `:` in normal mode.](#commands-entered-by-pressing--in-normal-mode)
  - [Search \& Replace](#search--replace)
- [Commands for searching and replacing text.](#commands-for-searching-and-replacing-text)
  - [Visual Mode](#visual-mode)
- [Commands for selecting text visually.](#commands-for-selecting-text-visually)
  - [Macros](#macros)
- [Macros allow you to record and replay a series of commands.](#macros-allow-you-to-record-and-replay-a-series-of-commands)
  - [Windows \& Tabs](#windows--tabs)
- [Commands for managing multiple windows and tabs.](#commands-for-managing-multiple-windows-and-tabs)
  - [Miscellaneous](#miscellaneous)
- [Useful commands that don't fit into other categories.](#useful-commands-that-dont-fit-into-other-categories)
  - [Reviewing Changes in Vim](#reviewing-changes-in-vim)
- [To review changes in Vim, you can use several built-in features and plugins. Here are some methods to help you review changes:](#to-review-changes-in-vim-you-can-use-several-built-in-features-and-plugins-here-are-some-methods-to-help-you-review-changes)
  - [1. Using Vim's Built-in Features](#1-using-vims-built-in-features)
    - [Undo and Redo](#undo-and-redo)
    - [Viewing Undo History](#viewing-undo-history)
  - [2. Using Diff Mode](#2-using-diff-mode)
- [If you have two versions of a file and want to compare them, you can use Vim's diff mode.](#if-you-have-two-versions-of-a-file-and-want-to-compare-them-you-can-use-vims-diff-mode) - [Open Files in Diff Mode](#open-files-in-diff-mode)

## Introduction

Vim (Vi Improved) is a highly configurable text editor known for efficient text editing. It is an improved version of the vi editor distributed with most UNIX systems. Vim is known for its modal editing, extensive plugin support, and powerful customization options. Other editors in Linux are emacs and gedit, but Vim remains a favorite among developers and system administrators.

Vim operates in three primary modes:

1. **Command Mode**: For navigating and executing commands.
2. **Insert Mode**: For inserting and appending text.
3. **Extended Command Mode (Ex Mode)**: For executing more complex commands.

By default, Vim opens in command mode. Press `i` to enter insert mode and `:` to enter extended command mode.

## Basic Navigation

# These commands are used to move the cursor around the file in command mode

- `gg`: Go to the beginning of the file.

  ```vim
  gg
  ```

- `G`: Go to the end of the file.

  ```vim
  G
  ```

- `w`: Move the cursor forward one word.

  ```vim
  w
  ```

- `b`: Move the cursor backward one word.

  ```vim
  b
  ```

- `nw`: Move the cursor forward n words (e.g., `5w`).

  ```vim
  5w
  ```

- `nb`: Move the cursor backward n words (e.g., `5b`).

  ```vim
  5b
  ```

- `0`: Move to the beginning of the line.

  ```vim
  0
  ```

- `$`: Move to the end of the line.

  ```vim
  $
  ```

- `h`: Move left.

  ```vim
  h
  ```

- `j`: Move down.

  ```vim
  j
  ```

- `k`: Move up.

  ```vim
  k
  ```

- `l`: Move right.

  ```vim
  l
  ```

- `:n` or `:20`: Go to line number n (e.g., line 20).

  ```vim
  :20
  ```

## Working with Buffers

# Buffers are Vim's way of handling files in memory

- `:e filename`: Open a file in a new buffer.

  ```vim
  :e filename
  ```

- `:bnext` or `:bn`: Go to the next buffer.

  ```vim
  :bn
  ```

- `:bprev` or `:bp`: Go to the previous buffer.

  ```vim
  :bp
  ```

- `:ls`: List all open buffers.

  ```vim
  :ls
  ```

- `:bd`: Delete (close) the current buffer.

  ```vim
  :bd
  ```

## Editing Modes

# These commands switch between different editing modes

- `i`: Insert mode (before cursor).

  ```vim
  i
  ```

- `a`: Insert mode (after cursor).

  ```vim
  a
  ```

- `A`: Insert mode (end of line).

  ```vim
  A
  ```

- `o`: Insert mode (new line below).

  ```vim
  o
  ```

- `O`: Insert mode (new line above).

  ```vim
  O
  ```

- `Esc`: Exit insert mode and return to normal mode.

  ```vim
  Esc
  ```

## Copy & Paste (Yank)

# These commands are used for copying, cutting, and pasting text

- `yy` or `Y`: Copy (yank) entire line.

  ```vim
  yy
  ```

- `nyy`: Copy n lines (e.g., `5yy`).

  ```vim
  5yy
  ```

- `p`: Paste below cursor.

  ```vim
  p
  ```

- `P`: Paste above cursor.

  ```vim
  P
  ```

- `dd`: Cut entire line.

  ```vim
  dd
  ```

- `ndd`: Cut n lines (e.g., `5dd`).

  ```vim
  5dd
  ```

- `"+y`: Copy to system clipboard.

  ```vim
  "+y
  ```

- `"+p`: Paste from system clipboard.

  ```vim
  "+p
  ```

## Deleting & Undoing

# Commands for deleting text and undoing changes

- `x`: Delete character under cursor.

  ```vim
  x
  ```

- `X`: Delete character before cursor.

  ```vim
  X
  ```

- `dw`: Delete word.

  ```vim
  dw
  ```

- `dd`: Delete line.

  ```vim
  dd
  ```

- `ndd`: Delete n lines.

  ```vim
  ndd
  ```

- `d$`: Delete to end of line.

  ```vim
  d$
  ```

- `d0`: Delete to beginning of line.

  ```vim
  d0
  ```

- `u`: Undo last change.

  ```vim
  u
  ```

- `U`: Undo all changes on line.

  ```vim
  U
  ```

- `Ctrl+r`: Redo changes.

  ```vim
  Ctrl+r
  ```

## Extended Mode (Colon Mode)

# Commands entered by pressing `:` in normal mode

- `:w`: Save changes.

  ```vim
  :w
  ```

- `:w!`: Force save changes (if you have permission issues).

  ```vim
  :w!
  ```

- `:q`: Quit without saving.

  ```vim
  :q
  ```

- `:q!`: Force quit without saving.

  ```vim
  :q!
  ```

- `:wq`: Save and quit.

  ```vim
  :wq
  ```

- `:wq!`: Force save and quit.

  ```vim
  :wq!
  ```

- `:x`: Save and quit (only if changes were made).

  ```vim
  :x
  ```

- `:X`: Set/remove password for file.

  ```vim
  :X
  ```

- `:set nu`: Show line numbers.

  ```vim
  :set nu
  ```

- `:set nonu`: Hide line numbers.

  ```vim
  :set nonu
  ```

- `:set ai`: Auto indent.

  ```vim
  :set ai
  ```

- `:set noai`: Disable auto indent.

  ```vim
  :set noai
  ```

- `:set ruler`: Show ruler.

  ```vim
  :set ruler
  ```

- `:syntax on`: Enable syntax highlighting.

  ```vim
  :syntax on
  ```

- `:syntax off`: Disable syntax highlighting.

  ```vim
  :syntax off
  ```

## Search & Replace

# Commands for searching and replacing text

- `/pattern`: Search forward for pattern.

  ```vim
  /pattern
  ```

- `?pattern`: Search backward for pattern.

  ```vim
  ?pattern
  ```

- `n`: Repeat search forward.

  ```vim
  n
  ```

- `N`: Repeat search backward.

  ```vim
  N
  ```

- `:%s/old/new/g`: Replace all occurrences in file.

  ```vim
  :%s/old/new/g
  ```

- `:%s/old/new/gc`: Replace all occurrences in file with confirmation.

  ```vim
  :%s/old/new/gc
  ```

- `:s/old/new/g`: Replace all occurrences in line.

  ```vim
  :s/old/new/g
  ```

- `:%s/\\<old\\>/new/g`: Replace whole words only.

  ```vim
  :%s/\<old\>/new/g
  ```

## Visual Mode

# Commands for selecting text visually

- `v`: Start visual mode (character-wise).

  ```vim
  v
  ```

- `V`: Start linewise visual mode.

  ```vim
  V
  ```

- `Ctrl+v`: Start visual block mode.

  ```vim
  Ctrl+v
  ```

- `y`: Copy selection.

  ```vim
  y
  ```

- `d`: Delete selection.

  ```vim
  d
  ```

- `>`: Indent right.

  ```vim
  >
  ```

- `<`: Indent left.

  ```vim
  <
  ```

- `gv`: Reselect the previous visual selection.

  ```vim
  gv
  ```

## Macros

# Macros allow you to record and replay a series of commands

- `q[char]`: Start recording a macro in register `[char]` (e.g., `qa`).

  ```vim
  qa
  ```

- `q`: Stop recording the macro.

  ```vim
  q
  ```

- `@[char]`: Execute the macro stored in register `[char]` (e.g., `@a`).

  ```vim
  @a
  ```

- `@@`: Re-execute the last executed macro.

  ```vim
  @@
  ```

## Windows & Tabs

# Commands for managing multiple windows and tabs

- `:sp filename`: Open filename in horizontal split.

  ```vim
  :sp filename
  ```

- `:vsp filename`: Open filename in vertical split.

  ```vim
  :vsp filename
  ```

- `Ctrl+w h/j/k/l`: Navigate between windows (left/down/up/right).

  ```vim
  Ctrl+w h
  ```

- `:tabnew filename`: Open filename in new tab.

  ```vim
  :tabnew filename
  ```

- `:tabn` or `:tabnext`: Go to the next tab.

  ```vim
  :tabn
  ```

- `:tabp` or `:tabprev`: Go to the previous tab.

  ```vim
  :tabp
  ```

- `:tabmove [index]`: Move the current tab to the specified index.

  ```vim
  :tabmove 2
  ```

- `:tabclose`: Close the current tab.

  ```vim
  :tabclose
  ```

- `:tabonly`: Close all tabs except the current one.

  ```vim
  :tabonly
  ```

## Miscellaneous

# Useful commands that don't fit into other categories

- `.`: Repeat last command.

  ```vim
  .
  ```

- `ZZ`: Save and quit.

  ```vim
  ZZ
  ```

- `ZQ`: Quit without saving.

  ```vim
  ZQ
  ```

- `:help`: Open help.

  ```vim
  :help
  ```

- `:set number` or `:set nu`: Show line numbers.

  ```vim
  :set number
  ```

- `:set nonumber` or `:set nonu`: Hide line numbers.

  ```vim
  :set nonumber
  ```

- `:!command`: Execute a shell command.

  ```vim
  :!ls -l
  ```

- `:r filename`: Insert the content of filename into the current file.

  ```vim
  :r filename
  ```

- `:set wrap`: Enable line wrapping.

  ```vim
  :set wrap
  ```

- `:set nowrap`: Disable line wrapping.

  ```vim
  :set nowrap
  ```

## Reviewing Changes in Vim

# To review changes in Vim, you can use several built-in features and plugins. Here are some methods to help you review changes

### 1. Using Vim's Built-in Features

#### Undo and Redo

- **Undo**: To undo changes, press `u`.

  ```vim
  u
  ```

- **Redo**: To redo changes, press `Ctrl-r`.

  ```vim
  Ctrl-r
  ```

#### Viewing Undo History

- **Undo Tree**: Vim has an undo tree that allows you to navigate through different states of your file.

  - To view the undo tree, you can use the `:undolist` command.

    ```vim
    :undolist
    ```

  - To navigate through the undo tree, you can use `:earlier` and `:later` commands.

    ```vim
    :earlier 4m "Go back 4 minutes"
    :later 1h    "Go forward 1 hour"
    ```

### 2. Using Diff Mode

# If you have two versions of a file and want to compare them, you can use Vim's diff mode

#### Open Files in Diff Mode
