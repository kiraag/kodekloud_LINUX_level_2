The Nautilus team doesn't want its data to be accessed by any of the other `groups/teams` due to security reasons and want their data to be strictly accessed by the `sysadmin` group of the team.

Setup a collaborative directory `/sysadmin/data` on `app server 3` in Stratos Datacenter.

The directory should be group owned by the group `sysadmin` and the group should own the files inside the directory. The directory should be `read/write/execute` to the user and group owners, and others should not have any access.

---

To set up a collaborative directory /sysadmin/data on App Server 3 in Stratos Datacenter that is strictly accessible by the sysadmin group, follow these steps:

## 1. Create the Directory
```bash
sudo mkdir -p /sysadmin/data
```

## 2. Create the sysadmin Group (If Not Exists)
```bash
sudo groupadd sysadmin
```

## 3. Set Group Ownership of the Directory
```bash
sudo chown :sysadmin /sysadmin/data
```

### 4. Set Proper Permissions
```bash
sudo chmod 770 /sysadmin/data
```
```bash
7 (rwx) → Owner has full permissions.
7 (rwx) → Group has full permissions.
0 (---) → Others have no permissions.
```

## 5. Set Group Ownership for New Files Inside Directory
To ensure that new files inside `/sysadmin/data` inherit the `sysadmin` group:

```bash
sudo chmod g+s /sysadmin/data
```

## Verification

1. Check Directory Permissions

```bash
ls -ld /sysadmin/data
```
Expected Output:

```bash
drwxrws--- 2 root sysadmin 4096 Mar 3 10:00 /sysadmin/data
```

2. Check Group Ownership

```bash
stat -c "%G" /sysadmin/data
```

Expected Output:
```bash
sysadmin
```

3. Check New File Ownership

```bash
touch /sysadmin/data/testfile
ls -l /sysadmin/data/testfile
```

Expected Output:
```bash
-rw-r--r-- 1 username sysadmin 0 Mar 3 10:05 testfile
```

- Conclusion

Now, only `sysadmin` group members can access `/sysadmin/data`, and any new files will be owned by the same group.
