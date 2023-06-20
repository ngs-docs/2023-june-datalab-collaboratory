---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - snakemake for workflows - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: 
or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/organizing-projects.md)

should:
* run as much of your pipeline as possible
* not re-create files/re-run commands unnecessarily

may:
* be configurable outside the snakefile
* use `conda:` blocks to install conda software
* run jobs efficiently in parallel with -j, and/or be parallelizable across a cluster

how to get started:
* pick a series of three commands that run quickly :)
* list out the shell commands you want to run, put them in shell blocks, run them by name
* add input/output blocks
* add a pseudorule
