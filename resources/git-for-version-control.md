---
tags: summer2023, collaboratory
---

[toc]

# DataLab Collaboratory - git & github resources - June 2023

[Go back to main schedule page](https://hackmd.io/KhkZGZhyRt6pu4lbEHi6ow?view)

Edit: [![hackmd-github-sync-badge](https://hackmd.io/M8Ztk4KpT-mYquotj1bOFQ/badge)](https://hackmd.io/M8Ztk4KpT-mYquotj1bOFQ) or or on [![github](https://raw.githubusercontent.com/ngs-docs/2023-june-datalab-collaboratory/main/images/GitHub_Logo.png)](https://github.com/ngs-docs/2023-june-datalab-collaboratory/blob/main/resources/git-for-version-control.md)

git (well, version control more generally) is an invaluable tool for safeguarding your work. It gives Titus the heeby jeebies to think about making changes to files without tracking them somehow! And that's what he uses git for!

Combined with github, git is even more powerful, because now you can have backups and also share your files with others (including future you). Also, Titus really likes the github interface for browsing files, and the github issue tracker is a really useful way to track research results for yourself, too!

## git repos should:

* contain all hand-generated scripts and config files, but not data files or anything > 1 MB.
* be linked to a github (or other) hosting site
* be the place you run things out of - as in, when you do a `git clone` to create a new repo, you can run your scripts directly from that without any changes.
* contain a README that has a minimal description and getting-started list

## git repos can:

* use branches to manage long running "experimental" changes to your files
* use releases to checkpoint your analyses
* be linked to zenodo via github to support backups/DOI minting upon releases

## advice & traps to avoid:

* don't git add all; use .gitignore too
* avoid committing large files! use git status first
* don't clean up or edit files before adding to version control; clean up _after_ adding to version control!

## getting started from an existing project:
* `git init` in top level project directory
* `git add <filename(s)>` to stage file for commit;
* `git commit -m "adding files"` to commit;
* To push to github:
  * create an empty github project
  * copy/paste `git remote add ...` and `git push ...` commands onto command line to connect your repositories and push commit from your working repo to github
  * verify your files show up!
* repeat until all of your scripts etc are on github.

continuing with git:
* edit files, and/or use `git mv <from> <to>` to rename them;
* `git status` to see what has changed overall;
* `git add <...>` to stage files/changes for commit;
* list filenames in `.gitignore` to 
* `git commit -m "description"` to commit; 
* `git push` to push commits to github;

more advanced topics to consider:
* add a README! (you can write one in hackmd.io if you like, and then upload it directly to github)
* try running your code directly from your repo!
* edit your files to use relative paths instead of absolute paths!
* using branches and/or pull requests!
* using github issues to track your research results!
* connecting to zenodo and making "releases" to generate DOIs for your software!

## Session notes

(add notes here, everyone!)

## Documentation and tutorials and other resources

(add your favorites here!)

Introductory:
* Remote Computing tutorial: [Keeping track of your files with version control](https://ngs-docs.github.io/2021-august-remote-computing/keeping-track-of-your-files-with-version-control.html)

More advanced:
* [Using branches and pull requests - GitHub Flow](https://docs.github.com/en/get-started/quickstart/github-flow)

## Appendix: setting up a Personal Authentication Token

You will probably need to set up a PAT to communicate with github...

### Go to settings, generate classic token

![](https://hackmd.io/_uploads/SyYxwgg0s.png)

### Give it a name, expiration date, and "repo" scope

![](https://hackmd.io/_uploads/BktZDggCs.png)

### Copy this ghp_ string as your password to github on farm

![](https://hackmd.io/_uploads/S1MGDgxAs.png)

### Use your github username and the ghp_ string as your password when cloning

![](https://hackmd.io/_uploads/B1qfPglRo.png)
