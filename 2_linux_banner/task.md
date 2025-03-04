Task

During the monthly compliance meeting, it was pointed out that several servers in the Stratos DC do not have a valid banner. The security team has provided serveral approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.



Update the `message of the day` on all `application` and `db servers` for Nautilus. Make use of the approved template located at `/home/thor/nautilus_banner` on jump host

---

To update the `Message of the Day (MOTD)` on all `application and database servers` in the Nautilus environment using the approved template located at `/home/thor/nautilus_banner` on the jump host, follow these steps:

## Step 1: Copy the Banner Template to any app server to `/tmp/` path.

1. To copy the banner template located on jump host to app server, use the command

```bash
scp nautilus_banner <user>@<app-server-ip>:/tmp
```
It asks for password of the app server, enter the password. Then the banner template will be copied to `/tmp` path of app server.

## Step 2: Login to the app server and run the following commands:

1. Login to the app server and move the template to `/etc/motd` 

```bash
# login command
ssh <user>@<app-server-ip> 
# Move the banner to the MOTD location
sudo mv /tmp/nautilus_banner /etc/motd
# Set the correct permissions
sudo chmod 644 /etc/motd
```

## Step 3: Verify the MOTD

1. After updating the MOTD, logout & login again to the app server to verify that the new banner is displayed correctly.

```bash
# logout from the app server
logout
# login again to the app server
ssh <user>@<app-server-ip>
```
You should see the new banner message upon successful login.

### Note

Repeat the same steps on the servers which we want to do this task.

This process ensures that all servers in the Nautilus environment are compliant with the security requirements regarding the MOTD banner.