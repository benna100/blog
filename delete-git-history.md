# Delete your git history

Taken from here: https://stackoverflow.com/questions/13716658/how-to-delete-all-commit-history-in-github



1. Checkout

   `git checkout --orphan latest_branch`

2. Add all the files

   `git add -A`

3. Commit the changes

   `git commit -am "commit message"`

4. Delete the branch

   `git branch -D main`

5. Rename the current branch to main

   `git branch -m main`

6. Finally, force update your repository

   `git push -f origin main`