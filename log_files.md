## Log files

Tail a log file but show only specific lines:

```shell
tail -f /path/to/log | grep --line-buffered "X" | grep -v "Y"
```

