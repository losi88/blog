---
layout: default
title: "command"
parent: LINUX
nav_order: 2
published: true
---

# command
{: .no_toc }

## Table Of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## awk

### Option

```
-F fs            : Use fs for the input field separator
```

### Using Variables
```
$0 for the whole line.
$1 for the first field.
$2 for the second field.
$n for the nth field.
```
### Difference between single and double quotes in awk 
Based on the comments above by awk experts and some research, I am posting this answer:
```
awk strings are enclosed in double quotes, not single quotes; more precisely: single quotes are not string delimiters in awk, unlike shell
awk attaches no special meaning to single quotes and they need to be enclosed in double quotes if used in string literals
it is best to use single quotes to wrap awk statements on command line, unlike OP's code that's using double quotes (Ed pointed this out clearly)
```
Further clarification:
```
"" is the null string in awk, not ''
to use single quotes in an awk string literal, enclose them in double quotes, as in "Ed's answers are great!"
other techniques followed while handling single quotes in awk are:

a) use a variable, as in awk -v q="'" '{ print q }' ...

b) use octal or hex notation, as in awk '{ print "\047"$0"\047" }' ...
```

### Reference
```
https://www.geeksforgeeks.org/awk-command-unixlinux-examples/
https://stackoverflow.com/questions/44445852/difference-between-single-and-double-quotes-in-awk
```
---
## Regex
### Regex Graph
```
https://jex.im/regulex/#!flags=&re=%5E(a%7Cb)*%3F%24
```
