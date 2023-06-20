---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - slurm, srun, and sbatch - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit on [![hackmd-github-sync-badge](https://hackmd.io/9XoHaRy3RFyoEpSIaGqyBw/badge)](https://hackmd.io/9XoHaRy3RFyoEpSIaGqyBw) or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/slurm-srun-sbatch-clusters.md)

## srun commands must:
* srun commands describe necessary compute resources: time, memory, CPUs, queue

## sbatch scripts must:
* contain description of necessary compute resources: time, memory, CPUs, queue
* load necessary software via modules, conda, etc.

## sbatch scripts should/may:
* contain commands to measure resources actually used
* log output
* notify you when things are done
* be in version control

## Session notes

(add notes here, everyone!)

## Documentation and tutorials and other resources

(add your favorites here!)

Introductory:
* [Executing large analyses on HPC clusters with slurm](https://ngs-docs.github.io/2021-august-remote-computing/executing-large-analyses-on-hpc-clusters-with-slurm.htm)