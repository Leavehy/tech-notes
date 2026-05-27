# Resolve "failed to push some refs" Error
## Problem
When running `git push origin main`, I got:
error: failed to push some refs to 'github.com:Leavehy/xxx.git'
hint: Updates were rejected because the remote contains work that you do not have locally.

## Cause
The remote repository has commits that are not in my local history (e.g., a README.md created via GitHub web).

## Solution
1. Fetch and merge the remote changes with `--allow-unrelated-histories`:
   ```bash
   git pull origin main --allow-unrelated-histories
2. Resolve any conflicts (if both sides added a README, keep the version you want).

3. Commit the merge:

   ```bash
   git add .
   git commit -m "Merge remote initial commit"

4. Push again:

   ```bash
   git push origin main