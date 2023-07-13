---
share: true
tags:
  - Home Assistant
  - Backup
---
Hello, Home Assistant enthusiasts! Today, we're going to walk through a simple, yet effective way to set up an automated backup solution for your Home Assistant Operating System (HAOS) using the Samba Backup add-on. This will ensure your HAOS data is safe and sound, and can be easily restored if needed. Let's dive in!

## Step 1: Installing the Samba Backup Add-on

First things first, we need to install the Samba Backup add-on. This handy tool will allow us to create automatic backups and store them on a network share, such as a Synology NAS.

1. Navigate to your Home Assistant dashboard.
2. Click on the Supervisor menu on the left-hand side.
3. Select the Add-on Store tab.
4. Search for "Samba Backup" in the search bar.
5. Click on the Samba Backup add-on and then click on the INSTALL button.

Voila! You've successfully installed the Samba Backup add-on.

## Step 2: Configuring the Samba Backup Add-on

Now that we have the add-on installed, it's time to configure it. This is where we tell the add-on where to store the backups, how many backups to keep, and when to create the backups.

1. Go to the Supervisor menu again and click on the Dashboard tab.
2. Find the Samba Backup add-on and click on it.
3. Click on the Configuration tab.

Here, you'll need to enter the following details:

```yaml
host: <hostname or IP of your Synology NAS>
share: <name of the Samba share on your Synology NAS>
target_dir: <directory on the Samba share where backups will be stored>
username: <username to access the Samba share>
password: <password to access the Samba share>
keep_local: 0
keep_remote: 10
trigger_time: '02:00'
trigger_days: 'mon,wed,fri'
backup_name: "{type} Backup {version} {date}"
```

Replace the placeholders (`<...>`) with your actual values. The `trigger_days` option is set to 'mon,wed,fri' to create backups every third day. The `keep_remote` option is set to 10 to keep ten days' worth of backups, after which the oldest backup will be deleted when a new one is created. The `backup_name` option is set to include the type of backup, the version of Home Assistant, and the date in the name of the backup.

4. Click on SAVE to save your configuration.

## Step 3: Starting the Samba Backup Add-on

With the configuration saved, we're ready to start the add-on.

1. Click on the Info tab for the Samba Backup add-on.
2. Click on the START button.

And that's it! Your Samba Backup add-on will now automatically create backups according to the schedule you set and store them on your Synology NAS.

## Step 4: Restoring from a Backup

In the unfortunate event that you need to restore your HAOS from a backup, here's how you do it:

1. Go to the Supervisor menu and click on the Snapshots tab.
2. You'll see a list of all your available backups. Click on the one you want to restore.
3. Click on the RESTORE button.

Remember, it's always a good idea to keep your Home Assistant configuration and data safe. With this automated backup solution, you can rest easy knowing that your HAOS data is secure and can be easily restored if needed. Happy automating!