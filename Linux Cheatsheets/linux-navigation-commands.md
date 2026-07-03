# Linux Navigation Commands Cheatsheet
## Week 1 - Day 7

---
## Stdout - Standard output
 **Echo** is the standard output

#### Example
```bash
$ echo Hello!
Hello!
```
### Redirecting (>)
It is used to copy the output of echo to a file,whether it exist or not and overwrite a existing file.

#### Example
```bash
$ echo Hello Github! > file.txt
Hello Github!
$ cat file.txt
Hello Github!
```
### Appending (>>)
It is used to copy the output of echo to a existing file without changing its previous content.

#### Example
```bash
$ cat file.txt
Hola,
$ echo Hello Github! >> file.txt
Hello Github!
$ cat file.txt
Hola,Hello Github!
```
---
## Whoami 
 It is used to find out what user we're currently logged in.
 ```bash
$ whoami
khushi_18
```
---

## pwd - Print Working Directory
Shows your current location in the file system

#### Example
```bash
$ pwd
/home/username/Documents
```

### When to Use
- ✅ Confirm your current location
- ✅ Get full path for scripts
- ✅ Verify navigation success

---

## cd - Change Directory
Navigate between directories

#### Syntax
```bash
cd /path/to/directory       # Absolute path
cd dirname                  # Relative path
cd ..                       # Go up one level
cd ~                        # Home directory
cd -                        # Previous directory
```

#### Examples
```bash
$ cd /home                  # Absolute path
$ cd Documents              # Relative path (from current dir)
$ cd ..                     # Go up one directory
$ cd ~                      # Go to home
$ cd -                      # Go back to previous directory
$ pwd                       # Verify location
```

#### Common Patterns
```bash
cd /var/log                 # Navigate to absolute path
cd ./Documents              # Current dir + subfolder
cd ../../                   # Go up two levels
cd ~/Downloads              # Home + Downloads
```

---

## ls - List Files and Directories
Display directory contents

#### Syntax
```bash
ls                          # Simple listing
ls -l                       # Long format (detailed)
ls -a                       # Show hidden files
ls -la                      # Long + hidden (most useful)
ls -lh                      # Long + human-readable sizes
ls -lS                      # Sort by size
ls -lt                      # Sort by modification time
ls -R                       # Recursive (show subdirectories)
ls /path                    # List specific directory
ls -r                       # sort the files in dir in reverse alpha order
```

#### Examples
```bash
$ ls
Documents  Downloads  file.txt

$ ls -l
-rw-r--r-- 1 user user 4096 Jun 28 10:30 file.txt
drwxr-xr-x 2 user user 4096 Jun 28 11:22 Documents

$ ls -la
-rw-r--r--  1 user user  1234 Jun 28 10:30 .bashrc
-rw-r--r--  1 user user  4096 Jun 28 10:30 file.txt
drwxr-xr-x  2 user user  4096 Jun 28 11:22 Documents

$ ls -lh
-rw-r--r-- 1 user user  4.2K Jun 28 10:30 file.txt
drwxr-xr-x 2 user user  4.0K Jun 28 11:22 Documents
```

#### Understanding ls -l Output
```
-rw-r--r-- 1 user user 4096 Jun 28 10:30 file.txt
│││││││││  │ │    │    │    │  │  │    │
Permissions │ │    │    │    │  │  │    └─ Filename
            │ │    │    │    │  │  └────── Time
            │ │    │    │    │  └───────── Date
            │ │    │    │    └──────────── Month
            │ │    │    └─────────────────── File size
            │ │    └──────────────────────── Group
            │ └───────────────────────────── Owner
            └─────────────────────────────── Link count
```

---
## Pipe (|)
 It is a operator ,used to link multiple independent files that connects the stout of one command to stdin of another.
 #### Example
 ```bash
 $ ls -la /etc | less
```
Note : It lists all files (including hidden ones) in the /etc directory with detailed information and displays the output one page at a time so it's easy to read.
___
## tee
It helps to split the output in two direction , one is to stdout and another to a specific file.
#### Example
```bash
 $ ls | tee peanut.txt
```
Note - it forward the output of ls to peanut.txt file.
___
## touch 
It is used to creat new file and change file timestamps.
### Creating file 
#### Example
```bash
 $ touch file.txt
```
you can also create multiple files at once .
```bash
 $ touch file1.txt file 2.txt file3.log
```
### Changing timestamps 
#### Example
```bash
# Checking original timestamp
 $ ls -l linuxfile
# Updating timestamp
 $ touch linuxfile
# Checking new timestamp
 $ ls -l linuxfile
```
### Advance timestamp control
1. -r - allow to change the timestamp of a file in match of another file.
#### Example
```bash
 $ touch -r file1.txt file2.txt
```
2. -d - allow to set the timestamp to a specific date and time.
#### Example
```bash
 $ touch -r file1.txt file2.txt
```
---
### file
In linux, filename doesn't represent the content of file.So,file command is used to do the same.
#### Example
```bash
 $ file file.txt
 file.txt: ASCII text, with no line terminators
```
---
## cat 
It is used to read the content  of a file.
### Catenating 
#### Example
```bash
 $ cat file1.txt file2.txt
```
its show the content of file on terminal in same given order.
### Redirection
#### Example
```bash
 $ cat > file2.txt
```
Now,type the text in terminal and press ctrl + D ,if file2.txt doesn't exist ,it will creat a one.
### Command options
  1. -n : numbers all the output lines, starting from 1
  2. -b : numbers only non- empty output lines
