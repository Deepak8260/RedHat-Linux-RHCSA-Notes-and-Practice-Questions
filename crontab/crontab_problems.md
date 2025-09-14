# **RHCSA Job Scheduling Practice Questions**

---

### Questions

1. As the user `deepak`, schedule a cron job that runs the script `/home/deepak/logtime.sh` every minute.

2. Create a cron job for the user `deepak` that executes `/home/deepak/sysinfo.sh` every day at 6 PM.

3. Schedule a cron job that runs `/home/deepak/backup.sh` on the 10th of every month at 6 PM.

4. Configure a cron job that executes `/home/deepak/weekly.sh` every Sunday.

5. As the root user, list all cron jobs configured for the user `ajay`.

6. As the root user, deny the user `neeta` from using cron.

7. Configure the system so that only the users `ajay` and `deepak` are allowed to use cron.

8. Create a shell script at `/home/deepak/job1.sh` which appends the text `Backup started at <current date and time>` to `/home/deepak/backup.log`. Make this script run every minute using cron.

9. Verify if the script `/home/deepak/job1.sh` is running correctly by checking the log file `/home/deepak/backup.log`.

10. Write a shell script `/home/deepak/admin_tasks.sh` that:

    * Copies all files owned by the user `sara` to `/backup`.
    * Deletes all files owned by the user `harry`.
    * Archives and compresses the `/etc` directory into `/backup/etc.tar.xz`.
  Schedule this script to run at 6:30 PM on December 10 every year.

11. Configure a cron job that runs `/home/deepak/job1.sh` every minute and saves both output and errors into `/home/deepak/job1.log`.

12. As the root user, monitor cron job executions in real time using the appropriate log file.

13. As the user `deepak`, schedule a cron job that runs `/usr/local/bin/cleanup.sh` every 5 minutes.

14. Configure a cron job for the user `neeta` to run `/usr/local/bin/report.sh` at 7:15 AM every day.

15. Schedule a cron job that executes `/usr/local/bin/rotate_logs.sh` every Monday at midnight.

16. Create a cron job that runs `/usr/local/bin/check_disk.sh` every two hours.

17. Configure a cron job that runs `/usr/local/bin/monthly_audit.sh` on the first day of every month at 1:05 AM.

18. As the root user, list all cron jobs configured for the entire system.

19. Restrict all users except `deepak` and `ajay` from scheduling jobs with the `at` command.

20. Schedule a one-time job with `at` to run `/usr/local/bin/security_scan.sh` at 11:45 PM today.

21. Schedule a job with `at` to execute `/usr/local/bin/reboot_notice.sh` at 8 AM two days from now.

22. Verify the scheduled `at` jobs for the user `neeta`.

23. Remove all pending `at` jobs for the user `ajay`.

24. Create a shell script `/usr/local/bin/daily_tasks.sh` that:

    * Lists the running processes into `/var/log/process.log`.
    * Displays the free disk space into `/var/log/disk.log`.
    * Shows all logged-in users into `/var/log/users.log`.
  Schedule this script to run daily at 9:30 AM.

25. Configure a cron job that runs `/usr/local/bin/alert.sh` every minute but redirects all output and errors to `/dev/null`.

26. As the root user, identify which cron jobs failed to execute by checking the appropriate log file.

27. Create a cron job that runs `/usr/local/bin/sync.sh` every 15 minutes.

28. Schedule a cron job to run `/usr/local/bin/update_db.sh` at 6:10 AM on weekdays (Monday to Friday).

29. Schedule a cron job for the user `deepak` that runs `/usr/local/bin/holiday.sh` on December 25 at 8:00 AM.

30. Temporarily disable all cron jobs for the user `ajay` without deleting them.

---

