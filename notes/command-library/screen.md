---
layout: page
title: screen
permalink: /notes/command-library/screen/
---

- List out all existing screen sessions.
```bash
screen -ls
```

- Initiate new screen window.
```bash
screen -S <screen-name>
```

- Kill useless screen session.
```bash
kill <screen-id>
```

- Enter an existing detached screen session.
```bash
screen -r <screen-id>
```

- Enter an existing attached screen session (hint: detach first)
```bash
screen -rd <screen-id>
```

- Address screen backspace problem
```bash
$ export TERM=screen
```

- Exit from the current screen window (detach)
	- Click `Ctrl-a d` on the keyboard.

- Create a new terminal window in a screen session.
	- Click `Ctrl-a c` on the keyboard.

- Rename the current terminal window.
	- Click `Ctrl-a Shift-a` on the keyboard.

- List all terminal windows in a screen session.
	- Click `Ctrl-a Shift-"`on the keyboard.

- Redirect to the next terminal window.
	- Click `Ctrl-a Space` on the keyboard.

- Redirect to the former terminal window.
	- Click `Ctrl-a Backspace` on the keyboard.

- Kill the current screen window
	- Click `Ctrl-a k` on the keyboard.

- Make the screen session scrollable.
	- Click `Ctrl-a ESC` on the keyboard.

- Scroll up in a screen session.
	- Press `Ctrl-A` on the keyboard and press `Esc`.
	- Press the `Up` and `Down` arrow keys or the `PgUp` and `PgDn` keys to scroll through previous output.
	- Press `Esc` to exit scrollback mode.