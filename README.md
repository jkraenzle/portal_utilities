# portal_utilities

Currently, a set of utilities for Portal backup and restore. There are two ways to execute the utilities, either by running individual actions, or performing a complete backup/restore cycle.

The requirements.txt includes the additional dependent Python libraries required to run the scripts.

<b>Backup/Restore Cycle</b>

> python portal_utilities.py --backuprestorefromconfig backuprestore.yaml

The backuprestore.yaml configuration file includes the ability to specify the source hostname and username and the destination hostname and username, along with backup storage, deletion, and other options.

<b>Backup Only</b>

> python portal_utilities.py --backupfromconfig backup.yaml

The backup.yaml configuration file includes the ability to specify hostname, username, and backup storage, deletion, and other options.

<b>Actions</b>

<b>List backups</b>

> python portal_utilities.py --hostname <hostname> --username admin --action list_backups

Note, only two backups are permitted on Portal at one time. If two exist, one backup file needs to be deleted (using the ID), if there are already two existing and you want to pull (create) or upload a backup file.

<b>Delete backup</b>

> python portal_utilities.py --hostname <hostname> --username admin --action delete_backup --actionfile <ID_of_backup_file_on_appliance>

<b>Create, download and delete backup</b>

> python portal_utilities.py --hostname <hostname> --username admin --action pull_backup

<b>Upload backup</b>

> python portal_utilities.py --hostname <hostname> --username admin --action upload_backup --actionfile <backup_file.backup.tgz>

<b>Upload certificate</b>

> python portal_utilities.py --hostname <hostname> --username admin --action upload_certificate --actionfile <certificate.yaml>
>> The file certificate.yaml configures (1) the path to certificate and key file and (2) the passphrase.
>> An example certificate.yaml is included in the GitHub repository files.

<b>Restore backup</b>

> python portal_utilities.py --hostname <hostname> --username admin --action restore --actionfile <ID_of_backup_file_on_appliance>

<b>Show restore status</b>
  
> python portal_utilities.py --hostname <hostname> --username admin --action restore_status
```
  Output example:
   {'last_restore_time': 1602540247, 'status': 'completed', 'status_message': ''}
```
