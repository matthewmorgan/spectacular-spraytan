# Five Git Tips in Five Minutes

### For a SEM-JS lightning talk by Matt Morgan

---

# Git Orientation

* Repos have branches: bugfix or feature
* Branches have commits: logical units of work 
* Commits have refs: unique IDs

No hard and fast rules, but usually a commit is a logical unit of work that supports a feature or bug fix.  Branches are usually temporary, and merged back in to master when the feature or bugfix is complete.

---

#### Always Branch Your Work from Master

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
#### Not Ready to Commit?  
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

```
$ git log --color --graph \
--pretty=format:'%C(bold white)%h%Creset -%C(bold green)%d%Creset %s %C(bold green)(%cr)\
%Creset %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative

* 15635d5 - (HEAD -> master) Add more content (2 minutes ago) <Matthew Morgan>
* 3036572 - Initial commit (15 minutes ago) <Matthew Morgan>
```

The above command can and should be made in to any easy, short alias, like `git lg`.  
We can talk about that another time.

You can also get a nice summary of what's changed recently:

```
$ git log --since='last month' \
--pretty=format: --name-only | sort | uniq -c | sort -rg | head -10

   7 src/com/dulcetsoftware/mmi/backoffice/ItemEditor.java
   4 src/com/dulcetsoftware/mmi/backoffice/ItemList.java
   3 src/com/dulcetsoftware/mmi/backoffice/Test.java
   3 src/com/dulcetsoftware/mmi/backoffice/SuggestedOrdersList.java
   3 src/com/dulcetsoftware/mmi/backoffice/ParScheduleEditor.java
   3 src/com/dulcetsoftware/mmi/backoffice/ParScheduleEditor.form
   3 src/com/dulcetsoftware/mmi/backoffice/GenerateSuggestedPurchases.java
   3 src/com/dulcetsoftware/mmi/backoffice/GenerateOrders.java
   2 src/com/dulcetsoftware/mmi/backoffice/VendorItemPackEditor.java
```

---
#### Write Good Commit Messages
Made a typo?  Or maybe just a not-great commit message?

```
$ git commit --amend
```

This opens your text editor and lets you change the message on the last commit you made.  


---
#### Share Your Work with Others Using Remotes

Need to point back at your repo on GitHub?
Let's call our remote `origin`:

```
$ git remote add origin git@github.com:matthewmorgan/spectacular-spraytan.git
```

`origin` is not magic or reserved.  We could easily use:

```
$ git remote add yggdrasil git@github.com:matthewmorgan/spectacular-spraytan.git
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
---
#### GitHub Time Machine

```
$ git reset --soft XXXXXX && git commit
```

---
#### Cherry Pick One Commit

Grab all the changes made in one commit, from any branch, and replay them on to your current checked-out branch:

```
$ git cherry-pick XXXX
```

---
#### Save Everything

My git anxiety largely went away when I realized that `commit` and even `reset --hard` don't really remove anything.  Your work is all still there:

```
$ git reflog
3c2d08b HEAD@{0}: commit: Add logging format tips
15635d5 HEAD@{1}: commit: Add more content
3036572 HEAD@{2}: commit (initial): Initial commit
```

Any of the above listed refs can be checked out to recover work that you didn't mean to blow away.

Thanks very much to @BrianGenisio, @IanVS, @jrwren, @MiguelCastillo, and @StevenACoffman for their initial thoughts on useful tips.

---

# Final Thoughts

* Branch your work
* Commit early and often

github: @matthewmorgan

email: mail.matt.morgan@gmail.com

this file: https://github.com/matthewmorgan/spectacular-spraytan.git

slide tool: https://gnab.github.io/remark/remarkise


