## grep command

Find all files containing a String

* from the root directory
  ```shell
  grep -Ril "text-to-find-here" /
  ```

* from the current directory
  ```shell
  grep -Ril "text-to-find-here" .
  ```
<br>

| Regular Expressions - Basics                                               |
| :--------------------------------------------------------------------------|
| `.` A period represents any single character                               |
| `[]` Brackets enclose character sequences                                  |
| `-` A dash is used between characters to create a sequence (inside [])     |
| `^` A carat is used to negate a sequence (inside [])                       |
| `*` An asterisk searches for zero, one, or many instances of a search item |
| `?` A question mark searches for zero or one instance of a search item     |
| `+` A plus sign searches for one or many instances of a search item        |
| `$` A dollar sign searches the end of a line                               |
| `^` A carat searches the beginning of a line                               |
| `\` A backslash preceding a special character makes it a plain character   |

grep.txt
```
I like golf.
Golf is played on grass.
I created gilf.
Gandalf is a protagonist.
What is g2lf?
This time the o is missing in glf.
Some people might say goolf.
golf has been a fine example
let's talk about something besides golf
```

### Using brackets

```shell
$ grep "[gG]olf" grep.txt
```

> I like **golf**.<br>
> **Golf** is played on grass.<br>
> **golf** has been a fine example<br>
> let's talk about something besides **golf**<br>

<br>

```shell
$ grep "[gG][oi]lf" grep.txt
```

> I like golf.<br>
> Golf is played on grass.<br>
> I created gilf.<br>
> golf has been a fine example<br>
> let's talk about something besides golf<br>

### The period

```shell
$ grep "g.lf" grep.txt
```

> I like **golf**.<br>
> I created **gilf**.<br>
> What is **g2lf**?<br>
> **golf** has been a fine example<br>
> let's talk about something besides **golf**<br>

### Dash

```shell
$ grep "g[a-z]lf" grep.txt
```

> I like **golf**.<br>
> I created **gilf**.<br>
> **golf** has been a fine example<br>
> let's talk about something besides **golf**<br>
