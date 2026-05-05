### LINUX OVERVIEW

#### OS Types:

- Centos
- Ubuntu
- Parrot
- Kali
- Kali

#### Linux Philosophy:

1. Everything is a file
2. Small, single purpose program
3. Chain programs to perform complex tasks
4. No captive user interface
5. Config data stored in text file

---

## LINUX ARCHITECTURE

### Hardware (Bottom):

- RAM (ROM)
- Kernel

### Layers (Top to Bottom):

1. **Hardware**: RAM, ROM
2. **Kernel** (manages system I/O, devices)
3. **Shell** (user interface, command interpreter)
4. **System Utilities** (functions for users)

---

## COMPONENTS BREAKDOWN

### 1. Boot Loaders: Start the OS

### 2. OS Kernel: Manage system I/O, devices

### 3. Daemons: Background service

### 4. OS Shell: Terminal being used

- BASH: Terminal using used

### 5. Graphics: Running graphics

### 6. Windows Manager: GUI

### 7. Utilities: Functions for users

---

## FILE SYSTEM STRUCTURE

### Top-Level Directory (/) - for booting all the other files

### Files Directory Structure:

1. **/** - Top level directory, for booting all the other files
2. **/bin** - Command binaries
3. **/boot** - For booting system
4. **/dev** - Access hardware attached to the system
5. **/etc** - Portable file stored (Each user has subdirectory)
6. **/home** - Each user has a subdirectory
7. **/lib** - For system boot
8. **/media** - External removable devices
9. **/opt** - Optional third party tools
10. **/root** - root/admin (root/user)
11. **/sbin** - System administration
12. **/tmp** - Temporary file
13. **/usr** - Contain libraries
14. **/var** - Log files, cache
15. **/proc** - Running graphics (because GUI Should id it and security)

---

## SHELL BASICS

### What is Shell?

A window that shows everything to the users

### Terminal emulation:

A way to work simultaneously with multiple windows known as TMUX

---

## SHELL PROMPT

**Format**: `terminal@terminal-temple ~ $`

Breaking down:

- **terminal** - computer name
- **@** - connecting character
- **terminal-temple** - user
- **~** - Working directory
- **$** - Standard users

**Root prompt**: `root@ktb[/ktb]# > 
* **#** - root user

---
	# LINUX COMMANDS & CONCEPTS - ORGANIZED NOTES

**From your handwritten notes - cleaned up** 📝

---

## **BASIC OUTPUT COMMANDS**

### **echo** - Print messages to terminal

```bash
echo "Your message here"
# Syntax: echo "msg you want to print"
```

### **date** - Display current date and time

```bash
date
# Shows: current date and time
```

### **cal** - Display calendar

```bash
cal           # Current month calendar
cal 2026      # Calendar for entire year
cal -j 2026   # Calendar with Julian dates
```

### **ncal** - Display calendar in vertical format

```bash
ncal
# Shows calendar in vertical/narrow format
	```

**variable** - name place for storing information
```bash
name="bliz"
$-> symbol is used for calling the variable
echo "$name"
bliz
echo "name"
name
```


**read -p** - for taking input from the user
```bash
read -p "Enter your name" name 
-p is a flag for prompt
name is the variable for storing it
# Takes input from the user and displays it
```


---

## **ARITHMETIC & CALCULATIONS**

### **expr** - Perform arithmetic operations (+, -, *, /)

```bash
expr 2 + 2    # Result: 4
expr 10 - 3   # Result: 7
expr 5 \* 6   # Result: 30 (escape * with \)
expr 20 / 4   # Result: 5

# IMPORTANT: Put spaces between operation
expr 2+2      # Wrong - prints "2+2"
expr 2 + 2    # Correct - prints "4"
```

---

## **TEXT & ASCII ART**

### **figlet** - Convert text to ASCII art

```bash
figlet "Linux"                    # Basic ASCII art
figlet -f bubble "Linux"          # Different font style
figlet -f banner "Your message"   # Banner style

