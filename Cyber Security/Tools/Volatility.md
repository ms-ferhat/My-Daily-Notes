#DF #Tools

### Show Windows info

```
python vol.py -f memory.mem windows.info
```

### List all running Process
```
python vol.py -f memory.mem windows.pslist
```

### All Process Run from cmd
```
python vol.py -f memory.mem windows.cmdline
```

### List All Network Activity
```
python vol.py -f memory.mem windows.netstat
```

## Search for malicious code in memory
```
python vol.py -f MemoryDump.mem windows.malfind
```