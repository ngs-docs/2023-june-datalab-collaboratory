---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - automating everything with scripts - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: [![hackmd-github-sync-badge](https://hackmd.io/Vd7gHav9QZ-LGegA5CUE9Q/badge)](https://hackmd.io/Vd7gHav9QZ-LGegA5CUE9Q)
 or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/git-for-version-control.md)

## scripts

must:
* run your stuff

should:
* have #! at top and be executable
* be in version control
* not be something you have to edit by hand to change parameters (but this is hard!)
* bash: use set -x, set -e
* not have full paths hardcoded in via command line

may:
* use ``#! /usr/bin/env ...` at top
* take input/output via command line parameters
* be configurable via options (e.g. python)
* python: contain `__main__` block
* be something you parameterize and parallelize with GNU `parallel`
* be something that you parameterize and parallelize by running multiple sbatch


NOTE: titus tutorial here: [A brief overview of automation and parallelization options in UNIX/on an HPC](https://hackmd.io/E8EgmtZoSe-lou4ZJnpiFw?view)
