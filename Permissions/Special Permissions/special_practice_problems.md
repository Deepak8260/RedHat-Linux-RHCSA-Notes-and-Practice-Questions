# **Linux Special Permissions**
---

Your system administrator has asked you to perform the following tasks related to special permissions. Complete each step carefully.

---

### **Part 1: Set Group ID (SGID)**

1. A directory `/TCS` exists. Change the group ownership of this directory to `TataGroup`.
2. Set the **SGID** permission on `/TCS` so that any files created inside automatically inherit the group ownership of the directory.
3. Verify that a new file created inside `/TCS` by user `user1` has group ownership `TataGroup`.
4. Remove the **SGID** permission from `/TCS`.

---

### **Part 2: Set User ID (SUID)**

5. Locate the full path of the command `nmtui`.
6. Set the **SUID** permission on the `nmtui` binary so that it always runs with the file owner’s privileges.
7. Verify that a normal user (such as `virat`) can run `nmtui` with elevated privileges.
8. Remove the **SUID** permission from the `nmtui` binary.

---

### **Part 3: Numerical Representation of Special Permissions**

9. Set the permissions on the file `/opt/demo_file` to include **SUID** and **SGID** using the **numeric method**.
10. Change the permissions on `/opt/demo_file` to include only the **Sticky Bit** using the **numeric method**.
11. Remove all special permissions from `/opt/demo_file` using the numeric method.

---

### **Part 4: Hidden Files & Home Directory Example**

12. Move user `rahul`’s home directory to `/home2/rahul`.
13. Ensure that `/home2/rahul` has the correct ownership and permissions for user `rahul`.
14. Copy all **hidden files** from `/home/rahul` to `/home2/rahul` so that the user’s environment works properly.
15. Verify that user `rahul` does not face any shell errors after logging in with the new home directory.

---
