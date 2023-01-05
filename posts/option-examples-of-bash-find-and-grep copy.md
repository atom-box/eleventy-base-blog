---
title: Common examples of Find and Grep
description:
date: 2021-10-04
tags:
  - linux
layout: layouts/post.njk
---

Find and Grep are friends. I memorize *Grep* syntax pretty well but mix up things in the *Find* syntax. So here are my personal examples to refer to.  

## Easy examples with FIND in Linux BASh

The `sudo` can usually be omitted unless you're rooting around up in /etc and those kinds of places.  It does no harm here but is actually not neccessary down in the tilda: ~ (your home directory)

```bash
## finds directories recursively anywhere in your home
find ~ -type d -name vendor

## searches from your current (pwd) directory, case insensitive
sudo find . -iname *eadev*

## The f looks for filenames, ignoring the pattern in paths, directories
## The ls option makes long listing style
## Note this will be case SENSITIVE since there's no i flag
sudo find . -type f -name "bin" -ls
```


## Basic examples of GREP

``` bash
## look for abc in both index.php and index.html
grep abc public/index.* 
```

## Some options to try with GREP in Linux BASh

``` bash/0
-i // insensitive
-n // show line numbers
-r // (??)
-c // counts occurances per filename; cool!
-R // drill down recursively
-C // 1 show one line of context
```


## Tell Grep which style of regex to use

You learn Regex in a tutorial or book somewhere and they don't tell you that the command line tools don't tell you up front which flavor of pattern matching they are doing. 
In Grep, you can conquer this aspect by forcing a flavor; use these options.

```
-E extended regex
-F glob style 
-G old fashioned regex, pre-extended
-P Perl style, like Larry Wall
```

Glob stands for global. It is not RegEX at all.  In Glob style, asterisks are wildcards, same as percent signs in SQL. And same as asterisks in Javascript match command.

## BASh can't capture chars unless you escape the capture parens.

So  
`\(` and `\)`,  
not  
`(` and `)`  

## Building regex on the CLI isn't hard

A lot of complaints about RegEx being hard are deserved because reading someone else's Regex is tedious.  Writing it isn't hard though, you just build up a char at a time. Play around with an echoed string in SED. Try this:
``` bash
echo "katmandu cat" | sed 's_AT_froggy_gi'
```

