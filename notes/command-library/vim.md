---
layout: page
title: vim
permalink: /notes/command-library/vim/
---

- Switch to command mode
	- Press `ESC`

- Show current working directory
```
:pwd
```

- Change working directory
```
:cd <path/to/new/directory>
```

- Save file
```
:w <filename>
```

- Save file with fullpath
```
:w </full/path/filename>
```

- Open existing file
```
vi <file_path>
```

- Open Bash file using vim
```
vim ~/.bashrc
```

- Check pip version
```
pip -V
```

- Save the file without quit
```
:w
```

- Save the file and quit
```
:wq
```

- Select character: `v`, or whole line: `V`

- Paste before cursor: `P`, or after cursor: `p`

- Open file explorer
	- Click `Ctrl-N`

- Shift cursor to file explorer
	- Click `Ctrl-W` + left arrow key.

- Shift cursor to code editor
	- Click `Ctrl-W` + right arrow key.

- Comment a code block
	- `Ctrl-V` go to visual mode
	- Select the code block
	- `Shift-i`
	- Enter a `#` (for Python).
	- `ESC`

- Uncomment code block
	- `Ctrl-V` go to visual mode
	- Select the commented code block
	- Enter `X`.

- Freeze and unfreeze screen output
	- Freeze: `Ctrl-S`
	- Unfreeze: `Ctrl-Q`

- Scroll down to next result under Search mode
	- Press `n`

- Copy the entire row and paste to the following row
	- Press `yy` followed by `p`.

- Move cursor (under Control mode)
	- to start of a line: `Shift - ^`
	- to end of a line: `Shift - $`
	- to end of a file: `Shift - g`

- Add/reduce indent of code block
	- Press V and select the block of code.
	- Press `Shift + '>' or '<'` to add/reduce indentation.

- Select the entire row, and paste it behind
	- Press `Shift-V` to select the current row.
	- Press `y` to copy and `p` to paste.

- Find and replace for the whole file
	- Under control mode: `:%s/foo/lish/g`

- Faster way of exixting file and switching back
	- Exit: `Ctrl-z`
	- Switch back: `fg`

- Set number of space to insert when pressing tab key
	- Create a ~/.vimrc file with this line:
```
set ts=4 sw=4
#:set expandtab ts=4 sw=4
```

 - To paste text to vim editor
```
:set paste
```

