## Learn git
#To change the commit message \
`git commit --amend -m “New commit message”`

#To add a new file to the latest exists commit\
`git add file6` \
`git commit --amend --no-edit`

#Add and commit in one command\
`git commit -am "commit message"`

#Copy changes from another branch(Let’s have two branches, branchA and branchB. Instead of committing in both branches manually, we can use git rebase command.) \
`git checkout branchA` \
`git rebase branchB`

