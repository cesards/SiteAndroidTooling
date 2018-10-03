# Best practices

REVIEW THIS SECTION

[**Source**](https://speakerdeck.com/lemiorhan/10-git-anti-patterns-you-should-be-aware-of?slide=3)

- Don't push commits immediately after you commit: You miss the opportunity of reorganizing your commits by reset, rebase, commit or ammend in a safely way.
- Commit **Early**, Commit **Often**, Perfect **Later**, Publish **Once**.
- Merge master / develop into your branch regularly by squashing all commits into your feature branch.
- Add explanative commits.
- Use commit templates (typically file `.gitmessage` used by `.gitconfig` in the user folder). More information about it [**here**](https://robots.thoughtbot.com/better-commit-messages-with-a-gitmessage-template)
- I DONT UNDERSTAND THIS POINT VERY MUCH

`git pull` can cause duplicated commits in the graph. Rebase and force push (from your branch)
```
git rebase 
git push -f
```
and then pull a forced-pushed branch (with rebase)
```
git pull --rebase
```

- git reflog?
