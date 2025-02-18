# Vim Cheat Sheet

Vim (Vi Improved) is a highly configurable text editor built to enable efficient text editing. It is an improved version of the vi editor distributed with most UNIX systems. Vim is known for its modal editing, extensive plugin support, and powerful customization options. Other editors in Linux are emacs and gedit, but Vim remains a favorite among developers and system administrators.

Vim operates in three primary modes:

1.  **Command Mode**: For navigating and executing commands.
2.  **Insert Mode**: For inserting and appending text.
3.  **Extended Command Mode (Ex Mode)**: For executing more complex commands.

By default, Vim opens in command mode. Press `i` to enter insert mode and `:` to enter extended command mode.

## Basic Navigation

These commands are used to move the cursor around the file in command mode.

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

## Editing Modes

These commands switch between different editing modes.

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

These commands are used for copying, cutting, and pasting text.

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

## Deleting & Undoing

Commands for deleting text and undoing changes.

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

Commands entered by pressing `:` in normal mode.

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

## Search & Replace

Commands for searching and replacing text.

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

## Visual Mode

Commands for selecting text visually.

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

## Windows & Tabs

Commands for managing multiple windows and tabs.

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
- `gt`: Next tab.
  ```vim
  gt
  ```
- `gT`: Previous tab.
  ```vim
  gT
  ```

## Miscellaneous

Useful commands that don't fit into other categories.

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

## Reviewing Changes in Vim

To review changes in Vim, you can use several built-in features and plugins. Here are some methods to help you review changes:

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

If you have two versions of a file and want to compare them, you can use Vim's diff mode.

#### Open Files in Diff Mode
