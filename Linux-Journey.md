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

