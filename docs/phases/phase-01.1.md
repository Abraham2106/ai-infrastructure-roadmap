# 🐧 The Linux Command Line
> *Study notes — William Shotts | Chapters 1–4*

---

## Chapter 1 — The Shell

The **shell** is a program that takes keyboard commands and passes them to the OS to carry out. The most common shell is called `bash` (*Bourne-Again Shell*). To interact with it we use a **terminal emulator** like GNOME Terminal.

### The prompt

```bash
[user]$
```

If you type something that doesn't exist, the shell responds:

```bash
[user]$ gibberish
Command not found
```

> 💡 **Tip:** Press `↑` to navigate through previous commands.

### Basic commands

| Command | Description | Example output |
|---|---|---|
| `date` | Displays current date and time | `Sat 28 Feb 2026 01:25:12 AM CST` |
| `cal` | Displays current month calendar | *(see below)* |
| `exit` | Ends the terminal session | — |

```bash
   February 2026
Su Mo Tu We Th Fr Sa
 1  2  3  4  5  6  7
 8  9 10 11 12 13 14
15 16 17 18 19 20 21
22 23 24 25 26 27 28
```

---

## Chapter 2 — Navigation

> Key commands: `pwd` · `cd` · `ls`

### The file system tree

Linux organizes its files in a **hierarchical directory structure**, like a tree. The starting point is the **root** directory (`/`), which contains all other files and subdirectories.

### `pwd` — Where am I?

```bash
$ pwd
/home/abe/personal/projects
```

### `ls` — What's here?

```bash
$ ls
assets  backend.pdf  devops  docs  LICENSE  README.md
```

### `cd` — Change directory

There are two ways to specify paths:

**Absolute pathname** — starts from the root `/`:
```bash
$ cd /usr/bin
```

**Relative pathname** — starts from the current working directory:
```bash
$ cd ..        # go up to parent directory
$ cd ./bin     # go into bin from current directory
$ cd -         # go back to previous directory
$ cd           # go to home directory
```

```bash
[me@linuxbox ~]$ cd /usr/bin
[me@linuxbox bin]$ pwd
/usr/bin

[me@linuxbox bin]$ cd ..
[me@linuxbox usr]$ pwd
/usr
```

> 💡 The `./` can be omitted — `cd bin` and `cd ./bin` do the same thing.

### `cd` shortcuts

| Shortcut | Action |
|---|---|
| `cd` | Goes to home directory |
| `cd -` | Goes back to previous directory |
| `cd ~user` | Goes to another user's home directory |

---

## Chapter 3 — Exploring the System

> Key commands: `ls` · `file` · `less`

### `ls` options

```bash
ls /usr          # list a specific directory
ls -l            # long format
ls -a            # list all files (including hidden . files)
ls -A            # like -a but without . and ..
ls -r            # reverse order
ls -S            # sort by file size
ls -t            # sort by modification time
ls -lh           # long format with human-readable sizes
```

### `less` — View text files

`less` lets you browse long text files without opening an editor. Inside `less`:

| Key | Action |
|---|---|
| `Space` | Forward one page |
| `b` | Backward one page |
| `/text` | Search forward |
| `q` | Quit |

### Important system directories

| Directory | Contents |
|---|---|
| `/etc` | System-wide configuration files |
| `/home` | Users' personal directories |
| `/lib` | Shared library files used by core programs |
| `/root` | Home directory of the root account |
| `/usr` | Programs and support files for regular users |
| `/usr/bin` | Executable programs installed by the distro |
| `/usr/lib` | Shared libraries for programs in `/usr/bin` |
| `/usr/local/bin` | Programs compiled from source code |

---

## Chapter 4 — Manipulating Files and Directories

> Key commands: `cp` · `mv` · `mkdir` · `rm` · `ln`

---

### Wildcards

Wildcards let you select groups of files by pattern.

| Wildcard | Description |
|---|---|
| `*` | Matches any characters |
| `?` | Matches any single character |
| `[characters]` | Matches any character in the set |
| `[!characters]` | Matches any character NOT in the set |
| `[[:class:]]` | Matches any character of a specified POSIX class |

**Character classes:**

| Class | Description |
|---|---|
| `[:alnum:]` | Matches any alphanumeric character |
| `[:alpha:]` | Matches any alphabetic character |
| `[:digit:]` | Matches any numeral |
| `[:lower:]` | Matches any lowercase letter |
| `[:upper:]` | Matches any uppercase letter |

**Examples:**

| Pattern | Matches |
|---|---|
| `*` | All files |
| `g*` | Any file beginning with g |
| `b*.txt` | Any file beginning with b followed by any characters and ending with `.txt` |
| `Data???` | Any file beginning with Data followed by exactly three characters |
| `[abc]*` | Any file beginning with either an a, a b, or a c |
| `BACKUP.[0-9][0-9][0-9]` | Any file beginning with `BACKUP.` followed by exactly three numerals |
| `[[:upper:]]*` | Any file beginning with an uppercase letter |
| `[![:digit:]]*` | Any file not beginning with a numeral |
| `*[[:lower:]123]` | Any file ending with a lowercase letter or the numerals 1, 2, or 3 |

---

### `mkdir` — Create directories

```bash
mkdir directory
mkdir dir1 dir2 dir3    # create several at once
```

---

### `cp` — Copy files and directories

```bash
cp item1 item2              # copy item1 to item2
cp item... directory        # copy multiple items into a directory
cp *.txt /usr/bin/downloads # copy all .txt files
```

**Main options:**

| Option | Description |
|---|---|
| `-a`, `--archive` | Copy files and directories with all their attributes and permissions |
| `-i`, `--interactive` | Prompt before overwriting an existing file |
| `-r`, `--recursive` | Recursively copy directories and their contents |
| `-u`, `--update` | Only copy files that are new or newer than the destination |
| `-v`, `--verbose` | Display informative messages as the copy is performed |

---

### `mv` — Move and rename files

```bash
mv item1 item2          # rename or move item1 to item2
mv item... directory    # move multiple items into a directory
```

**Examples:**

| Command | Result |
|---|---|
| `mv file1 file2` | Rename `file1` to `file2`. If `file2` exists, it is overwritten |
| `mv -i file1 file2` | Same, but prompts before overwriting |
| `mv file1 file2 dir1` | Move `file1` and `file2` into `dir1` |
| `mv dir1 dir2` | If `dir2` doesn't exist, create it and move the contents of `dir1` into it |

---

### `rm` — Remove files and directories

```bash
rm file
rm -r directory     # remove a directory and all its contents
```

**Options:**

| Option | Description |
|---|---|
| `-i`, `--interactive` | Prompt before deleting |
| `-r`, `--recursive` | Recursively delete directories and their contents |
| `-f`, `--force` | Ignore errors and do not prompt (overrides `-i`) |
| `-v`, `--verbose` | Display informative messages as deletion is performed |

> ⚠️ **Be careful with `rm -rf`** — there is no recycle bin in the command line. Deleted files are gone for good.

---

### `ln` — Create links

```bash
ln file hard_link           # hard link
ln -s file symbolic_link    # symbolic link (like a shortcut)
```

---
