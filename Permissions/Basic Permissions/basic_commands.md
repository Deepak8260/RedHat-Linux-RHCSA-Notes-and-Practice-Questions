# Linux File Permissions – Beginner to Advanced (Basics)

---

## 1. Introduction to Permissions

In Linux, everything is treated as a **file** — whether it’s a text file, a directory, or even a device.
Permissions are rules that control **who** can do **what** with those files and directories.

Think of it like a house:

* The **owner** (you) can open doors, rearrange furniture, or lock it.
* Your **family group** (people living with you) may also have some access.
* **Visitors** (others) may only be allowed to enter the living room but not the bedroom.

Linux uses **permissions** to decide this access.

There are **three layers of permissions**:

1. **Basic Permissions** – Everyday rules for users, groups, and others.
2. **Access Control Lists (ACLs)** – More advanced, fine-grained control (later topic).
3. **Special Permissions** – Like sticky bit, SUID, SGID (later topic).

This guide focuses on **basic permissions**.

---

## 2. Basic Permissions: The Three User Categories

Every file/directory in Linux has permissions for **three groups of people**:

1. **User (u) or Owner**

   * The person who created the file or directory.
   * Example: If **Rohit** creates a file, he is the owner.

2. **Group (g) or Group Owner**

   * A group of users who share common permissions.
   * Example: A group named **MI Group**. All members of this group get the same permissions.

3. **Others (o)**

   * Everyone else who is **not the owner** and **not in the group**.
   * Example: **Virat** and **Mahendra** if they don’t belong to MI Group.

👉 So every file/directory has **3 different sets of permissions**:

* One for **User**
* One for **Group**
* One for **Others**

---

## 3. Permission Types: Read, Write, and Execute

Each of these three categories (User, Group, Others) can have **three types of permissions**:

1. **Read (r)**

   * For files → allows opening and reading the file.
   * For directories → allows listing the files inside.

   📌 Example:

   * If you have `r` on `notes.txt`, you can open and view the contents.
   * If you have `r` on `/documents/`, you can list files inside it.

2. **Write (w)**

   * For files → allows modifying or deleting the file.
   * For directories → allows creating, deleting, or renaming files inside.

   📌 Example:

   * If you have `w` on `notes.txt`, you can change its text.
   * If you have `w` on `/documents/`, you can create or delete files in that directory.

3. **Execute (x)**

   * For files → allows executing (running) the file if it’s a script or program.
   * For directories → allows entering the directory with `cd`.

   📌 Example:

   * If you have `x` on `run.sh`, you can execute the script.
   * If you have `x` on `/documents/`, you can enter the directory.

👉 Together, these three permissions (`r`, `w`, `x`) control access to files and directories.

---

## 4. Permission Syntax and Description

When you run the `ls -l` command in a terminal, you get a long listing format that shows details about files and directories. For example:

```
drwxr-xr-x. 2 rohit mi_group 6 Aug 25 21:09 mumbai
```

This may look confusing at first, but it follows a structured format. Let’s carefully break it down step by step:

