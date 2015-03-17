## Sync fork with upstream

```
git fetch upstream
git checkout devel
git merge upstream/devel
```

## Update github master branch from local devel branch

- Create pull request from local devel branch to github master branch
- Merge pull request on github master branch
- Sync local master branch
- Merge synced changes on local devel branch with following command:

```
git merge origin/master
```

## Resources

 - [Syncing a fork](https://help.github.com/articles/syncing-a-fork/)
