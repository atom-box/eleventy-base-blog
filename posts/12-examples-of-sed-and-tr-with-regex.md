---
title: Nine Examples of sed and tr with Regular Expressions
description:
date: 2019-09-17
tags:
  - linux
layout: layouts/post.njk
---

Both tr and sed can modify text in the command line interface. tr is GNU Translate and sed is the GNU Stream Editor. Here are some examples I find myself using over and over.

## Delete the whole line if any part of it matches the pattern

``` bash/0
$ sed '/a/d' months.txt
june
july
september
october
november
december
```

``` bash/0
$ sed '/er/d' months.txt
january
february
march
april
may
june
july
august
```

``` bash/0
$ sed '/r/d' months.txt
may
june
july
august
```

## KEEP the line if any part of it matches the pattern

``` bash/0
$ sed '/r/!d' months.txt
january
february
march
april
september
october
november
december
```

``` bash/0
$ sed '/er/!d' months.txt
september
october
november
december
```

## Remove blank lines

``` bash/0
$ cat months.txt | sed "/^[[:space:]]*$/d"`
```

## Remove ING from the ends of words
TR fails here because it looks for single letters but SED works for the ING pattern.

``` bash/0/3
$ echo  "Running and scrambling to see the mayor!" |  tr -d "ing"
Ru ad scrambl to see the mayor!

$ echo  "Running and scrambling to see the mayor!" |  sed "s/ing//g"
Runn and scrambl to see the mayor!
```


## Any character can be used as the delimiter

You don't need to always delimit with a slash.
The following are equivalent; both will replace lowercase vowels with an x.

``` bash
sed s_[aeiou]_x_g
sed s/[aeiou]/x/g

```

## Escaping the ? or + operator
Unlike '*', both '+' (one or more) and '?' (zero or one) must be escaped.
``` bash
$ echo "The       great wheel in the  sky." | sed "s_ \+_x_g"
Thexgreatxwheelxinxthexsky.
$ echo "The       great wheel in the  sky." | sed "s_ \?_x_g"
xTxhxexxxxxxxgxrxexaxtxwxhxexexlxixnxtxhxexxsxkxyx.x
```


