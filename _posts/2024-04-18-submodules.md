---
layout: post
title:  "Setting up and using Submodules in your Repo"
author: Rachel
image: ../images/submodules-img.png
---
# Setting up submodules in your repo
Sometimes, when working cross-project or with code that's been cloned from
elsewhere, it helps to add them as a submodule to a main repo. For example,
for assignment 2 I need to write a blog (this one!), generate a fingerprint
identifier GUI and train image classification models
on a CPU and GPU, all of which are in different repos upon set up.

Without submoduling, each time I log in to a remote desktop session to
remote lab computers, I'd need to clone each of these repos individually
which is a lot more effort than it's worth.

 ![Submodules on Github](/images/submodules-img.png)

1. TOC
{:toc}

## Steps to add a submodule repo
### 1. Clone your main repo
```sh
git clone <YOUR_MAIN_REPO>
```

### 2. Clone in your sub-module repo/s
Just clone in your submodules like normal here. The magic is in the next step.

```sh
cd <YOUR_MAIN_REPO>
git clone <YOUR_SUBMODULE_REPO> <SUBMODULE_REPO_NAME>
```

### 3. Add your repo to git
```git
git submodule add <YOUR_SUBMODULE_REPO_LINK> <SUBMODULE_REPO_NAME>
```
If successful, you should get a message saying that it has been successfully added.

And voila! You should be able to verify that a submodule has been added on github.

## Clone your repo with submodules
Now, when you're cloning the main repo to a new destination, you'll need to add
the ```recurse-submodules``` flag. This ensures that the contents of the submodules
will also be cloned in. They will also retain the branch/commit number you're using
for the submodule as well (if it happens to be different).

```git
git clone --recurse-submodules <YOUR_REPO_PATH>
```

## Troubleshooting and Warnings
Submodules can be very tricky and cause grief if not used properly. A couple good rules
of thumb to follow are:
1. Only make a submodule of a repo once (don't clone it into two spots within your main repo)
2. Only use submodules when there is some level of dependency. I've used submodules
just because it helps with organisation. But this can get gnarly very quicky with an
abundance of git issues.

Here are some troubleshooting guides:
### Removing a submodule
1. Delete the relevant lines from the ```.gitmodules``` file. The lines should look
like this:
```git
[submodule "<SUBMODULE_REPO_PATH>"]
	path = <SUBMODULE_REPO_PATH>
	url = https://github.com/<SUBMODULE_REPO_URL>
```

2. Remove the link via git in the command line:
```git
git rm --cached <SUBMODULE_REPO_PATH>
```

3. Finally, remove the folder locally if it still exists. Then stage and commit your changes
```git
rm -R <SUBMODULE_REPO_PATH>
```

Also, be prepared to deal with an abundance of merge conflicts and branch rebasing.
It's definitely not for the faint of heart!