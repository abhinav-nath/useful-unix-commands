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
