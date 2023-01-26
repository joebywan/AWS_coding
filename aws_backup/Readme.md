# AWS Backup CFN template

This will setup the following

- Backup vault (won't be deleted if the stack tries to update/replace/delete)
- Backup Role - Needs the permissions to do stuff
- SNS Topc & Policy - So you can receive the notifications about failed backups
- 3 x Backup plans that execute every 7, 14 & 28 days.

The backup plans have selection criteria added to them so that they find the resources using tags.

The tags to use:
backup:7 - Backup every 7 days, retains backups for 28 days.
backup:14 - Backup every 14 days, retain backups for 56 days.
backup:28 - Backup every 28 days, retain backups for 112 days.

I've purposely not setup any vault access permissions, if something goes pear shaped, you can add that to it later when you need to restore.  I'd rather leave it inaccessible by default.