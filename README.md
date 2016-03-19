# Five Git Tips in Five Minutes

### For a SEM-JS lightning talk by Matt Morgan

#### Branch Your Work
Create and check out a branch at the same time

```
$ git checkout -b my-new-branch

```

List your branches

```
$ git branch -a
master
*my-new-branch
```

Switch back to master using a shortcut (no 'branch' command needed!)

```
$ git master
```

Or any other branch

```
$ git branch my-new-branch
```

---
#### Stash Your Work for Later
Stash your work to a stack for later recall
```
$ git stash
```

What do I have stashed anyway?
```
$ git stash list

stash@{0}: WIP on master: 049d078 added the index file
stash@{1}: WIP on master: c264051 Revert "added file_size"
stash@{2}: WIP on master: 21d80a5 added number to log
```

When you want to reapply your stashed changes:
```
$ git stash apply
```
This pops the top ref from the stack.
To be more picky:
```
$ git stash apply stash@{2}
```
---
#### Print Pretty Logs
Get an easier to read summary of your commit history

---
#### Edit Your Commit Messages
Made a typo?  Or maybe just a not-great commit message?

```
$ git commit --amend
```

This opens your text editor and lets you change the message on the last commit you made.  
Need to edit a different commit? No problem:

```
$ git commit --amend 21d80a5
```

---
#### Add a Remote for Your Repository

Need to point back at your repo on GitHub?
Let's call our remote `origin`:

```
$ git remote add origin https://github.com/matthewmorgan/spectacular-spraytan.git
```

`origin` is not magic or reserved.  We could easily use:

```
$ git remote add yggdrasil https://github.com/matthewmorgan/spectacular-spraytan.git
```

Then, to push our changes up to GitHub:

```
$ git push yggdrasil master
```

You can shortcut the need to specify the remote name by setting the remote as 'upstream':

```
$ git push -u yggdrasil master
```

To see all remotes associated with your repo:

```
$git remote -v
yggdrasil	https://github.com/matthewmorgan/spectacular-spraytan.git (fetch)
yggdrasil	https://github.com/matthewmorgan/spectacular-spraytan.git (push)
```

To delete a remote:

```
$ git remote rm yggdrasil
```