---
## less
This command allow user to read and navigate through the file, page by page in page format .
### Navigation and Controls
1) Arrows and pages key - ⬅️ <kbd>←</kbd>➡️ <kbd>→</kbd>⬆️ <kbd>↑</kbd>⬇️ <kbd>↓</kbd> to navigate through the file line by line or page by page.
2) Go to start - [Press g] to move directly to the beginning of the text file.
3) Go to end - [Press G] to jump to end of the file.
4) Help menu - While inside less, [Press h]
5) Quiting less - [Press q]
---
## history
This command keeps a recorrd of all of your recent used command.
#### Example
```bash
$ history
1  history
    2  cd ..
    3  cd ~
    4  ls
    5  cat file.txt
    6  history
```
1) !! shortcut - It is used to use your most recent or previous one used command.
2)  Clearing history - $ history -c
3)  Writing to file - $ history -w
---
## mkdir - Make Directory
Create new directories

### Syntax
```bash
mkdir dirname               # Create single directory
mkdir -p path/to/dir        # Create nested directories (with parents)
mkdir dir1 dir2 dir3        # Create multiple directories
```

#### Examples
```bash
$ mkdir Documents
$ ls -l
drwxr-xr-x 2 user user 4096 Jun 28 12:00 Documents

$ mkdir -p projects/python/scripts
$ cd projects/python/scripts
$ pwd
/home/user/projects/python/scripts

$ mkdir folder1 folder2 folder3
$ ls
folder1  folder2  folder3
```

### Common Usage
```bash
# Create project structure
mkdir -p myproject/{src,tests,docs,config}

# Verify
ls -la myproject/
```

---

## rm - Remove Files
Delete files and directories

### Syntax
```bash
rm filename                 # Remove file
rm file1 file2              # Remove multiple files
rm -r dirname               # Remove directory (recursive)
rm -f filename              # Force remove (no confirmation)
rm -rf dirname              # Force remove directory (dangerous!)
```

#### Examples
```bash
# Remove single file
$ rm test.txt
$ ls
Documents  file.txt

# Remove multiple files
$ rm file1.txt file2.txt
$ ls
Documents

# Remove directory (with contents)
$ rm -r Documents
$ ls
# Remove empty directory
$ rmdir Downloads

# Force remove
$ rm -f important.txt
```

### ⚠️ WARNING - Dangerous Commands
```bash
rm -rf /                    # ❌ NEVER! Deletes entire system
rm -rf ~/*                  # ❌ NEVER! Deletes home directory
rm -rf *                    # ⚠️ CAREFUL! Deletes everything in current dir
```

### Safe Practices
```bash
# List before deleting
ls -la | grep "pattern"
rm matching-files

# Use -i for confirmation
rm -i filename              # Asks before deleting

# Dry run (preview)
ls -la | grep "old"         # See what would be deleted
```

---

## cp - Copy Files
Copy files and directories

### Syntax
```bash
cp source destination       # Copy file
cp -r source_dir dest_dir   # Copy directory (recursive)
cp file1 file2 dest/        # Copy multiple files to directory
cp -v source dest           # Verbose (show what's being copied)
```

#### Examples
```bash
# Copy single file
$ cp notes.txt backup.txt
$ ls
backup.txt  notes.txt

# Copy to different directory
$ cp notes.txt Documents/
$ ls Documents/
notes.txt

# Copy directory
$ cp -r project1 project1_backup
$ ls
project1  project1_backup

# Copy multiple files
$ cp *.txt Documents/
$ ls Documents/
file1.txt  file2.txt  file3.txt

# Verbose output
$ cp -v file.txt file_copy.txt
'file.txt' -> 'file_copy.txt'
```

### Common Patterns
```bash
# Backup before modifying
cp config.json config.json.bak

# Copy to backup location
cp important.txt ~/backups/

# Copy entire project
cp -r myproject ~/backup/myproject_backup
```
### Handling file overwrites
By default, cp will overwrites a file at the destination
 1) -i - prompts for confirmation, prevent unwanted data loss
  ```bash
  $ cp -i km file.txt
  ```
2) -f - for to force an overwrite
  ```bash
   $ cp -f km file.txt
  ```

