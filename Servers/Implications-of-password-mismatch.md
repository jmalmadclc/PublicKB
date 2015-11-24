{{{
  "title": "Implications Of Password Changes (Password Mismatch between Local OS and Portal)",
  "date": "11-24-2015",
  "author": "Jake Malmad",
  "attachments": [],
  "contentIsHTML": false
}}}

### Overview:

When the Administrator or Root password is changed locally on a guest VM, rather than being changed through the CenturyLink Cloud Portal, the portal metadata will be out of sync with the local credentials, causing several problems to arise in CenturyLink functions. The functions that are impacted (failures) are:

•	Add disk partition (cannot format disk in VM, manual intervention notice posted to logs, raw volume is the result state, email alert sent to user)

•	Resize partition (cannot extend partition inside VM, manual intervention notice posted to logs, email alert sent to user)

•	Execute Package Errors:
•	[Error] Attempt Copy Package failed with error: The user name or password is incorrect.
•	[Error] One or more errors occurred. (Build log error: Attempt Copy Package failed with error: Password authentication failed. The following authentication methods are available for this user: publickey,gssapi-keyex,gssapi-with-mic,password.)

Items that will succeed:

•	Convert to template (NOTE:  when bringing out of template mode password is set again based on customer input)
•	Archive Server
•	Clone (NOTE:  the control password is updated automatically to the password input into the clone dialog box w/o notification)
•	Add RAW Disk (completed successfully but cannot be displayed in OS by means known to me, see above)
•	Remove disk
•	Autoscale
•	CPU/RAM metrics in Portal
•	Disk usage stats (this seems odd to me but it somehow works) (added disks appear in portal but show no usage stats, just grey)
•	Alerts (CPU/RAM/Disk)
•	Change CPU/RAM
•	Scheduled Tasks (power actions, snaps etc)
•	Power Actions
•	Snapshots
