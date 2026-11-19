# Git Commands Cheat Sheet

A beginner-friendly Git command reference for using Git in the VS Code
terminal.

## 1. Git configuration

``` bash
git --version
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list
git config --global init.defaultBranch main
```

  ---------------------------------------------------------------------------------------
  Command                                             Purpose
  --------------------------------------------------- -----------------------------------
  `git --version`                                     Check the installed Git version

  `git config --global user.name "Your Name"`         Set your Git username

  `git config --global user.email "your@email.com"`   Set your Git email

  `git config --list`                                 Display Git configuration

  `git config --global init.defaultBranch main`       Set `main` as the default initial
                                                      branch
  ---------------------------------------------------------------------------------------

## 2. Create or download a repository

``` bash
git init
git clone https://github.com/USERNAME/REPOSITORY.git
git status
```

  Command           Purpose
  ----------------- --------------------------------------
  `git init`        Initialize Git in the current folder
  `git clone URL`   Clone a remote repository
  `git status`      Show the current working-tree status

## 3. Stage and commit changes

``` bash
git add filename
git add .
git add -A
git commit -m "Your commit message"
git commit -am "Update tracked files"
git diff
git diff --staged
```

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git add filename`                  Stage one file

  `git add .`                         Stage changes in the current
                                      directory

  `git add -A`                        Stage all changes, including
                                      additions and deletions

  `git commit -m "message"`           Commit staged changes

  `git commit -am "message"`          Stage and commit modified/deleted
                                      tracked files; does not add new
                                      untracked files

  `git diff`                          Show unstaged changes

  `git diff --staged`                 Show staged changes
  -----------------------------------------------------------------------

## 4. Connect to GitHub and synchronize

Replace the example URL with your own GitHub repository URL.

``` bash
git remote -v
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
git remote remove origin
git push -u origin main
git push
git pull origin main
git fetch
```

  Command                           Purpose
  --------------------------------- ------------------------------------------
  `git remote -v`                   List configured remote URLs
  `git remote add origin URL`       Add a remote named `origin`
  `git remote set-url origin URL`   Change the remote URL
  `git remote remove origin`        Remove the remote named `origin`
  `git push -u origin main`         Push `main` and set its upstream
  `git push`                        Push to the configured upstream
  `git pull origin main`            Fetch and merge the remote `main` branch
  `git fetch`                       Download remote updates without merging

## 5. Branch commands

``` bash
git branch
git branch feature-name
git switch feature-name
git switch -c feature-name
git branch -M main
git merge feature-name
git branch -d feature-name
git branch -D feature-name
```

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git branch`                        List local branches

  `git branch feature-name`           Create a branch

  `git switch feature-name`           Switch to a branch

  `git switch -c feature-name`        Create and switch to a branch

  `git branch -M main`                Rename the current branch to `main`

  `git merge feature-name`            Merge the named branch into the
                                      current branch

  `git branch -d feature-name`        Delete a merged branch

  `git branch -D feature-name`        Force-delete a branch
  -----------------------------------------------------------------------

## 6. Undo and restore commands

