# RepSol

Small repo of utils I found useful at 360Learning. Provided as is, with no guarantee. Feel free to use/modify/contribute.

Most scripts were built to work with zsh, but should work with bash (or other shells) with minor modifications.

## Specific script advice

### open-ready-prs

This script waits for your checks to complete before opening your PRs for review. Best used as an hourly cron (`cd <THIS_FOLDER> && . .env && ./open-ready-prs`)
Needs `GIT_FOLDER`, `READY_PRS_SOURCE_FILE` and `READY_PRS_REVIEWERS` environment variables (example in `.env.example`)

`READY_PRS_SOURCE_FILE` should contain ready PRs, one line per PR in the following format:
```
PR_NUMBER,SHOULD_BYPASS_SONAR_BOOLEAN
```
If SHOULD_BYPASS_SONAR_BOOLEAN is "true", the script will open the PR even if the Sonar check fails (useful when you know you will not test client files such as `routes.ts`).

### git-push-force-safe

This script will check if a non-draft PR exists for this branch and block force pushing if it's the case.

I recommend aliasing the command you use for force pushing to this script (for example, I ran `git config alias.pf '!/home/filip/repsol/git-push-force-safe'`).

If you want to bypass the script (for any reason), you can still run `git push --force` or `git push --force-with-lease`.

Note that it adds a minor overhead if your connection is very slow.
