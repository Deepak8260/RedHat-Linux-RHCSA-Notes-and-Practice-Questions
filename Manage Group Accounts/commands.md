# 🐧 Linux User and Group Management – Beginner’s Guide

Managing **users, groups, and permissions** is one of the most important jobs of a Linux administrator. These commands help you **control who can access the system and what they can do**.

---

## 👤 User and Group Management

### 1. `useradd` → Create a New User

This command creates a **new user account**. It also creates a personal group for them (called the **primary group**).

```bash
useradd sachin
```

📌 *How it works:*

* Adds a new entry in `/etc/passwd` and `/etc/shadow`.
* Runs silently — no output if it succeeds.

---

### 2. `groupadd` → Create a New Group

Groups are used to **organize users** and manage permissions together.

```bash
groupadd IBM_Group
```

📌 *How it works:*

* Creates a new entry in `/etc/group`.

---

### 3. `passwd` → Set or Change a Password

This command sets or updates a user’s password.

```bash
passwd sachin
```

📌 *How it works:*

* System asks you to type the new password twice.
* Password is stored as an encrypted hash in `/etc/shadow`.

---

### 4. `gpasswd` → Manage Group Members

This is a **multi-purpose command** for adding/removing users in groups or setting group admins.

* **Add a user to group (`-a`)**

  ```bash
  gpasswd -a ajay IBM_Group
  ```

  ✅ Output: `Adding user ajay to group IBM_Group`

* **Remove a user from group (`-d`)**

  ```bash
  gpasswd -d salman IBM_Group
  ```

  ✅ Output: `Removing user salman from group IBM_Group`

* **Add multiple users (`-M`)**

  ```bash
  gpasswd -M ajay,salman,virat IBM_Group
  ```

  ⚠️ Be careful — this **overwrites existing members**.

* **Set group administrator (`-A`)**

  ```bash
  gpasswd -A ajay IBM_Group
  ```

  ✅ Ajay can now add/remove members. Info is stored in `/etc/gshadow`.

---

### 5. `userdel` → Delete a User

Removes a user account. Often used with `-r` to also delete their files.

```bash
userdel -r harry
```

📌 *How it works:*

* `-r` removes home directory + files along with the account.

---

### 6. `groupdel` → Delete a Group

Deletes only the **group entry**. Users stay on the system but lose membership in that group.

```bash
groupdel IBM_Group
```

---

## 🔎 Verifying User and Group Information

### 1. `grep` → Search for User/Group in System Files

Useful to check if a user or group exists.

```bash
grep sachin /etc/passwd
```

📌 *How it works:*

* Shows the line with `sachin` → includes UID, GID, home directory, etc.

---

### 2. `ls -ld` → Check Ownership of a Directory

Displays permissions, owner, and group of a directory.

```bash
ls -ld Chennai
```

📌 *How it works:*

* By default: `root root` (user owner = root, group owner = root).

---

### 3. `whoami` → See Current User

Quickly check which account you’re logged in as.

```bash
whoami
```

📌 Prints your **effective username**. Handy after switching users with `su`.

---

## 📂 File and Directory Ownership

### 1. `chown` → Change File/Directory Owner

```bash
chown Mahindra Chennai
```

📌 Now `Chennai` belongs to user **Mahindra**.

---

### 2. `chgrp` → Change Group Ownership

```bash
chgrp CSK_Group Chennai
```

📌 Now group ownership is **CSK\_Group**.

---

### 3. `chown user:group` → Change Both Owner and Group

```bash
chown rohit:MI_Group Mumbai
```

📌 Owner = **rohit**, Group = **MI\_Group**.

---

### 4. `chmod` → Change File/Directory Permissions

```bash
chmod 750 Chennai
```

📌 Meaning of `750`:

* `7` → Owner: read + write + execute
* `5` → Group: read + execute
* `0` → Others: no permissions

---