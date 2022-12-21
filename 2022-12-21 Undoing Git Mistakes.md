
#### Editing old commit messages
how far back in time do I want to go? how many commit messages back?
Go back as far as the parent of the commit message
`git rebase -i HEAD~3` 

the interactive presents the messages from oldest to newest

#### Deleting Commits
One can delete old commit messages with interactive rebase
the action word for deleting the commit from the history is  `drop`

#### Combining commits
Generally you want to make small commits instead of huge unless you have over done it. 
using `squash` will combine messages from above and below the squash then you will create a new commit message for both.

#### Adding a change to an old commit 
`fixup` takes the banaid commit and combines it with the new one and cleans up the git history
Git changes the order of the git history with fixup, its like a squash and combines with the line above. 
`git rebase -i HEAD~4 autosquash`
git tower `hold` option and select your commit message and move it to the desire order

#### Git Interactive changes 
Caution when rewriting commits. Don't use rebase for commits you have pushed to the remote 