### Preserving file attribute 
To make exact replica of original file with same content,meta data etc.,use -p
 ```bash
   $ cp -p km file.txt
  ```
---

## mv - Move and Rename Files
Move files/directories or rename them

### Syntax
```bash
mv source destination       # Move file or directory
mv oldname newname          # Rename file or directory
mv file1 file2 dest/        # Move multiple files to directory
mv -v source dest           # Verbose output
```

### Examples
```bash
# Rename file
$ mv notes.txt my_notes.txt
$ ls
my_notes.txt

# Move file to directory
$ mv my_notes.txt Documents/
$ ls
Documents
$ ls Documents/
my_notes.txt

# Move and rename at once
$ mv old_name.txt Documents/new_name.txt
$ ls Documents/
new_name.txt

# Move directory
$ mv project1 Documents/
$ ls Documents/
project1

# Move multiple files
$ mv *.txt Documents/
$ ls Documents/
file1.txt  file2.txt  file3.txt

# Verbose output
$ mv -v important.txt backup/
'important.txt' -> 'backup/important.txt'
```
### Important options for the mv command
By default, mv will overwrites a existing file with same name 
1) -i - prompt for confirmation
2) -b - backup your older version with a rename having [~] in its name

### Difference Between cp and mv
```bash
cp file.txt copy.txt        # file.txt still exists
# Result: file.txt and copy.txt both exist

mv file.txt renamed.txt     # Original name removed
# Result: only renamed.txt exists
```

---

## Quick Reference Table

| Command | Purpose | Common Options |
|---------|---------|-----------------|
| `pwd` | Show current directory | None |
| `cd` | Change directory | `..`, `~`, `-` |
| `ls` | List files | `-l`, `-a`, `-lh`, `-R` |
| `mkdir` | Create directory | `-p` (parents) |
| `rm` | Delete file | `-r` (recursive), `-f` (force) |
| `cp` | Copy file | `-r` (recursive), `-v` (verbose) |
| `mv` | Move/rename | `-v` (verbose) |

---

## Common Workflows

### Navigate and Explore
```bash
pwd                         # Know where you are
ls -la                      # See all files
cd Documents                # Go to Documents
ls                          # List contents
cd ..                       # Go back
pwd                         # Confirm location
```

### Create and Organize
```bash
mkdir projects              # Create folder
cd projects                 # Enter folder
mkdir python java           # Create subfolders
ls                          # Verify
```

### Copy and Backup
```bash
cp important.txt important.txt.bak      # Backup
ls -la                                  # Verify backup exists
```

### Organize Files
```bash
mkdir archive               # Create archive folder
mv old_file.txt archive/    # Move old files
ls                          # Verify move
```

### Rename Files
```bash
ls
mv report_draft.pdf report_final.pdf
ls
```

---

## Practice Exercises

- [ ] Use `pwd` to find your current directory
- [ ] Create a folder: `mkdir my_project`
- [ ] Navigate into it: `cd my_project`
- [ ] Create subfolders: `mkdir src data output`
- [ ] List with details: `ls -la`
- [ ] Create a file: `echo "test" > file.txt`
- [ ] Copy file: `cp file.txt backup.txt`
- [ ] Rename file: `mv backup.txt file_backup.txt`
- [ ] Move file: `mv file_backup.txt data/`
- [ ] List moved file: `ls data/`
- [ ] Go back: `cd ..`
- [ ] Navigate to nested dir: `cd my_project/data`
- [ ] Remove file: `rm file_backup.txt`
- [ ] Go back to start: `cd`

---

## Tips & Tricks

### Tab Completion
```bash
cd Do[TAB]          # Autocompletes to Documents
ls fi[TAB]          # Autocompletes to file.txt
```

### Wildcard Patterns
```bash
ls *.txt            # All .txt files
ls file*            # All files starting with "file"
cp *.py backup/     # Copy all Python files
rm *.log            # Remove all log files
```

### History Navigation
```bash
cd /var/log         # Go to directory
cd -                # Back to previous
cd -                # Back to /var/log again
```

### Create and Navigate Together
```bash
mkdir newdir && cd newdir   # Create and enter in one command
```

---

## Common Mistakes

❌ **Forgetting -r with rm or cp**
```bash
rm -r dirname       # Correct - recursive
rm dirname          # Wrong - error "Is a directory"
```

❌ **Overwriting files with cp**
```bash
cp file.txt backup.txt      # If backup.txt exists, it's overwritten
cp -i file.txt backup.txt   # Better - asks before overwriting
```

❌ **Wrong path separator**
```bash
cd Documents        # Correct - subdirectory of current
cd ~/Documents      # Correct - home + Documents
cd /Documents       # Wrong - looks in root /Documents
```

---

**Phase:** Week 1  
**Day:** 7  
**Topic:** Navigation & File Management Commands  
**Commands:** pwd, cd, ls, mkdir, rm, cp, mv
