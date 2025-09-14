# **Regular Expressions and File Searching**

Regular expressions (often called **Regex**) are patterns used to search and filter text. In Linux, Regex is built into many commands. It lets you quickly find or match specific words, file names, permissions, ownership (user or group), size, and much more without manually checking each file.
Think of it as a very smart “search filter” built right into the command line.

---

## 1. `grep` Command – Searching Inside File Content

### **Concept**

`grep` (Global Regular Expression Print) searches for words or patterns inside files. Instead of opening a file to look for a word, `grep` finds and prints the matching lines for you.
It’s like pressing **Ctrl+F** but from the command line.
### **Commands and How They Work**

1. **Basic Search**

   * `grep secure /home/ct.txt`
   * Looks for the word “secure” in `/home/ct.txt` and shows the whole line where it appears.
   * You can imagine it as using “Ctrl+F” inside a file but from the terminal.

2. **Search Across Multiple Files**

   * `grep Karan /etc/passwd /etc/group /home/ct.txt`
   * Searches for “Karan” in all three files at once.
   * Each result shows which file it came from so you know where it was found.

3. **Case-Insensitive Search**

   * `grep -i Linux /home/ct.txt`
   * Finds “Linux” no matter how it’s written (linux, LINUX, etc.).
   * This is great when you’re unsure about upper or lowercase.

4. **Show Line Numbers**

   * `grep -n Linux /etc/passwd`
   * Shows each matching line along with its line number.
   * This helps you jump to that exact spot in the file.

5. **Count Matches Only**

   * `grep -c Linux /home/ct.txt`
   * Instead of showing lines, it just gives a single number of how many matches it found.
   * Useful for quickly checking how many times something appears.

6. **List Only Filenames With a Match**

   * `grep -l Karan /etc/passwd /etc/group`
   * Shows just the names of the files that contain “Karan” at least once.
   * Handy when you only need to know “which files” without the details.

7. **List Files That Do NOT Contain a Match**

   * `grep -L Karan /etc/passwd /etc/group /home/ct.txt`
   * The uppercase `L` is the opposite of lowercase `l`. It lists files where “Karan” does **not** exist.
   * Good for spotting missing patterns.

8. **Invert the Match (Show Unmatched Lines)**

   * `grep -v secure /home/ct.txt`
   * Shows all lines that do **not** have “secure.”
   * Think of it as filtering out unwanted lines.

9. **Search by Line Position (Start or End)**

   * `grep "^Linux" /home/ct.txt` finds lines that **start** with “Linux.”
   * `grep "OS$" /home/ct.txt` finds lines that **end** with “OS.”
   * The `^` and `$` act like anchors for the beginning or end of a line.

10. **Recursive Search in All Files**

    * `grep -r secure /etc`
    * Searches “secure” inside every file under `/etc` and its subfolders.
    * Very powerful for scanning entire directories.

11. **Redirecting Output to a File**

    * `grep Linux /home/ct.txt > result.txt` overwrites `result.txt` with the results.
    * `grep Windows /home/ct.txt >> result.txt` appends new results to the end of the file.
    * This is how you save your search results to look at later.

---

## 2. `find` Command – Locating Files and Directories

### **Concept**

`find` searches for files and folders by their **name**, **owner**, **group**, **size**, or **permissions**. Instead of opening every folder, you can ask Linux to hunt down what you need.

### **Commands and How They Work**

1. **Search by Name**

   * `find /home -name ct.txt`
   * Starts from `/home` and looks for a file called `ct.txt`.
   * Prints the full path so you know exactly where it is.

2. **Search by User (Owner)**

   * `find /data -user amir`
   * Shows all files and directories owned by the user `amir` in `/data`.
   * Helps track down a particular user’s files.

3. **Search by Group**

   * `find / -group TataGroup`
   * Lists everything that belongs to group `TataGroup` anywhere on the system.
   * Useful in shared environments.

4. **Search by Size**

   * `find /usr -size +100M` finds files bigger than 100 MB.
   * `find /usr -size +50M -size -100M` finds files between 50 MB and 100 MB.
   * Lets you clean up or audit disk space easily.

5. **Search by Permissions**

   * `find / -perm 777` lists everything with permission 777.
   * You can also check for special permissions like `find / -perm 4755` (SUID), `2755` (SGID), or `1755` (Sticky Bit).
   * Good for security audits.

6. **Run a Command on the Results**

   * `find /data -user amir -exec rm {} \;`
   * Finds all files owned by `amir` and deletes them.
   * The `{}` is a placeholder for each file found, and `\;` ends the command.
   * This is powerful – you can automatically act on whatever you find.

---

## 3. `head`, `tail`, and `wc` – Quick File Inspection

These are simple but handy commands for peeking at files or counting things without opening them fully.

### **`head` – View the Beginning of a File**

* `head /etc/passwd` shows the first 10 lines.
* `head -n 5 /etc/passwd` shows only the top 5 lines.
* Perfect when you only need to preview the start of a file.

### **`tail` – View the End of a File**

* `tail /etc/passwd` shows the last 10 lines.
* `tail -n 5 /etc/passwd` shows the bottom 5 lines.
* Often used for checking the latest entries in logs.

### **`wc` (Word Count) – File Statistics**

* `wc /home/ct.txt` prints three numbers:

  1. Lines
  2. Words
  3. Characters
     plus the filename.
* `wc -l` shows only lines, `wc -w` only words, `wc -c` only characters.
* Great for quickly checking the size or length of a file’s content.

---


