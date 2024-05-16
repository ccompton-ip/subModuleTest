# subModuleTest

[Git Submodule Doc](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

Checkout with 
`git clone --recurse-submodules https://github.com/ccompton-ip/subModuleTest.git`

Run `git config --local include.path ../.gitconfig` to point git at the `.hooks` directory for githooks

### Pulling in Upstream Changes from the Submodule Remote

Update submodules with
`git submodule update --remote <SubModule>` so for this `git submodule update --remote .hooks`

Update default branch for the previous command to pull from
`git config -f .gitmodules submodule.<submodule>.branch <banch>`

### Pulling Upstream Changes from the Project Remote
Simply executing git pull to get your newly committed changes is not enough.

By default, the git pull command recursively fetches submodules changes, as we can see in the output of the first command above. However, it does not update the submodules. This is shown by the output of the git status command, which shows the submodule is “modified”, and has “new commits”. 

To finalize the update, you need to run git submodule update. `git submodule update --init --recursive`
Note that to be on the safe side, you should run git submodule update with the --init flag in case the MainProject commits you just pulled added new submodules, and with the --recursive flag if any submodules have nested submodules.
