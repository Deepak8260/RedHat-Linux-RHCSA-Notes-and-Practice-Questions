# Linux User Management Commands

### User Account Creation and Deletion

* **`useradd`**: Creates a new user account on the system.

  ```bash
  useradd sachin
  ```

  *Output:*
  (No output on a successful execution.)

  ➡️ *Tip:* After creating a user, you can verify by:

  ```bash
  grep sachin /etc/passwd
  ```

  It should show Sachin’s entry.

---

* **`passwd`**: Sets or changes a user's password.

  ```bash
  passwd sachin
  ```

  *Output:*

  ```bash
  Changing password for user sachin.
  New password:
  Retype new password:
  passwd: all authentication tokens updated successfully.
  ```

  💡 *Note:* If you enter mismatched passwords, it will ask you to retry.

---

* **`userdel`**: Deletes a user account. Using the **-r** option also removes the user's home directory.

  ```bash
  userdel -r harry
  ```

  *Output:*
  (No output on a successful execution.)

  👉 *Check after deletion:*

  ```bash
  ls /home
  ```

  You should no longer see Harry’s home directory.

---

### Viewing User Information

* **`grep /etc/passwd`**: Searches the `/etc/passwd` file to display a user's account properties.

  ```bash
  grep sachin /etc/passwd
  ```

  *Output:*

  ```bash
  sachin:x:1001:1001::/home/sachin:/bin/bash
  ```

  🔎 *Breakdown:*

  * `sachin` → Username
  * `x` → Password is stored in `/etc/shadow`
  * `1001` → UID (User ID)
  * `1001` → GID (Group ID)
  * `/home/sachin` → Home directory
  * `/bin/bash` → Default shell

---

* **`grep /etc/shadow`**: Displays a user's encrypted password and password aging information from the secure `/etc/shadow` file.

  ```bash
  grep sachin /etc/shadow
  ```

  *Output:*

  ```bash
  sachin:$6$qg3B...:19299:0:99999:7::1
  ```

  💡 *Note:* You need **root privileges** to view this file.

---

* **`whoami`**: Prints the name of the current user.

  ```bash
  whoami
  ```

  *Output:*

  ```bash
  root
  ```

  👉 *Try this:* Switch user with `su sachin` and run `whoami` again.

---

### Session and Account Control

* **`su`**: Switches to another user account.

  ```bash
  su sachin
  ```

  *Output:*

  ```bash
  [sachin@vbox ~]$
  ```

  💡 *Note:* Use `su - sachin` for a full login shell with environment variables.

---

* **`exit`**: Logs out of the current shell or user session.

  ```bash
  exit
  ```

  *Output:*

  ```
  logout
  ```

  👉 *Interactive Flow:*

  * Login as root
  * Switch to user `sachin`
  * Type `exit` → You’ll be back to root

---

### `usermod` - Modify a User Account

The `usermod` command is used to modify an existing user's properties. The output for these commands is shown in the format of a user's `/etc/passwd` entry.

The starting user entry is:

```
deepak:x:1001:1001:actor:/home/deepak:/bin/bash
```

---

**a. Change Login Name (`-l`)**
  *Definition:* Changes a user's login name.

 ```bash
usermod -l kumar deepak
```

*Output:*
`kumar:x:1001:1001:actor:/home/deepak:/bin/bash`

👉 *Tip:* The home directory remains `/home/deepak` unless you also use `-d`.

---

**b. Change User ID (`-u`)**
  *Definition:* Modifies a user's unique ID number.

```bash
usermod -u 5555 deepak
```

*Output:*
`deepak:x:5555:1001:actor:/home/deepak:/bin/bash`

💡 *Note:* UID must be unique.

---

**c. Add or Change a Comment (`-c`)**
  *Definition:* Adds or changes a user's full name or comment.

```bash
usermod -c "Software Developer" deepak
```

*Output:*
`deepak:x:1001:1001:Software Developer:/home/deepak:/bin/bash`

👉 This “comment” often appears in GUI login prompts or `finger` command outputs.

---

**d. Change Home Directory (`-d`)**
  *Definition:* Changes the path to a user's home directory.

```bash
usermod -d /home/developer deepak
```

*Output:*
`deepak:x:1001:1001:actor:/home/developer:/bin/bash`

💡 Use `-m` along with `-d` to move existing files to the new directory.

---

**e. Change Login Shell (`-s`)**
  *Definition:* Modifies a user's default shell program.

```bash
usermod -s /sbin/nologin deepak
```

*Output:*
`deepak:x:1001:1001:actor:/home/deepak:/sbin/nologin`

👉 Prevents login access while keeping files intact.

---

**f. Lock a User Account (`-L`)**
  *Definition:* Locks a user's password, preventing them from logging in.

```bash
usermod -L deepak
```

*Output:*
`deepak:x:1001:1001:actor:/home/deepak:/bin/bash`

💡 This adds a `!` in front of the password hash inside `/etc/shadow`.

---

**g. Unlock a User Account (`-U`)**
  *Definition:* Unlocks a user's password.

```bash
usermod -U deepak
```

*Output:*
`deepak:x:1001:1001:actor:/home/deepak:/bin/bash`

---

**h. Set Account Expiry Date (`-e`)**
  *Definition:* Sets a date when the user's account will expire.

```bash
usermod -e 2025-09-30 deepak
```

*Output:*
`deepak:x:1001:1001:actor:/home/deepak:/bin/bash`

👉 After expiry, the account cannot be used to log in.

---

### Other Commands

**a. `chage`**: Interactively changes a user's password aging information.

  ```bash
  chage user1
  ```

  *Output:*

  ```
  Changing the aging information for user1
  Minimum number of days between password change [0]:
  Maximum number of days between password change [99999]:
  Number of days of warning before password expires [7]:
  ```

  💡 Use `chage -l user1` to view settings without changing them.

---

**b. `vim /etc/login.defs`**: Opens the system-wide policy file that sets default values for all new users.

  ```bash
  vim /etc/login.defs
  ```

  *Output:*
  (This command opens the file in the terminal for editing.)

  ```
  # /etc/login.defs - Useradd defaults

  PASS_MAX_DAYS   99999
  PASS_MIN_DAYS   0
  ...
  ```

  👉 These defaults apply when you create a new user with `useradd`.

---