# Git + GitHub

_Fundamentals of Git CLI commands and useful info for GitHub and repos_

## Common commands

<br>

**bold**

![Picture here](img/code_sample.png)

---

## **Resources**

<br>

How to undo the last commit ?

```
$ git commit -m "Something terribly misguided" # (0: Your Accident)
$ git reset HEAD~                              # (1)
[ edit files as necessary ]                    # (2)
$ git add .                                    # (3)
$ git commit -c ORIG_HEAD                      # (4)
```

[Read more](https://stackoverflow.com/questions/927358/how-do-i-undo-the-most-recent-local-commits-in-git)

<br>

**also**

<br>

[20 Common Git commands](https://dzone.com/articles/top-20-git-commands-with-examples)