# View available fonts:
man figlet    # Shows manual and font options
```

---
## 2. The Filesystem

> [!tip] Linux Philosophy **Everything in Linux is treated as a file** — including devices, processes, and directories.

The entire filesystem starts from `/` (the **root directory**) and branches into sub-directories.

### Filesystem Tree (simplified)

```
/
├── bin       → essential user binaries (ls, cp, mv, etc.)
├── etc       → system configuration files
├── home      → user home directories (e.g., /home/taha-asim)
├── var       → variable data (logs, mail, databases)
├── usr       → user programs and libraries
├── tmp       → temporary files (cleared on reboot)
├── root      → home directory of the root user
├── opt       → optional / third-party software
└── dev       → device files
```

> [!warning] `/` vs `/root`
> 
> - `/` → the **root directory** (top of filesystem)
> - `/root` → the **home directory of the root user**
> 
> They sound the same but are different places.

---

## 3. `pwd` — Print Working Directory

Tells you where you currently are in the filesystem.

```bash
pwd
```

**Example:**

```bash
$ cd /home/taha-asim/Desktop/Linux-Notes
$ pwd
/home/taha-asim/Desktop/Linux-Notes
```

---

## 4. Paths — Absolute vs Relative

A **path** is a sequence that leads from a starting point to a specific location in the filesystem.

### Absolute Path

Starts from the **root directory** (`/`). Always begins with `/`.

```bash
cd /home/taha-asim/Desktop/Linux-Notes
```

### Relative Path

Starts from the **current location**. Does _not_ begin with `/`.

```bash
# If currently in ~/Desktop:
cd Linux-Notes
```

### Path Shortcuts

|Shortcut|Meaning|
|---|---|
|`.`|Current directory|
|`..`|Parent directory (one level up)|
|`~`|Your home directory (`/home/taha-asim`)|
|`/`|Filesystem root|
|`-`|Previous directory (`cd -` takes you back)|

---

## 5. `cd` — Change Directory

The primary command for navigating the filesystem.

```bash
cd /home/taha-asim/Desktop/Linux-Notes   # absolute
cd Linux-Notes                            # relative
cd .                                      # stay in current directory
cd ..                                     # go up one level
cd ~                                      # go to home (/home/taha-asim)
cd -                                      # go back to previous directory
```

> [!example] Practice Sequence
> 
> ```bash
> pwd                  # confirm location
> cd ~                 # go home
> pwd
> cd Desktop           # relative move
> cd ..                # back to home
> cd -                 # back to Desktop
> ```

---

## 6. `ls` — List Contents

Lists files and sub-directories in a given location.

### Basic Usage

```bash
ls                              # current directory
ls /home/taha-asim/Desktop      # specific path
```

### Common Flags

|Flag|Purpose|
|---|---|
|`-a`|Show **all** files including hidden ones (those starting with `.`)|
|`-l`|**Long format** — permissions, owner, size, date, name|
|`-h`|**Human-readable** sizes (K/M/G instead of bytes) — use with `-l`|
|`-t`|Sort by **modification time** (newest first)|
|`-r`|**Reverse** order|
|`-R`|**Recursive** — descend into sub-directories|
|`-S`|Sort by **size**|

### Useful Combinations

```bash
ls -la       # long format + hidden files (most common combo)
ls -lh       # long format with readable sizes
ls -lt       # newest files first
ls -ltr      # oldest first (great for log analysis)
ls -lhS      # long, readable, sorted by size
```

> [!tip] Security Relevance Hidden files (`.ssh/`, `.bash_history`, `.env`, `.gitconfig`) often contain credentials, command history, and secrets. Always check them when investigating a system.

### Long Format Anatomy

```
-rw-rw-r--  1  taha-asim  taha-asim  0  May 4 22:17  file.txt
│           │  │          │           │  │           │
│           │  │          │           │  │           └── filename
│           │  │          │           │  └── modification time
│           │  │          │           └── size (bytes)
│           │  │          └── owner group
│           │  └── owner
│           └── number of links
└── permissions
```

---

## 7. `touch` — Create Files / Update Timestamps

> [!note] `touch` has two purposes
> 
> 1. Create an empty file (if it doesn't exist)
> 2. Update the access/modification time of an existing file
> 
> The second behavior is actually `touch`'s original purpose.

### Basic Usage

```bash
touch file.txt                   # single file
touch file1.txt file2.txt        # multiple files at once
```

### Custom Timestamps

```bash
touch -d "2026-04-05 23:00:00" file2.txt
```

**Real example from my terminal:**

```bash
$ touch file.txt
$ ls -l
total 4
-rw-rw-r-- 1 taha-asim taha-asim 0 May 4 22:17 file.txt
```

---

## 8. `file` — Identify File Type

Returns a description of what type of file something is — based on content, not extension.

```bash
file Linux.txt
# Output: Linux.txt: ASCII text
```

> [!tip] Why this matters File extensions can lie. `report.pdf` could actually be a malicious script with a renamed extension. `file` reads the actual content signature, which is harder to fake. This is a basic forensics / security technique.

---



## 📂 File Viewing

### `cat` — concatenate / display file contents

Used to show the contents of a file in the terminal.

```bash
cat Linux.txt                       # display single file
cat Linux.txt file2.txt             # display multiple files (back-to-back)
cat > file2.txt                     # create a new file and type content
                                    # press Ctrl+D to save and exit
