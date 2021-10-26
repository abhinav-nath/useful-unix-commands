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

This method searches for any character that falls between a and z (in alphabetic order).
This excludes strings with numbers or symbols in between g and lf that are not really words (like g2lf) and probably not part of your desired search criteria.

```shell
$ grep "g[a-z]lf" grep.txt
```

> I like **golf**.<br>
> I created **gilf**.<br>
> **golf** has been a fine example<br>
> let's talk about something besides **golf**<br>


You can also search for multiple character sequences by including additional sets within the brackets.
For instance, to search for a-z and A-Z, use the following search:

```shell
$ grep "g[a-zA-Z]lf" grep.txt
```

### Caret

It is easier to search by avoiding certain characters rather than specifying the characters you want to find.

```shell
$ grep "g[^0-9]lf" grep.txt
```

### Asterik

An asterisk indicates the search item can occur zero, once, or multiple times.

```shell
grep "go*lf" grep.txt
```

Your search returns lines with the words golf, glf, and goolf.

<br>

### Question mark

The function of a question mark is similar to an asterisk, except the search item can occur zero or once.
Multiple occurrences will not be matched.

```shell
$ grep "go?lf" grep.txt

# need to escape it on mac
$ grep "go\?lf" grep.txt
```

**golf** and **glf** are returned as matching results, but **goolf** is not because there are multiple instances of the search item `o` preceding the `?`

> I like **golf**.<br>
> This time the o is missing in **glf**.<br>
> **golf** has been a fine example<br>
> let's talk about something besides **golf**<br>

### Plus sign

A plus sign will find when a search item occurs once or multiple times.
Unlike the asterisk, at least one occurrence must be found to make a match.

```shell
$ grep "go+lf" grep.txt

# need to escape it on mac
$ grep "go\+lf" grep.txt
```

This time, the search returns **golf** and **goolf**, but it does not return **glf** because no **o** is found.
