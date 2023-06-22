---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - automating everything with scripts - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: [![hackmd-github-sync-badge](https://hackmd.io/Vd7gHav9QZ-LGegA5CUE9Q/badge)](https://hackmd.io/Vd7gHav9QZ-LGegA5CUE9Q)
 or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/scripts-for-automating.md)
 
"Scripts" ("shell" scripts, e.g. bash scripts; R scripts; Python scripts; etc.) are text files containing instructions in a scripting language (bash, Python, R, etc.). Typically the instructions could be run interactively as well, but you are putting them in a script so that you can run them all at once.

Scripting languages (like bash, R, and Python) typically ignore lines starting with `#` (for comments, and othe reasons).

## Key point about scripts

A script is a text file containing instructions in some language.

You can always run it explicitly, e.g. `python script.py`. (Note that the `.py` ending is for humans, not for computers.)

Scripts run in their own subprocess - so things like working directory and environment variables are discarded upon exit.

Every script has its own language - common / typical ones are `bash`, `python`, `R` (the command line interpreter for `R` is called `Rscript`).
* bash: a shell program where you do things like `cd`, `rm`, `ls`, etc.
* python: a programming language that is often used for data processing and machine learning as well as other things
* R: a programming language that is often used for data processing, statistics, and visualization, as well as other things.
* (there's no right or wrong answer to "what language do I learn/use", just tradeoffs!)

Use a script when you don't want to type all that stuff out, and/or you want to automate something.

Scripts can run other scripts! :tada: 

## Recommended activities for collaboratory

* put your scripts in git & github!
* put them in a `scripts/` or `bin/` subdirectory
* make them command-line programs!
    * annotate your scripts with ``#! /usr/bin/env LANGUAGE` at the top
    * make them executable with `chmod +x ...`
    * (commit and update your git)
* change them to be "portable" by location (use relative paths only, or change them to take command-line arguments)
* add command line options (R, Python)

## scripts must:

* run your stuff!

## scripts should:

* have a file ending indicating their language (`.py`, `.R`, `.sh`)
* have `#! program` at top indicating their interpreter, and be executable (`chmod +x scriptname`)
* be in version control
* not be something you have to edit by hand to change parameters (but this can be hard!)
* bash scripts should use `set -x`, `set -e`
* not have full paths hardcoded in:
    * use relative paths
    * take in arguments from command line (see examples below)

## scripts may:

* R, python: use `#! /usr/bin/env ...` at top to properly run in `module` or `conda` environments
* take input/output via command line parameters; see examples below
* be configurable via options (e.g. python argparse)
* python: contain `__main__` block
* be something you parameterize and parallelize with GNU `parallel`
* and/or be something that you parameterize and parallelize by running multiple sbatch commands

## "scripts" vs sbatch scripts

sbatch scripts differ from regular scripts in that they have sbatch configuration options at the top, guarded from the scripting language by comments (`# `). They're typically written in bash but I'm not sure that's required.

(question: can you sbatch python scripts? Titus should try ;))

Note that you can run sbatch scripts at the command line with `bash scriptname`. They just don't get an allocation via slurm. So you can do either:
* `sbatch scriptname`
* or `srun ...` and then `bash scriptname`.

## Session notes

(add notes here, everyone!)

## Documentation and tutorials and other resources

(add your favorites here!)

Some basics:
* Remote computing tutorial: [ Automating your analyses and executing long-running analyses on remote computers](https://ngs-docs.github.io/2021-august-remote-computing/automating-your-analyses-and-executing-long-running-analyses-on-remote-computers.html)

On exit codes in UNIX processes: or, why is "zero" success??
* read: [never fail me](https://ngs-docs.github.io/2023-snakemake-book-draft/recipes/never-fail-me.html)

Parallelization:

* titus has a tutorial on parallelization with scripts here: [A brief overview of automation and parallelization options in UNIX/on an HPC](https://hackmd.io/E8EgmtZoSe-lou4ZJnpiFw?view)

## Appendix - example scripts

### bash script

Your basic bash script:
```
#! /bin/bash
echo hello, world
```

Using arguments:
```
#! /bin/bash
echo program name is $0
echo first command line parameter is $1
echo second command line parameter is $2
```

Being safe with variables
```
#! /bin/bash
set -u # disallow empty variables
echo program name is $0
echo first command line parameter is $1
echo second command line parameter is $2
```

Fail immediately:
```
#! /bin/bash
set -e # exit when exit code is 0
set -x # print out commands as they are executing

mkdir test
rm test # will fail, since `test` is a directory

echo continuing with life because bash is WEIRD.
```

### R scripts

See [this script](https://raw.githubusercontent.com/mblstamps/stamps2022/main/kmers_and_sourmash/sourmash_gather_to_metacoder_plot.R) for full example.

```
#! /usr/bin/env Rscript
# Taylor Reiter, github: @taylorreiter
# 7/27/22

# from https://www.r-bloggers.com/2015/09/passing-arguments-to-an-r-script-from-command-lines/
args = commandArgs(trailingOnly=TRUE)

# test if there is at least one argument: if not, return an error
if (length(args)==0) {
  stop("At least one argument must be supplied (input gather CSV)", call.=FALSE)
} else if (length(args)==1) {
  # default output file
  args[2] = "metacoder_gather.png"
}

# from https://github.com/sourmash-bio/sourmash/issues/2041
library(dplyr)
library(readr)
library(metacoder)
# ... more R code goes here
```

### python scripts

your basic hello world:
```
#! /usr/bin/env python
print('hello world')
```

Your basic use of command line args:
```
#! /usr/bin/env python
import sys

print('hello world; first argument is:')
print(sys.argv[1])
```

Titus's usual template using argparse:
```
#! /usr/bin/env python
import sys
import argparse

def main():
    p = argparse.ArgumentParser()
    p.add_argument('some_value')
    args = p.parse_args()
    
    print(f'some value is: {args.some_value}')

if __name__ == '__main__':
    sys.exit(main())
```

You might also look at command-line parsing libraries like `click`.