```

**Useful flags:**

| Flag | Purpose |
|------|---------|
| `-n` | Number all lines (1 to end of file) |
| `-b` | Number only non-empty lines |

**Example:**
```bash
$ cat -n file2.txt
     1
     2  hello this is my file 2

$ cat -b file2.txt
     1  hello this is my file 2
```

---

### `less` — view large files page by page

Better than `cat` for big files because it lets you scroll and search.

```bash
less /home/taha-asim/Desktop/Linux-Notes/Linux.txt
```

**Navigation inside `less`:**

| Key | Action |
|-----|--------|
| `↑ ↓` (arrows) | Scroll line by line |
| `Space` | Page down |
| `g` | Jump to beginning |
| `G` | Jump to end |
| `h` | Show help menu |
| `q` | Quit |

**Searching inside `less`:**

| Key | Action |
|-----|--------|
| `/term` | Search **forward** for term |
| `?term` | Search **backward** for term |
| `n` | Next match (same direction) |
| `N` | Previous match (opposite direction) |

> 💡 **Real use:** `less /var/log/auth.log` then `/Failed` walks you through every failed login attempt — exactly how you'd hunt suspicious activity.

---

## 📜 Command History

```bash
history          # shows all the commands you've typed in this session
```

Useful for recalling that one perfect command you ran an hour ago.

---

## 📋 Copying Files (`cp`)

### Basic Syntax

```bash
cp [source] [destination]
```

```bash
cp file2.txt /home/taha-asim/Desktop
```

### Wildcards (Glob Patterns)

| Wildcard | Matches |
|----------|---------|
| `*` | Any sequence of characters |
| `?` | Exactly one character |
| `[ ]` | Any one of the characters inside |

```bash
cp *.txt /home/taha-asim/Documents      # copy all txt files
cp file?.txt /backup/                    # file1.txt, fileA.txt, etc.
cp [abc].txt /backup/                    # a.txt, b.txt, or c.txt
```

### Copying Directories

Use `-r` (recursive) to copy folders and their contents:

```bash
cp -r Linux-Notes/ /home/taha-asim/Documents
```

### Important Flags

#### `-i` — Interactive (ask before overwriting)

```bash
cp -i source.txt dest.txt
```

```
   ┌─ Does dest.txt already exist?
   │
   ├─ NO  → Just copy silently. Done.
   │
   └─ YES → STOP. Ask: "overwrite?"
            ├─ y → overwrites
            └─ n → cancels
