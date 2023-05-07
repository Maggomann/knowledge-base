---
category: wiki
sub_category_1: linux
sub_category_2: screen
language: en
tags:
- wiki
- linux
- screen
---

1.  Identify the name of the session:

```bash
 $ screen -ls
```

2.  Close a session:

```bash
$ screen -XS <session-id> quit
```

- **screen**

Command to install the packages:

```bash
sudo apt-get install screen
```

Or install with [apturl](https://wiki.ubuntuusers.de/apturl/), link: [apt://screen](apt://screen "apt://screen")

## Opera

The window manager can be started with the command screen in a terminal.

### General

After calling screen, it seems as if nothing has happened. But this is not true, because screen is now running in the background to manage the sessions. You can now continue working normally and start various programs as you are used to.

### Important commands

The three most important commands or key combinations you should know are:

- Ctrl + A , followed by C to create a new window
- Ctrl + A , followed by N to switch to the next window
- Ctrl + A followed by D to detach the connection to the current session, the session will continue running in the background.

For an overview of all keyboard shortcuts, press Ctrl + A followed by ?

A session is ended by terminating the shell running there, i.e. either with the `exit` command or by pressing Ctrl + D .

### Other commands

Start a new session with the name "sitzung1".

```bash
screen -S sitzung1
```

Disconnects from the current session: Ctrl + A + D.

Resumes the session if only one session is running in the background:

Resumes the session with the name "sitzung1":

```bash
screen -r sitzung1
```

List the names of all running screen sessions:

Disconnects a running session with the name "sitzung1" (very useful if, for example, you lost the connection via ssh and therefore could not disconnect the session):

```bash
screen -d sitzung1
```

The session named "sitzung1" can be displayed on several computers at the same time:

```bash
screen -rx sitzung1
```

Send a command to the session named "sitzung1" and execute it (\n for \[ENTER\]):

```bash
screen -S sitzung1 -X stuff $'ls -l\n'
```

Toggle visual notification (flicker or sound; if the screen sometimes flickers, you should run this command until it says "switched to audible bell" at the bottom left): Ctrl + A + G

### Difference between session and window

The difference between a screen session and a screen window can be thought of as something like a browser with tabs, where screen sessions correspond to a browser window and screen windows correspond to a browser tab. You can have multiple screen sessions running at the same time and multiple screen windows open in each screen session, just as you can have multiple browser windows open and multiple tabs open in each browser window.

### Scrolling output

To scroll in the output of a screen window using the familiar key combinations ⇧ + image ↑ and ⇧ + image ↓, enter the line

```bash
termcapinfo xterm|xterms|xs|rxvt ti@:te@
```

Into the file **.screenrc** (which may still have to be created) in the home directory.

If this does not work, there is still the possibility to switch to the copy mode with Ctrl + A + Esc and to scroll there with the arrow keys or Ctrl + U (half window up), Ctrl + D (half window down), Ctrl + B (whole window back), Ctrl + F (whole window forward). After that you can leave the copy mode by pressing Esc or Q .

## Links

-   [Projektseite](https://www.gnu.org/software/screen/screen.html) 🇬🇧

-   [tmux](https://wiki.ubuntuusers.de/tmux/) - Alternative zu screen

-   [byobu](https://wiki.ubuntuusers.de/byobu/) - Erweiterung für screen
