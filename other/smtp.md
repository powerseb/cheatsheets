### Test manual for open relay
```
HELO <domain>
250 ...
Mail From: <user@domain>
250 2.1.0 Ok
Rcpt To: <user2@domain2>
250 2.1.5 Ok
Data
354 End data with <CR><LF>.<CR><LF>
Subject: <subject>
<content>
.
```

### Authenticate using base64
```
echo -n <user> | base64
echo -n <password> | base64
...
AUTH LOGIN
...
<userBase64>
...
<passwordBase64>
```

### Verify if user exists
```
VRFY <user>
```

### Mail spoof countermeasures - SPF (Sender Policy Framework - check if host is authorized to send mail)
```
dig <domain> | grep spf
```

### DMARC (Domain-based Message Authentication, Reporting & Conformance - polycies instruct mail server how to process mail for given domain)
```
dig _dmarc.<domain> TXT
```

### DKIM (DomainKeys Identified Mail - mail is signed and validatet by foreign Mail Transfer Agent - key is held within TXT DNS-record)
```
dig <domain> TXT | grep "p="
```

