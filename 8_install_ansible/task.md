During the weekly meeting, the Nautilus DevOps team discussed about the automation and configuration management solutions that they want to implement. While considering several options, the team has decided to go with `Ansible` for now due to its simple setup and minimal pre-requisites. The team wanted to start testing using Ansible, so they have decided to use jump host as an Ansible controller to test different kind of tasks on rest of the servers.

Install `ansible version 4.7.0` on Jump host using `pip3` only. Make sure Ansible binary is available globally on this system, i.e all users on this system are able to run Ansible commands.

---

To install Ansible version 4.7.0 on the Jump Host using pip3 and make it available globally, follow these steps:

## Step 1: Install Required Dependencies

Ensure pip3 and python3 are installed:

```bash
sudo yum install -y python3-pip
```

## Step 2: Install Ansible Version 4.7.0

```bash
sudo pip3 install ansible==4.7.0
```

## Step 3: Verify Installation
Check the installed version:

```bash
ansible --version
```

### Ensure it outputs:

```bash
ansible 4.7.0
```

## Step 4: Make Ansible Globally Accessible

If ansible is not found globally, link it to /usr/local/bin:

```bash
sudo ln -s /usr/local/bin/ansible /usr/bin/ansible
sudo ln -s /usr/local/bin/ansible-playbook /usr/bin/ansible-playbook
```

## Step 5: Confirm Global Access

Switch to a different user and check Ansible availability:

```bash
su - anotheruser
ansible --version
```
If it works, Ansible is now globally available.