| Part                | Example    | Meaning                                                                                                                                                                                                                                 |
| ------------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1st character**   | `d`        | Indicates **file type**. Possible values are: <br> - `d` → directory <br> - `-` → regular file <br> - `l` → symbolic link <br> - `c` → character device file <br> - `b` → block device file <br> - `p` → named pipe <br> - `s` → socket |
| **2–4 characters**  | `rwx`      | **User (Owner) permissions**. In this case, the owner `rohit` has: <br> - `r` → read permission <br> - `w` → write permission <br> - `x` → execute permission                                                                           |
| **5–7 characters**  | `r-x`      | **Group permissions**. Here, members of `mi_group` have: <br> - `r` → read permission <br> - `-` → no write permission <br> - `x` → execute permission                                                                                  |
| **8–10 characters** | `r-x`      | **Others (world) permissions**. This applies to everyone else on the system. They have: <br> - `r` → read permission <br> - `-` → no write permission <br> - `x` → execute permission                                                   |
| **`.` (dot)**       | `.`        | Indicates whether **Access Control Lists (ACLs)** are applied. <br> - `.` means no ACLs <br> - `+` means ACLs are present                                                                                                               |
| **2**               | `2`        | **Number of links** (hard links). <br> For directories, this count starts at 2: one for the directory itself (`.`), and one for its parent (`..`).                                                                                      |
| **rohit**           | `rohit`    | **Owner name**. The user who owns the file/directory.                                                                                                                                                                                   |
| **mi\_group**       | `mi_group` | **Group name**. The group that owns the file/directory.                                                                                                                                                                                 |
| **6**               | `6`        | **File size in bytes**. For a directory, this number often represents metadata size, not contents.                                                                                                                                      |
| **Aug 25 21:09**    | Date/time  | **Last modified timestamp**. Shows when the file/directory was last changed.                                                                                                                                                            |
| **mumbai**          | `mumbai`   | **File or directory name**. In this case, the name of the directory.                                                                                                                                                                    |

### Important Notes on Permissions:

1. Each set of three characters (`rwx`) corresponds to **read (r)**, **write (w)**, and **execute (x)**.
2. A dash (`-`) means the permission is **not granted** or **deny**.

   * Example: `r-x` means read and execute are allowed, but write is denied.
3. **Execute permission** has different meanings:

   * For **files** → allows the file to be run as a program/script.
   * For **directories** → allows entering the directory (using `cd`) and accessing files inside it.


👉 A dash `-` in place of `r`, `w`, or `x` means permission is denied.

---

## 5. Commands and Outputs

### 5.1 Viewing Permissions

* `ls -l <file_name>` → shows permissions of a file.
* `ls -ld <directory_name>` → shows permissions of a directory itself.

📌 Examples:

* File →

  ```
  -rw-r--r--. 1 rohit mi_group 6 Aug 25 21:09 my_team.txt
  ```

  * Owner: read, write
  * Group: read only
  * Others: read only

* Directory →

  ```
  drwxr-xr-x. 2 rohit mi_group 6 Aug 25 21:09 mumbai
  ```

  * Owner: full access
  * Group: read + execute
  * Others: read + execute

---

### 5.2 Changing Permissions with `chmod` (Symbolic Method)

**Syntax:**

```
chmod [u/g/o/a][+/-/=][r/w/x] <file_name>
```

* **u** = user (owner)

* **g** = group

* **o** = others

* **a** = all (ugo together)

* **+** = add permission

* **-** = remove permission

* **=** = set/overwrite permission

📌 Examples:

* `chmod o-rx mumbai` → remove read & execute from others.
* `chmod g+w mumbai` → add write permission for group.
* `chmod ugo+rx mumbai` → give read & execute to all.
* `chmod ugo-rwx mumbai` → remove all permissions for all.
* `chmod ug=rw mumbai` → set user & group to read & write only.

---

### 5.3 Changing Permissions with `chmod` (Numerical Method)

Each permission has a number:

* `r = 4`
* `w = 2`
* `x = 1`
* `- = 0`

👉 Add them to calculate:

* `rwx = 4+2+1 = 7`
* `rw- = 4+2 = 6`
* `r-x = 4+1 = 5`
* `r-- = 4`

**Syntax:**

```
chmod <number> <file_name>
```

📌 Examples:

* `chmod 750 mumbai`

  * User = 7 (rwx)
  * Group = 5 (r-x)
  * Others = 0 (---)

* `chmod 666 mumbai` → everyone gets read & write only.

* `chmod 777 mumbai` → everyone gets full permissions.

---

## 6. Other Details

* **Link count:** Number of hard links. Files = 1, Directories = start at 2.
* **Owner & group:** Can be changed with `chown` and `chgrp`.
* **File size:** In bytes; use `du` for disk usage.
* **Date/time:** Shows last modification.
* **Dot or plus:** `.` means no ACL, `+` means ACL applied.

---