# Migrate Repo from Bitbucket to Github

Note: only **public** repo should be migrated from bitbucket to github.
If you have a private github repo that you want it to
be under `github.com/aicip`, you should do "Transfer ownership" through
"Settings" page. 

## Step 0: Prerequisites

* You should either have or created a github account.
* You should send that github account ID to `hqi@utk.edu` and approved to be member of AICIP organization.

## Step 1: clone bitbucket repo to your local disk

you can either clone bitbucket repo through `https://` or `ssh` if you
have added your ssh key to the bitbucket. For example:

    git clone git@bitbucket.org:USERNAME/BB_REPO_NAME.git

## Step 2: create new repo under [http://github.com/aicip](http://github.com/aicip)

This is done through github's web interface. You can name it the same or
differently from bitbucket. It is a good practice to provide a short description
on what this repo is about.

## Step 3: change `origin` from bitbucket to github 

For your local repo that was just cloned from bitbucket:

    cd BB_REPO_NAME
    git remote set-url origin git@github.com:aicip/NEW_REPO_NAME.git
    git push -u origin master

Replace `NEW_REPO_NAME` with the repo name you just created on github.com.

If everything is fine, then the migration is complete. You can now delete the
original bitbucket repo and leave a redirection url, e.g.,
`http://github.com/aicip/NEW_REPO_NAME`.


## Trouble shooting

Bitbucket has generous 1G soft limit and 2G hard limit on repo size, which is
significantly larger than github (200MB). In the case of your repo size is too
big for github, the migration will fail. Here is a few tips to help.


* Large file is often frowned upon in code repo. You should consider remove it
  and host the file elsewhere. However, removing a file from git is tricky (as
  you have to rewrite history, doing just `git rm` won't work).
  [BFG](https://rtyley.github.io/bfg-repo-cleaner/) is a tool that greatly
  simplify the process. It can be used as:

      java -jar ~/Downloads/bfg-1.13.0.jar --strip-blobs-bigger-than 100M

* For either the data file, or presentations etc, you can ask `hqi@utk.edu` to create
  a place holder of Team Drive on Google Drive, and make it publicly accessible

  




