## find command

Executing commands on the files found by the `find` command

```shell
find -iname "MyCProgram.c" -exec md5sum {} \;
```

Finding the Top 5 big files

```shell
find . -type f -exec ls -s {} \; | sort -n -r | head -5
```

Finding the Top 5 Small Files

```shell
find . -type f -exec ls -s {} \; | sort -n  | head -5
```

```shell
find . -iname core -exec rm {} \;
```

Using more than one { } in same command

```shell
find -name "*.txt" cp {} {}.bkup \;
```

Substitute space with underscore in the file name

```shell
find . -type f -iname ,*.mp3? -exec rename ,s/ /_/g, {} \;
```