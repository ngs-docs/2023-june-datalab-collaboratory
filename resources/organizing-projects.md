---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - organizing your files - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: 
[![hackmd-github-sync-badge](https://hackmd.io/cY706EhiQU6Tw9azJ2L1lw/badge)](https://hackmd.io/cY706EhiQU6Tw9azJ2L1lw) or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/organizing-projects.md)

should:
* have all project-specific files under same top level directory
* files should be in git/github

may:
* clearly separate scripts/config from raw data from generated files
* contain all sbatch output files :)

how to get started:
* pick some part of your pipeline/scripts
* put them in git :)
* make sure they run
* make a copy of the git repo in a new location, run them from there

## Session notes

(add notes here, everyone!)

#### Wes's Wisdom

Incorporate a `README` file into everything repo/directory at the top-level.

RStudio is an excellent IDE and works well with github. RStudio enables a workflow for project management. Begin a project by hacking away in the `console` of the RStudio session.

Always create a `scratch` directory. As I find script and commands that work, I save them into this `scratch` folder. However, Do not include `scratch` folder to `.gitignore`, but while the scratch files tend to end up in github does not try to include them

Use a search function to identify previous script that has been used/works. Rstudio has search in the `history` tab, terminal has `history` command.

Once I find a command or script I like and works, I add the documentation to beginning of the script.

RStudio with `git` tab which has status symbols that can easily visualize what the `git status` returns. Also allows fine-grain commit (e.g. line selection commits)

Turning everything into functions makes analyses into flexible, modular workflows. Include a master file that creates the workflow.

Q: What are your paranoias for file management?
Often wonder if the analysis results has given true answers and worry about upon restart if the results will be the same (reproduciblitiy). Rely on history and version control to figure out the difference between results.


Finalize master scripts within `scratch ` directory and `cp` them into `R` directory for package creatation.

Everything I do I start in my `box` folder backed up on Box, I have a folder `projects`, and `git init` each one.

All paths should be relative paths, Rstudio projects feature this upon the start of a project. The rstudio projects save the relative path from the directory they are initialized in.

https://testthat.r-lib.org/ - Test the code ever time you integrate it as well as every time you commit to github.

If I share anything across packages/projects, it will be functions of a project. by create a package in R you simple have to tell collaborators to install the package you have written.

[webr ports the source code of R into javascript](https://docs.r-wasm.org/webr/latest/). OR https://blog.djnavarro.net/posts/2023-04-09_webr/
- https://github.com/d-rug/workshop-webr


Dani -- never ever save the R history and R data file.
I would also write notes to myself in the markdown to tell myself what I am doing, and what I want to do later with the script.

Titus -- I use a jupyter notebook similar to Dani. Once I have something I like I pull out the code chunks and turn them into functions. I am then left with a notebook that outline the project.

lintr identifies all the style errors in the code and styler fixes all the style errors in the code. Improved readability!!!

Find the tool that fits your brain.
Jupyter notebooks are terrible at tracing, and enforcing standards.

RMarkdown run from zero to complete. It is great to show a code narrative.

Quarto is the newest thing to look into.

name the function without calling it write only`install.packages` in the console and change the source code to use conda instead of R.


## Documentation and tutorials and other resources

(add your favorites here!)

https://datamanagement.hms.harvard.edu/plan-design/file-naming-conventions

https://snakemake.readthedocs.io/en/stable/snakefiles/deployment.html

https://github.com/d-rug/

https://github.com/ucdavisdatalab

https://github.com/ucdavisdatalab/workshop_intermediate_r

sphinx is a similar option. [Quarto](https://quarto.org/) is another option to render a webpage. `quarto render`