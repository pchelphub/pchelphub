---
layout: default
title: Reset / reinitialise Network States & Adapters
parent: Network
---
Written by [slydelv](https://github.com/slydelv)

### Run the following commands in an elevated Command Prompt
(Run CMD as Admin)

```
netsh winsock reset catalog
netsh int ip reset reset.log
ipconfig /flushdns
ipconfig /registerdns
route /f
shutdown /r /f /t 0
```

*Note: Your machine automatically restart when running this comand.*
