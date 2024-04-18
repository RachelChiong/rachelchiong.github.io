# Setting up submodules in your repo
Sometimes, when working cross-project or with code that's been cloned from
elsewhere, it helps to add them as a submodule to a main repo.

For example, for assignment 2 I need to write a blog (this one!),
generate a fingerprint identifier GUI and train image classification models
on a CPU and GPU, all of which are in different repos upon set up.

Without submoduling, each time I log in to a remote desktop session to
remote lab computers, I'd need to clone each of these repos individually
which is a lot more effort than it's worth.

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


## Steps to clone your repo with submodules
Now, when  
