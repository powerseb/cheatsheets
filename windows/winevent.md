### Get admin logon event
```
Get-WinEvent -FilterHashtable @{Logname='Security';ID=4672} -MaxEvents 1 | Format-List –Property *
```

### Discover possible kerberoasting attacks
```
Get-WinEvent -FilterHashtable @{Logname='Security';ID=4769} -MaxEvents 1000 | ?{$_.Message.split("`n")[8] -ne 'krbtgt' -and $_.Message.split("`n")[8] -ne '*$' -and $_.Message.split("`n")[3] -notlike '*$@*' -and $_.Message.split("`n")[18] -like '*0x0*' -and $_.Message.split("`n")[17] -like "*0x17*"} | select -ExpandProperty message
```

### Event IDs lateral movement
```
4624  Account Logon
4634  Account Logoff
4672  Admin Logon
```

### Event ID kerberoast
```
4769 Request Kerberos Ticket 
```

### Event IDs modification of ACLs (Audit Policy for object must be enabled)
```
4662  An operation was performed on an object
4670  Permissions on an object were changed
5136  A directory service object was modified
```

### Event IDs modification of users and groups
```
4724  An attempt was made to reset an account password
4728  A member has been added to a security-related group
```

### Event IDs modification of scheduled tasks
```
106   Scheduled task registered
140   Scheduled task updated
141   Scheduled task updated
4698  Scheduled task created
4699  Scheduled task deleted
4700  Scheduled task enabled
4701  Scheduled task disabled
4702  Scheduled task disabled
```

### Last reboot equivalent
```
Get-WinEvent -FilterHashtable @{logname='System'; id=6005,1074} | ForEach-Object { $_.TimeCreated; if ($_.Id -match "6005") { "boot" } if ($_.Id -match "1074") {"shutdown"}}
```

