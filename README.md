# Clone Repository without creating fork

### Clone the Original Repository

Clone the repository you want to your local system.
```bash
git clone --mirror https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```
   
The `--mirror` option ensures you clone all branches and tags.

### Navigate to the Cloned Directory

```bash
cd ORIGINAL_REPOSITORY
```

### Convert Your Mirror Clone to a Regular Clone(Optional)

When you create a mirror clone (`git clone --mirror`), you're creating what's called a **bare** repository. A bare repository has only the Git internal data and doesn't have a working directory. This means you can't see the files, make changes, or create new commits in the usual way.

For some tasks, a bare repository is perfect. For example, if you just want to copy everything from one remote repository to another without making any changes in between, a mirror clone is great.

However, suppose you later decide that you'd like to work with this local clone in the usual way (e.g., making changes, adding commits). In that case, you need to convert it into a regular repository, which does have a working directory.

The command `git config --unset core.bare` essentially tells **Git**, "Hey, this repository shouldn't be considered 'bare' anymore." Once you run this command, the repository becomes a regular one, and you can interact with it just like any other local repository.

### Create a New Private Repository on GitHub

Head to your GitHub account and create a new repository. Make sure to set its visibility to `Private`.

### Set Up Remotes for Your New Repository

The term `origin` in Git refers to the default remote repository from which you cloned. It's like a nickname for the repository's URL. When you make a mirror clone, `origin` refers to the repository you cloned from.

If you plan to push to a different repository (like your private one), you might get confused or make mistakes if you keep calling the original repository `origin`.

The term `upstream` is conventionally used in the open-source community to refer to the main/original repository from which a fork is derived. By renaming the original `origin` to `upstream`, you're aligning with this convention. It helps clarify that `upstream` is the source or main repository, while `origin` will be your own repository.

However, `upstream` is just a convention. You could name it anything else you like. Some alternatives might be `source`, `mainrepo`, or `original`, but `upstream` is widely understood in many Git contexts.

```bash
git remote rename origin upstream
```

After renaming the original remote, you can set your private repository as the `origin`, which is the standard name for the primary remote in most repositories. This makes it clear that when you do standard operations like `git push` or `git pull`, you're interacting with your private repository and not the original one.

```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_NEW_REPO.git
```

### Push to Your New Private Repository

Push everything from your local mirror clone to your new private GitHub repository. Make sure you replace `YOUR_USERNAME` and `YOUR_NEW_REPO` with your GitHub username and your new repository's name, respectively.

```bash
git push --mirror https://github.com/YOUR_USERNAME/YOUR_NEW_REPO.git
```

You've now successfully cloned a repository and pushed it to a new private repository on your own GitHub account, complete with all its branches and releases.

>**Note**
>Ensure you're not violating any licenses or terms of service by cloning and making private copies of repositories. Always refer to the license of the original repository to determine what is and isn't permissible.