```

**Real example:**
```bash
$ cp -i file2.txt /home/taha-asim/Documents
cp: overwrite '/home/taha-asim/Documents/file2.txt'? y
```

#### `-f` — Force overwrite (no asking)

```bash
cp -f file2.txt /home/taha-asim/Documents
```

Same effect as `-i` accepting yes, but **without prompting**. Use carefully.

#### `-p` — Preserve timestamps & metadata

| | Without `-p` | With `-p` |
|---|---|---|
| **Timestamp** | Set to current time | Original timestamp kept |
| **Owner** | Becomes you | Original owner kept |
| **Permissions** | Default | Original permissions kept |

```bash
cp -p file.txt backup/
```

> 🔐 **Why it matters:** for backups, forensics, or migrations, preserving timestamps is critical — they're evidence of when something actually happened.

---

## 🔄 Moving & Renaming (`mv`)

`mv` does **two jobs**: moving files between folders, and renaming files in place.

### Renaming

```bash
mv oldfile newfile
```

Same syntax works for directories.

### Moving

```bash
mv file.txt /home/taha-asim/Documents/
```

### Useful Flags

| Flag | Purpose |
|------|---------|
| `-i` | Ask before overwriting |
| `-b` | Backup the existing file with a `~` suffix before overwriting |
| `-v` | Verbose — show what's being done |

**Example:**
```bash
$ mv -v file2.txt testfile.txt
renamed 'file2.txt' -> 'testfile.txt'
```

> 💡 **`-b` in action:** if you `mv -b new.txt /docs/` and `/docs/new.txt` already exists, the old one becomes `/docs/new.txt~` (backup) and your new file takes its place.

---

## 📁 Creating Directories (`mkdir`)

```bash
mkdir folder_name
```

### `-p` — Create parent directories as needed

Creates the entire path even if the parent folders don't exist:

```bash
mkdir -p books/title/author
```

This single command creates all three folders (`books`, `title`, `author`) in one go. Without `-p`, you'd have to make them one at a time.

---

## 🗑️ Removing Files (`rm`)

> ⚠️ **Warning:** `rm` is permanent. There is no recycle bin in Linux. Once it's gone, it's gone.

### Basic Usage

```bash
rm file1
```

### Flags

| Flag | Purpose |
|------|---------|
| `-i` | Ask for confirmation before each deletion |
| `-f` | Force — delete without prompting (dangerous) |
| `-r` | Recursive — delete folders and their contents |
| `-v` | Verbose — show what's being deleted |

**Examples:**
```bash
rm -i file1                  # asks before deleting
rm -f file1                  # deletes silently, no questions
rm -r D1                     # delete a directory and everything inside
rm -rf folder/               # nuclear option — recursive force delete
```

### `rmdir` — Remove an Empty Directory

```bash
rmdir D1
```

Only works if the directory is **completely empty**. Safer than `rm -r` when you just want to clean up an empty folder.

---

## 🔎 Finding Files (`find`)

```bash
find [path] [expression]
```

### Search by Name

```bash
find /home -name myfile.txt
find -name file2.txt
# Output: ./Desktop/file2.txt
```

### Search by Type

| Flag | Meaning |
|------|---------|
| `-type f` | Files only |
| `-type d` | Directories only |

```bash
find -type d -name Linux-Notes
# Output: ./Desktop/Linux-Notes
```

> 💡 **Pro tip:** `find` is the proper way to search across folder trees. Wildcards like `*` only work in one folder at a time.

---

## ❓ Getting Help

### `--help` — Quick flag reference

```bash
ls --help
```

Shows a quick summary of a command's flags and usage.

### `man` — Full manual

```bash
man ls
```

Opens the complete manual page for a command. Navigate with `less`-style keys (`/`, `n`, `q`).

### `whatis` — One-line description

```bash
whatis cp
# cp (1) - copy files and directories
```

Quick way to remember what a command does without opening the full manual.

---

## ⚡ Aliases

Aliases are shortcuts for commands you type often.

### Creating a Permanent Alias

1. Open your bash config:
   ```bash
   nano ~/.bashrc
   ```

2. Add your aliases at the bottom:
   ```bash
   alias show='cat'
   alias update='sudo apt update && sudo apt upgrade'
   ```

3. Save: `Ctrl + O`, then `Enter`

4. Exit: `Ctrl + X`

5. Reload bash to apply:
   ```bash
   source ~/.bashrc
   ```

### Removing an Alias

```bash
unalias show
```

### Useful Aliases to Add

```bash
# Navigation
alias ..='cd ..'
alias ...='cd ../..'
alias ll='ls -lah'

# Safety
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

# Shortcuts
alias update='sudo apt update && sudo apt upgrade -y'
alias gs='git status'
```

---
<div align="center">

# 🐧 Linux Command Reference

### *My day-by-day notes on essential Linux commands — written as I learn.*

[![Linux](https://img.shields.io/badge/Linux-Ubuntu_24.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Bash](https://img.shields.io/badge/Shell-Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Status](https://img.shields.io/badge/Status-Living_Document-blue?style=for-the-badge)](https://github.com/Tahaasim502)
[![Phase](https://img.shields.io/badge/Phase-Foundations-yellow?style=for-the-badge)](https://github.com/Tahaasim502)

---

*"The best way to learn Linux is to live in it."*

</div>

---

## 📖 About

This is my personal Linux command reference, built as I work through my **60-day Linux mastery plan** on the path to becoming a Security Engineer. Every command here is one I've actually run, broken, fixed, and understood.

If you're learning Linux too, feel free to fork this and start your own.

---