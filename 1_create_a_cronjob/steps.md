Task

The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:

a. Install `cronie` package on all Nautilus app servers and start `crond` service.

b. Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

---

To acheive this task, follow these steps.

## Step 1: Install cronie Package on All Nautilus App Servers

1. SSH into each app server:
Use the appropriate credentials to log into each of the Nautilus app servers.

```bash
ssh <user>@<app_server_ip>
```

2. Install the `cronie` package:
On each server, install the cronie package using the package manager (yum for CentOS/RHEL).

```bash
sudo yum install cronie -y
```

3. Start and enable the `crond` service:
After installation, start the `crond` service and enable it to start on boot.

```bash
sudo systemctl start `crond`
sudo systemctl enable `crond`
```

4. Verify the status of crond:
Ensure that the crond service is running without any issues.

```bash
sudo systemctl status crond
```

## Step 2: Add a Cron Job for the Root User

1. Open the crontab for the root user:
Edit the crontab file for the root user to add the new cron job.

```bash
sudo crontab -e
```

2. Add the cron job:
Insert the following line into the crontab file to schedule the task:

```bash
 */5 * * * * echo hello > /tmp/cron_text
```
This cron job will run every 5 minutes and write "hello" to the `/tmp/cron_text` file.

3. Save and exit:
Save the changes and exit the editor. If you're using vi or vim, you can do this by pressing Esc followed by :wq and then Enter.

4. Verify the cron job:
List the cron jobs to ensure that the new job has been added successfully.

```bash
sudo crontab -l
```

5. Check the output:
After a few minutes, check the `/tmp/cron_text` file to confirm that the cron job is executing as expected.

```bash
cat /tmp/cron_text
```
You should see the word `"hello"` in the file.

### Summary

By following these steps, you have successfully installed the `cronie` package, started the `crond` service, and added a cron job that runs every 5 minutes to write `"hello"` to a file. This setup can now be used as a template for deploying more complex automation scripts across the Nautilus app servers.