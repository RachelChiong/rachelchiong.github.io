---
layout: post
title:  "Setting up and using Submodules in your Repo"
---

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