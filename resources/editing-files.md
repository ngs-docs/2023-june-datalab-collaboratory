---
tags: summer2023, collaboratory
---
# Editing files on remote computers - setting your default editor

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

[![hackmd-github-sync-badge](https://hackmd.io/wwMJiUc5REKRS54okRaoJw/badge)](https://hackmd.io/wwMJiUc5REKRS54okRaoJw)

Editing files on remote computers is not, by default, particularly easy. The default editors make you use various different key combinations, because they don't integrate very well with 

The default editor on farm for things like editing git commit messages is `jed` (see [Wikipedia page](https://en.wikipedia.org/wiki/JED_(text_editor))). The first thing you need to know about Jed is this: to exit it, type CTRL-X CTRL-C.

## Setting your default editor to `nano`

Many of you use the `nano` editor, which is a good simple editor! But it needs to be set explicitly.

To do that, add these two lines to your `~/.bashrc`:
```
export EDITOR='nano'
export VISUAL='nano'
```
and then either log out and log back in, or run
```
source ~/.bashrc
```

### More background reading

The first two entries in [this StackOverflow post](https://unix.stackexchange.com/questions/4859/visual-vs-editor-what-s-the-difference) are good if you're interested in why there are two different environment variables, $VISUAL and $EDITOR, that specify editors.

## Other choices

Hannah really likes [VSCode](https://code.visualstudio.com/), which is a desktop application that runs on Mac and Windows and Linux, and offers directory browsing and ssh functionality for working directly with remote computers! See her [VSCode tutorial here](https://hackmd.io/r0L9HY0TSFmHqFLE9r6Awg)

Titus teaches using RStudio Server, which [is available on farm](https://hackmd.io/ocS5H5CnTAm_EWugvYF_Mw?view). It's somewhat tricky to get it running, however, because it uses ssh tunneling. On the flip side, once set up, it also provides a full RStudio experience ;).

## Session notes

Farm has `Jed` which is an `emacs` compatible editor

what is the difference `/.profile` and `/.bashrc` files?
- `.profile` is run in a login shell 
- `.bashrc` is run anytime a login shell is not used

What is the difference between the `bash` and `source` commands?
`bash` runs the bash script
`source` runs a bash script in login shell and retains the environmental commands set up within the script

`Nano` is perfectly good for opening and editing, but searching and editing a large file is difficult. There also is no syntax highlighter in `nano`.