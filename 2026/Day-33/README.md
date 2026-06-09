# PRACTICE LAB
# Day 33 – Login Process, systemd, Shells and Initialization Files
## June 9th, 2026

> Based on Class Notes and Slides by NIT Academy

---

# Objective

The objective of this lab is to learn how to properly take backups of important Linux configuration files before making any changes.

## Golden Rule

Before you:

- Modify a file
- Edit a file
- Delete a file
- Rename a file
- Change a configuration

Always take a backup first.

```text
Backup First, Change Later
```

---

# Table of Contents

| Task | Title |
|------|--------|
| 1 | Identify Critical Configuration Files |
| 2 | Create a Backup |
| 3 | Verify the Backup Using diff |
| 4 | Verify the Backup Using md5sum |
| 5 | Lab Summary |
| 6 | Review Questions |

---

# Task 1 - Identify Critical Configuration Files

## Objective

Identify important Linux system configuration files.

### Run

~~~bash
ls -l /etc/profile
ls -l /etc/bashrc
~~~

### Notes

These are important Linux configuration files:

| File | Purpose |
|--------|----------|
| `/etc/profile` | Global Login Shell Configuration |
| `/etc/bashrc` | Global Interactive Shell Configuration |

Any changes made to these files can affect:

- All users
- All login shells
- System-wide behavior

### Questions

1. Are these files owned by root?
2. Why are these files considered important?
3. Who should normally modify these files?

---

# Task 2 - Create a Backup

## Objective

Create a backup copy of a configuration file before making changes.

### Linux Copy Syntax

~~~text
cp -r [original_file] [backup_file]
~~~

### Run

~~~bash
cd /etc
pwd
cp -r profile profile_bak
ls
~~~

### Verify

You should see:

~~~text
profile
profile_bak
~~~

### Notes

The command:

~~~bash
cp -r profile profile_bak
~~~

creates an exact duplicate of the original file.

### Questions

1. Why should backups be taken before editing files?
2. What could happen if a configuration file is accidentally damaged?
3. What does the `cp` command do?

---

# Task 3 - Verify the Backup Using diff

## Objective

Verify that the backup file contains the same contents as the original file.

### Test #1 - Using diff

### Run

~~~bash
diff profile profile_bak
~~~

### Expected Result

~~~text
(No output)
~~~

### Notes

If `diff` produces no output:

```text
The files are identical.
```

If differences exist, `diff` will display them.

### Questions

1. What does the `diff` command compare?
2. Why is no output considered a good result?

---

# Task 4 - Verify the Backup Using md5sum

## Objective

Use MD5 checksums to confirm that the backup file is identical to the original file.

### Test #2 - Using md5sum

### Run

~~~bash
md5sum profile
md5sum profile_bak
~~~

### Example Output

~~~text
d41d8cd98f00b204e9800998ecf8427e  profile
d41d8cd98f00b204e9800998ecf8427e  profile_bak
~~~

### Notes

The MD5 hash value acts like a fingerprint.

If both files have the same MD5 value:

```text
The files are identical.
```

If the values are different:

```text
The files are different.
```

### Questions

1. What is an MD5 hash?
2. Why is md5sum considered a stronger verification method than simply looking at filenames?
3. What does it mean if the two MD5 values are different?

---

# Lab Summary

You have successfully:

- Identified critical Linux configuration files.
- Created a backup of a configuration file.
- Verified the backup using `diff`.
- Verified the backup using `md5sum`.
- Learned why backups are important before making changes.

### Important Lesson

Before changing any Linux configuration file:

~~~text
1. Create a Backup
2. Verify the Backup
3. Make the Change
4. Test the Change
~~~

---

# Review Questions

1. What is the purpose of `/etc/profile`?
2. What is the purpose of `/etc/bashrc`?
3. What command is used to create a backup?
4. Why should backups be created before making changes?
5. What does the `diff` command do?
6. What does the `md5sum` command do?
7. What does it mean when two files have the same MD5 hash?
8. Which verification method is stronger: `diff` or `md5sum`?
9. Why is backup verification important?
10. What is the Golden Rule of Linux Administration?

### Golden Rule Answer

~~~text
Backup First, Change Later
~~~

---

# End of Lab

🐧 Happy Learning Linux Administration!
