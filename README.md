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

```bash
git config --unset core.bare
```

### Create a New Private Repository on GitHub

Head to your GitHub account and create a new repository. Make sure to set its visibility to `Private`.

### Set Up Remotes for Your New Repository

By default, the repository you cloned (the original repository) is named `origin`. If you push without renaming this remote, you'll push to the original repository, which you might not have permissions to do. To avoid confusion or mistakes, it's recommended to rename the original repository's remote to something else (e.g., `upstream`).

```bash
git remote rename origin upstream
```

After renaming the original remote, you can set your private repository as the `origin`, which is the standard name for the primary remote in most repositories. This makes it clear that when you do standard operations like git push or git pull, you're interacting with your private repository and not the original one.

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
