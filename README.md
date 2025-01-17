# RebornOS ISO - GNOME Minimal

The official RebornOS ISO source.

> **Note**: The script for setting up prerequisites will only build on *Arch Linux* and its derivatives (that use `pacman`, and the Arch Linux package repositories)

The upstream is [the releng config of archiso](https://gitlab.archlinux.org/archlinux/archiso/-/tree/master/configs/releng).
This repository has been created using *git subtree*. [Please keep it updated by git merging with latest upstream changes](https://github.com/RebornOS-Developers/gnome-minimal-iso#3-update)

## 1. Cloning

In order to download the source code to your local computer for testing, or for development, you can clone from the remote repository using either SSH, or HTTPS. Below are instructions on how to do so using Gitlab hosted code as remote.

### HTTPS

```bash
git clone https://github.com/RebornOS-Developers/gnome-minimal-iso.git 
```

OR

### SSH

```bash
git clone git@github.com:RebornOS-Developers/gnome-minimal-iso.git
```

## (Optional) Clean-up old packages and directories

You usually do not need to do this unless the build fails.
The build process following cleanup is usually slow because it has to start from scratch. Change to the project directory (`cd gnome-minimal-iso`) and run
```bash
sh scripts/clean.sh
```

## 2. Build

The below script will build the ISO image (and install any prerequisites). Change to the project directory (`cd gnome-minimal-iso`) and run

```bash
sh scripts/build.sh
```
Check the `output/` directory for the output ISO file.

## 3. Update

To keep this project in sync with the upstream ArchISO Releng configuration, please follow the below steps. Change to the project directory (`cd gnome-minimal-iso`) before continuing...

1. **Fetch changes from the upstream GitLab source**: The below script first clones the [upstream ArchISO](https://gitlab.archlinux.org/archlinux/archiso) to the `archiso` branch (force overwrites it) and then uses *git subtree* to copy over the [releng configuration directory](https://gitlab.archlinux.org/archlinux/archiso/-/tree/master/configs/releng) to the `releng` branch.
```sh
sh scripts/update-releng-branch.sh
```

2. **Merge upstream changes**
```sh
git checkout main

git merge releng
```

3. **Manually handle merge conflicts**: Follow [this guide for commandline operations](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts) or [this guide if you are using *Visual Studio Code*](https://code.visualstudio.com/docs/sourcecontrol/overview#_merge-conflicts).

4. **Push updates back to the project**: After all the merge conflicts are handled and you stage all the changes, you are ready to push the updates with `git push`.
