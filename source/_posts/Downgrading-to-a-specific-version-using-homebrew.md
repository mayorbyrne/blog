---
title: Downgrading to a specific version using homebrew
date: 2024-09-25 21:59:36
tags:
---

After upgrading to the most recent version of a homebrew formula, I noticed a bug that wasn't present in the previous version. I wanted to downgrade to the previous version, but there was no real easy way of doing so. After doing a little research I found a way that is pretty simple.

1) First, you need to note the version number of the formula you want to downgrade to.
2) Uninstall the current formula.
3) Make a fork of the [homebrew-core](https://github.com/Homebrew/homebrew-core) repository. I noticed a TON of forks of this repository when I first navigated there, so that was how I knew I was on the right track.
4) Find the version of the formula you want to downgrade to, and copy the contents of the corresponding .rb file.
5) Switch back to the main branch of the forked repository, and find the latest .rb file for the formula you want to downgrade.
6) Replace the contents of the latest .rb file with the copied contents from step 4.
7) Commit and push the changes. You can do all of this through the github gui.
8) Ensure the formula is uninstalled so we don't get any conflicts with the following steps.
9) Install the formula using the following command: `brew install {github_username}/homebrew-core/{formula_name}`
10) You should now have the formula installed at the version you wanted to downgrade to.

More Info: [How to create and maintain a tap](https://docs.brew.sh/How-to-Create-and-Maintain-a-Tap)
```
