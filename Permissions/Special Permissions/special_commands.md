# **Special Permissions**

---

## Introduction: Why Special Permissions Are Needed

There are three types of permissions – **Basic**, **ACL**, and **Special**.
**Special Permissions** are meant for **executable files** and **directories**. They include:

1. **Set User ID (SUID)**
2. **Set Group ID (SGID)**
3. **Sticky Bit**

These permissions give extra control over how files and directories behave. They’re like “special rules” on top of normal permissions to control ownership or privilege in specific situations.

---

## Part 1: Set Group ID (SGID)

### **Concept**

The **SGID** permission on a directory makes sure that any file or folder created inside it automatically takes the **group ownership** of the parent directory instead of the group of the user creating it.

This is useful when many users work together in the same directory and you want all files to stay in one group.

### **Description**

Normally, when a user creates a file inside a directory, the file gets the **user’s primary group**. With SGID, the file instead gets the **directory’s group**, making teamwork smoother.
It’s like saying, “Anything born here belongs to this family, not to outsiders.”

### **Commands & Examples**

1. **Preparation:**

   * Create a directory (e.g., `TCS`).
   * Create a group (e.g., `TataGroup`).
   * Change the directory’s group ownership to `TataGroup`.
   * Create users `user1`, `user2`, and `user3`.

2. **Initial Behavior (Without SGID):**

   * **Command:** `ls -ld TCS` and then create files inside.
   * **Output:** Files made by `user1` inside `TCS` are owned by `user1` and have the group `user1`.
   * **Meaning:** This is the default rule where the file gets the creator’s group.

3. **Setting SGID:**

   * **Command:** `chmod g+s TCS`
   * **Output:** Permissions now show an `s` in the group’s execute spot (`rwx rws rwx`).

4. **New Behavior (With SGID):**

   * Files created by `user1` now automatically have the group `TataGroup`.
   * This shows SGID is working because group ownership comes from the parent folder.

### **Analogy**

Think of a family surname: a child born into a family automatically gets the family’s surname. SGID works the same way for group ownership.
This extra rule keeps everything consistent inside shared directories.

---

## Part 2: Set User ID (SUID)

### **Concept**

The **SUID** permission on an executable file lets a normal user run it with the **file owner’s permissions** instead of their own.

This is important for commands that need higher privileges but must be usable by non-admin users without giving them the actual password.

### **Description**

Without SUID, normal users cannot run certain system-level programs. With SUID, they temporarily “borrow” the file owner’s (often root’s) permissions only for that program.
It’s like giving someone a guest pass to do one specific action without giving them your full account.

### **Commands & Examples**

1. **Initial Behavior (Without SUID):**

   * A normal user (like `virat`) tries to run a privileged command such as `nmtui` and gets “Permission Denied.”

2. **Finding the Command’s Location:**

   * **Command:** `which nmtui`
   * **Output:** `/usr/bin/nmtui` (or similar).

3. **Setting SUID:**

   * **Command:** `chmod u+s /usr/bin/nmtui`
   * **Output:** Permissions show an `s` in the owner’s execute spot (`rws r-x r-x`).
   * A lowercase `s` means SUID + execute; uppercase `S` means SUID without execute.

4. **New Behavior (With SUID):**

   * Now `virat` runs `nmtui` successfully and can change the hostname without root password.
   * This happens because `nmtui` runs with the file owner’s (root’s) permissions.

### **Analogy**

This is like the “Run as Administrator” option in Windows – you temporarily gain higher rights to run a specific program but not full admin control elsewhere.
It gives power only for that task, keeping the system secure.

---

## Part 3: Numerical Representation of Special Permissions

Special permissions also have **numbers** like normal permissions. A **fourth digit** is added in front:

* **SUID:** `4`
* **SGID:** `2`
* **Sticky Bit:** `1`

### **Commands & Syntax**

* **Setting SUID:** `chmod 4755 <file_name>`
* **Setting SGID:** `chmod 2755 <file_name>`
* **Setting Sticky Bit:** `chmod 1755 <file_name>`

You can **add** numbers to set multiple special permissions at once (e.g., `4` + `2` = `6`).
*Example:* `chmod 6755 <file_name>` sets both SUID and SGID.

**Removing Special Permissions:**
Set the first digit to `0` (e.g., `chmod 0755 <file_name>`).

This numeric method is a shortcut; the symbolic method (`u+s`, `g+s`, `o+t`) works just as well and is easier to read.
So you can pick whichever style makes more sense to you.

---

## Part 4: Hidden Files & Home Directory Example

Sometimes, when moving or changing a user’s home directory, problems appear because of **hidden files**.

### **Observation:**

If the new home directory does not have the hidden files from the old one, the shell may give errors (like missing `.bash_profile`).
These hidden files store important settings for the user’s environment.

### **Solution:**

1. Make sure the new home directory has correct ownership and permissions (e.g., `chown user:user new_home`).
2. Copy all hidden files from the old home to the new one using `cp -a`.

### **Useful Commands:**

* `ls -a` – lists all files, including hidden ones (those starting with a dot).
* `mv .<file_name> <new_name>` – unhides a file by removing the dot at the start.

Copying these hidden files ensures the user’s shell and environment work exactly as before.

---
