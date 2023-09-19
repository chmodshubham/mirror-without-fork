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

If you wish to work with this local repository as a regular repository (and not just as a mirror), you might want to convert it from a bare clone to a regular one.

```bash
git config --unset core.bare
```

### Set Up Remotes for Your New Repository

By default, the repository you cloned (the original repository) is named `origin`. If you push without renaming this remote, you'll push to the original repository, which you might not have permissions to do. To avoid confusion or mistakes, it's recommended to rename the original repository's remote to something else (e.g., `upstream`).

```bash
git remote rename origin upstream
```

Then, add a new remote called 'origin' that points to your private repository:

```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_NEW_REPO.git
```

### Create a New Private Repository on GitHub

Head to your GitHub account and create a new repository. Make sure to set its visibility to `Private`.

### Push to Your New Private Repository

Push everything from your local mirror clone to your new private GitHub repository. Make sure you replace `YOUR_USERNAME` and `YOUR_NEW_REPO` with your GitHub username and your new repository's name, respectively.

```bash
git push --mirror https://github.com/YOUR_USERNAME/YOUR_NEW_REPO.git
```

You've now successfully cloned a repository and pushed it to a new private repository on your own GitHub account, complete with all its branches and releases.

>**Note**
>Ensure you're not violating any licenses or terms of service by cloning and making private copies of repositories. Always refer to the license of the original repository to determine what is and isn't permissible.
