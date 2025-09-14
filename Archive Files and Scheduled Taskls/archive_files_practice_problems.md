# **Archiving, Compression & Automation in Linux**
---

### Archiving & Compression

1. Create an uncompressed archive of the `/etc` directory and store it as `/home/student/etc_backup.tar`.

2. Create a gzip-compressed archive of the `/var/log` directory and save it as `/home/student/logs.tar.gz`.

3. Create a bzip2-compressed archive of `/usr/share/doc` and save it as `/home/student/docs.tar.bz2`.

4. Create an xz-compressed archive of `/boot` and save it as `/home/student/boot_backup.tar.xz`.

5. View the contents of `/home/student/logs.tar.gz` without extracting it.

6. Extract the archive `/home/student/etc_backup.tar` into the `/tmp/etc_restore` directory.

7. From the archive `/home/student/docs.tar.bz2`, extract only the file `README` into `/home/student/extracted_files`.

8. List the contents of `/home/student/boot_backup.tar.xz` showing details like permissions, owners, and size.

9. Create an archive of `/var/log` and store it as `/home/student/mixed_backup.tar`, then compress it separately using the gzip command.

10. Extract all files from `/home/student/logs.tar.gz` into the current user’s home directory.

---

### Automation with `at`

11. Schedule a task that creates a file `/home/student/message.txt` with the content `Backup completed` at 11:30 PM today.

12. Schedule a system shutdown to occur at 4:00 PM tomorrow.

13. Schedule a job to create a compressed backup of `/etc` as `/home/student/etc_nightly.tar.gz` at 2:00 AM the next day.

14. Schedule a task that writes `System maintenance done` into `/home/student/maintenance.log` at 8:00 AM on December 1st.

15. Display all jobs currently scheduled with the `at` command.

16. Remove the `at` job with job ID `3`.

---

### Automation with `cron`

17. Schedule a cron job to run every day at 7:00 PM that creates a compressed archive of `/etc` as `/home/student/daily_backup.tar.gz`.

18. Schedule a cron job to run every Saturday at 5:00 PM that creates a compressed archive of `/var/log` as `/home/student/sat_backup.tar.gz`.

19. Schedule a cron job to append the line `Weekly check completed` into `/home/student/weekly.log` every Monday at 9:00 AM.

20. Schedule a cron job to run at midnight on the first day of every month that creates a compressed archive of `/home/student` as `/home/student/monthly_home.tar.gz`.

21. Schedule a cron job to run every 10 minutes that appends the line `Task running` into `/home/student/cron_test.log`.

22. List all cron jobs created by the current user.

---

