# **Regular Expressions and File Searching**

Your system administrator has asked you to complete the following tasks on your Linux system using tools for searching and filtering files and content.

---

### **Part 1: Searching Inside File Content with `grep`**

1. Search for the word `secure` inside the file `/home/ct.txt` and display all matching lines.

2. Search for the name `Karan` in the files `/etc/passwd`, `/etc/group`, and `/home/ct.txt` and show where it appears.
3. Search for the word `Linux` inside `/home/ct.txt` without considering case sensitivity.
4. Display the line numbers along with the matching lines when searching for the word `Linux` inside `/etc/passwd`.
5. Count how many times the word `Linux` appears in `/home/ct.txt`.
6. Display only the filenames that contain the word `Karan` when searching in `/etc/passwd` and `/etc/group`.
7. Display only the filenames that do **not** contain the word `Karan` when searching in `/etc/passwd`, `/etc/group`, and `/home/ct.txt`.
8. Display all lines from `/home/ct.txt` that do **not** contain the word `secure`.
9. Display lines from `/home/ct.txt` that begin with the word `Linux`.
10. Display lines from `/home/ct.txt` that end with the word `OS`.
11. Search recursively for the word `secure` inside all files under the `/etc` directory.
12. Save the results of searching for the word `Linux` in `/home/ct.txt` into a file called `result.txt`. Then append the results of searching for the word `Windows` in the same file to `result.txt`.

---

### **Part 2: Locating Files and Directories with `find`**

13. Find the file named `ct.txt` under the `/home` directory and display its full path.

14. List all files and directories under `/data` that are owned by the user `amir`.
15. List all files and directories in the entire system that belong to the group `TataGroup`.
16. Find all files larger than 100 MB under the `/usr` directory.
17. Find all files between 50 MB and 100 MB in size under the `/usr` directory.
18. Search the entire system for files that have permission `777`.
19. Search the entire system for files with SUID (`4755`), SGID (`2755`), or Sticky Bit (`1755`) permissions.
20. Find all files owned by user `amir` in `/data` and delete them in a single command.

---

### **Part 3: Quick File Inspection with `head`, `tail`, and `wc`**

21. Display the first 10 lines of the `/etc/passwd` file.

22. Display only the first 5 lines of the `/etc/passwd` file.
23. Display the last 10 lines of the `/etc/passwd` file.
24. Display only the last 5 lines of the `/etc/passwd` file.
25. Display the total number of lines, words, and characters in the file `/home/ct.txt`.
26. Display only the number of lines in the file `/home/ct.txt`.
27. Display only the number of words in the file `/home/ct.txt`.
28. Display only the number of characters in the file `/home/ct.txt`.

---