``` bash
git restore filename
git restore .
git restore --staged filename
git reset --soft HEAD~1
git reset --mixed HEAD~1
git revert COMMIT_ID
git commit --amend
```

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git restore filename`              Discard unstaged changes in a file

  `git restore .`                     Discard all unstaged tracked-file
                                      changes in the current directory

  `git restore --staged filename`     Unstage a file while keeping its
                                      working-tree changes

  `git reset --soft HEAD~1`           Move the branch back one commit and
                                      keep changes staged

  `git reset --mixed HEAD~1`          Move the branch back one commit and
                                      keep changes unstaged

  `git revert COMMIT_ID`              Create a new commit that reverses a
                                      previous commit

  `git commit --amend`                Edit the most recent commit
  -----------------------------------------------------------------------

**Caution:** `git restore` can discard work. `git reset --hard` can
permanently discard uncommitted changes. Avoid rewriting commits that
have already been shared unless you understand the impact.

## 7. Stash commands

``` bash
git stash
git stash list
git stash pop
git stash apply
git stash drop
git stash clear
```

  Command             Purpose
  ------------------- --------------------------------------------
  `git stash`         Temporarily save tracked working changes
  `git stash list`    List saved stashes
  `git stash pop`     Apply and remove the latest stash
  `git stash apply`   Apply the latest stash without removing it
  `git stash drop`    Delete the latest stash
  `git stash clear`   Delete all stashes

## 8. Commit history and inspection

``` bash
git log
git log --oneline
git log --oneline --graph --all
git show
git show COMMIT_ID
git diff
git blame filename
git reflog
git shortlog
git ls-files
```

  -----------------------------------------------------------------------
  Command                             Purpose
  ----------------------------------- -----------------------------------
  `git log`                           Show commit history

  `git log --oneline`                 Show compact commit history

  `git log --oneline --graph --all`   Show a graph of branches and
                                      commits

  `git show`                          Show details of the latest commit

  `git show COMMIT_ID`                Show details of a specific commit

  `git blame filename`                Show the commit and author for each
                                      line

  `git reflog`                        Show recent movements of HEAD

  `git shortlog`                      Summarize commits by author

  `git ls-files`                      List files tracked by Git
  -----------------------------------------------------------------------

## 9. Tags

``` bash
git tag
git tag v1.0
git tag -d v1.0
git push origin v1.0
git push origin --tags
```

  Command                    Purpose
  -------------------------- --------------------------
  `git tag`                  List tags
  `git tag v1.0`             Create a lightweight tag
  `git tag -d v1.0`          Delete a local tag
  `git push origin v1.0`     Push one tag
  `git push origin --tags`   Push all local tags

## 10. Clean untracked files

``` bash
git clean -n
git clean -f
```

  Command          Purpose
  ---------------- -----------------------------------------------
  `git clean -n`   Preview untracked files that would be removed
  `git clean -f`   Remove untracked files

**Caution:** `git clean -f` deletes untracked files. Review the preview
first.

## 11. Upload a new project to GitHub

1.  Open your project folder in VS Code.
2.  Create an empty repository on GitHub. Do not initialize it with a
    README if you plan to push an existing local project.
3.  Open the VS Code terminal in the project folder.
4.  Run the following commands one at a time. Replace the URL with your
    repository URL.

``` bash
git init
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git add .
git status
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git push -u origin main
```

After the push succeeds, refresh your GitHub repository page to see the
uploaded files.

## 12. Daily Git workflow

Use this whenever you have made changes to your project:

``` bash
git status
git add .
git commit -m "Describe your changes"
git push
```

If you are collaborating with others, first get the latest remote
changes when appropriate:

``` bash
git pull
```

## 13. Example `.gitignore` for a React + Node.js project

Create a file named `.gitignore` in your project root. Adapt it if your
project has different folders.

``` gitignore
node_modules/
.env
.env.*
!.env.example
dist/
build/
coverage/
.DS_Store
```

Never commit real passwords, API keys, MongoDB connection strings, or
JWT secrets. Keep required environment-variable names in an
`.env.example` file with placeholder values only.

## 14. Important Git terminology

  Term             Meaning
  ---------------- ---------------------------------------------------
  Git              A version control system
  GitHub           A platform for hosting Git repositories
  Repository       A project whose changes are tracked by Git
  Commit           A recorded snapshot of staged changes
  Push             Send local commits to a remote repository
  Pull             Fetch remote changes and integrate them
  Fetch            Download remote updates without integrating them
  Clone            Copy a remote repository locally
  Branch           An independent line of development
  Merge            Combine changes from another branch
  Staging area     The place where changes are prepared for a commit
  HEAD             Reference to the currently checked-out commit
  Merge conflict   A situation Git cannot resolve automatically

## 15. The commands to learn first

Start with these everyday commands:

``` bash
git init
git clone URL
git status
git add .
git commit -m "message"
git push
git pull
git fetch
git branch
git switch
git merge
git restore
git log
```

------------------------------------------------------------------------

**Tip:** Run `git status` often. It helps you understand which files are
modified, staged, untracked, or ready to commit.
