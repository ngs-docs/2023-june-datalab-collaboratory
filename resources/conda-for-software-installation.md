---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - conda for software installation - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: [![hackmd-github-sync-badge](https://hackmd.io/Qt4AWbDfS5KtbKb-I3jY7Q/badge)](https://hackmd.io/Qt4AWbDfS5KtbKb-I3jY7Q) or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/conda-for-software-installation.md)

conda is a common (though not universal) system for installing software on Linux, Mac OS X, and (sometimes but not always) on Windows.

Its main features of interest are:

* you can install the conda system yourself on any computer, with no system privileges needed;
* you can install whatever software is available in "environments", which are isolated from each other
* this permits both installing & running software that conflicts with other software you have installed, AND sandboxing software by version (e.g. packages that need different versions of R and Python)
* you can also version pin software so that your results don't change

## Possible TODO items for collaboratory:

* install conda - see appendix.
* install the software you use for your computational work!
    * note, `r-base` installs R, and `python` installs Python.
* add the conda command line to your README.md in github!
* write an `environment.yml` file that installs some software! (see appendix for examples)
    * put that environment file in github!


## To create an environment named NAME containing python:

(and then activate it to use the software)

```
conda create -n NAME python
conda activate NAME
```

## To create an environment named NAME2 containing dplyr from an environment file:

```
cat > environment.yml <<EOF
channels:
 - conda-forge
 - bioconda
 - defaults
dependencies:
 - r-dplyr
EOF
conda env create -n NAME2 -f environment.yml
```

## conda environments must:
* contain all of the necessary software to run your pipeline

## conda environments should:
* be described in a environments file
* this environments file should be in version control

## conda environments may:
* contain version restrictions/version pinning, e.g. `python >=3.7,<3.10`

## things to discuss:
* interaction with system installed software and modules:
    * both conda and the module system 
    * whichever environment you activate last (`conda activate` or `module activate`) will take precedence
    * to add to the confusion, the module subsystem can load conda environments...
    * 
* R/Python conda installs
    * Titus recommends using both Python and R from conda, because it gives you precise & personal control over versions.
    * conda also supports binary installs of most common R and Python packages, e.g. `conda install r-dplyr`.
    * if you are running Python or R in a conda environment, and you install a package, it is installed within that conda environment. This is a nice (but maybe confusing) way to sandbox your packages and tie them to a particular R version.

## Session notes

(add notes here, everyone!)

## Documentation and tutorials and other resources

(add your favorites here!)

Introductory:
* Remote Computing tutorial: [Installing software on remote computers with conda](https://ngs-docs.github.io/2021-august-remote-computing/installing-software-on-remote-computers-with-conda.html)

## Appendix: installing conda

There are several ways to install conda; we recommend using [mambaforge](https://github.com/conda-forge/miniforge#mambaforge).

To install the June 2023 version of mambaforge on farm, you can avoid downloading mambaforge yourself and install it directly out of Titus's home directory. To do so, run:
```
echo source ~/.bashrc >> ~/.bash_profile
bash ~ctbrown/shared-conda-on-farm/Mambaforge-Linux-x86_64.sh
```

::::info
If you want to install the very latest version of mambaforge, or are not running on farm, you will want to download it yourself; to do that, run:
```
curl -LO https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh
bash Mambaforge-Linux-x86_64.sh 
```
::::

This will run a program that will ask a number of questions before installing conda; answer "yes" to all of them.

Then, log out and log back in.

Your shell prompt should now have `(base) ` at the beginning, indicating that conda was installed and you are in the base conda environment.

## Appendix: an example environment file

You can create a conda environment from an environment description file like so:

```
conda env create -n <name> -f <filename>.yml
```

An example `environment.yml` file:
```
channels:
 - conda-forge
 - bioconda
 - defaults
dependencies:
 - python
```

Another example `environment.yml` file, this one pinning the version of Python:
```
channels:
 - conda-forge
 - bioconda
 - defaults
dependencies:
 - python>=3.7,<3.10
```

You can see a more complicated environment file that installs a number of R packages [here](https://github.com/ngs-docs/2020-ggg-201b-rnaseq/blob/latest/binder/environment.yml).
