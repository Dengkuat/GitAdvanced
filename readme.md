## Git exercises

### Creating repo
```bash
    git clone https://github.com/Dengkuat/GitAdvanced.git
```

### Initializing Environment
```bash 
    DENGKUAT@MacBookPro GitAdvanced % touch test{1..4}.md
    DENGKUAT@MacBookPro GitAdvanced % git add test1.md
    DENGKUAT@MacBookPro GitAdvanced % git commit -m "chore: Create initial file"
    [main (root-commit) 750d9d6] chore: Create initial file
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test1.md
    DENGKUAT@MacBookPro GitAdvanced % git add test2.md
    DENGKUAT@MacBookPro GitAdvanced % git commit -m "chore: Create another file"
    [main 28d7bd4] chore: Create another file
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test2.md
    DENGKUAT@MacBookPro GitAdvanced % git add test3.md 
    DENGKUAT@MacBookPro GitAdvanced % git commit -m "chore: Create third and fourth files"
    [main 287d0bc] chore: Create third and fourth files
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test3.md
    DENGKUAT@MacBookPro GitAdvanced % 
```

# Part 1: Refining Git History (10 Challenges)

### 1.Missing File Fix:
```bash 
    DENGKUAT@MacBookPro GitAdvanced % git add test4.md
    DENGKUAT@MacBookPro GitAdvanced % git commit --amend -m "stages and added the test4.md"
    [main b3c743c] stages and added the test4.md
    Date: Mon Sep 8 16:03:14 2025 +0200
    2 files changed, 26 insertions(+)
    create mode 100644 README.md
    create mode 100644 test4.md
    DENGKUAT@MacBookPro GitAdvanced %    
```

### 2.Editing Commit History:
```bash 
        DENGKUAT@MacBookPro GitAdvanced % git log --oneline
    9499f6f (HEAD -> main) change before rebase
    b3c743c stages and added the test4.md
    287d0bc chore: Create third and fourth files
    28d7bd4 chore: Create another file
    750d9d6 chore: Create initial file
    DENGKUAT@MacBookPro GitAdvanced % git rebase -i HEAD~4
    Successfully rebased and updated refs/heads/main.
    DENGKUAT@MacBookPro GitAdvanced % git log --oneline   
    9499f6f (HEAD -> main) change before rebase
    b3c743c stages and added the test4.md
    287d0bc chore: Create third and fourth files
    28d7bd4 chore: Create another file
    750d9d6 chore: Create initial file
    DENGKUAT@MacBookPro GitAdvanced % git rebase -i HEAD~4
    Stopped at 28d7bd4...  chore: Create another file
    You can amend the commit now, with

    git commit --amend 

    Once you are satisfied with your changes, run

    git rebase --continue
    DENGKUAT@MacBookPro GitAdvanced % git commit --amend -m "Create second file"
    [detached HEAD 9d57a6c] Create second file
    Date: Mon Sep 8 16:01:09 2025 +0200
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test2.md
    DENGKUAT@MacBookPro GitAdvanced % git rebase --continue
    Successfully rebased and updated refs/heads/main.
    DENGKUAT@MacBookPro GitAdvanced % 
```

### 3.Keeping History Tidy - Squashing Commits:
```bash 
     DENGKUAT@MacBookPro GitAdvanced % git rebase -i --root
    [detached HEAD a80e7ca] chore: Squash intial and second commits
    Date: Mon Sep 8 16:00:31 2025 +0200
    2 files changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test1.md
    create mode 100644 test2.md
    [detached HEAD 160a933] change before rebase
    Date: Mon Sep 8 16:21:11 2025 +0200
    1 file changed, 59 insertions(+), 3 deletions(-)
Successfully rebased and updated refs/heads/main.
```
### 4. Splitting a Commit:
```bash
    DENGKUAT@MacBookPro GitAdvanced % git reset --soft 07a06aa^
    DENGKUAT@MacBookPro GitAdvanced % git reset
    DENGKUAT@MacBookPro GitAdvanced % git add test3.md
    DENGKUAT@MacBookPro GitAdvanced % git commit -m "Create Third File"
    [main 7d4f47d] Create Third File
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test3.md
    DENGKUAT@MacBookPro GitAdvanced % git add test4.md
    DENGKUAT@MacBookPro GitAdvanced % git commit -m "Create Fourth File"
    [main 388391b] Create Fourth File
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test4.md
    DENGKUAT@MacBookPro GitAdvanced % git log --oneline
    388391b (HEAD -> main) Create Fourth File
    7d4f47d Create Third File
    a80e7ca chore: Squash intial and second commits
```
<<<<<<< HEAD 

### 5. Advanced Squashing:
```bash
        DENGKUAT@MacBookPro GitAdvanced % git rebase -i HEAD~2
    pick 5258535 Create Third File
    squash 388391b Create Fourth File

    Create third and fourth files

    DENGKUAT@MacBookPro GitAdvanced % git log --oneline
    865f855 (HEAD -> main) Create third and fourth files
    a80e7ca chore: Squash initial and second commits
    07a06aa chore: Create third and fourth files
```

### 6. Dropping a Commit:
```bash
    DENGKUAT@MacBookPro GitAdvanced % git rebase -i HEAD~3
    Successfully rebased and updated refs/heads/main.
```

### 7. Reordering Commits:
```bash
    DENGKUAT@MacBookPro GitAdvanced % git log --oneline --graph --decorate
    * becc4d1 (HEAD -> main, origin/main) complete challenge 5 advanced squashing
    * 43416d2 Dropped commit message
    * e9e6d3f Remove old conflicting README files
    * 856b990 challenge 5
    * 7cd7169 challenge 4 splitting a commit into 2 separate commits
    * 5258535 Create Third File
    * a80e7ca chore: Squash initial and second commits
```

### 8. Cherry-Picking Commits:
```bash
   DENGKUAT@MacBookPro GitAdvanced % git checkout -b ft/branch
Switched to a new branch 'ft/branch'

DENGKUAT@MacBookPro GitAdvanced % echo "This is test 5 content" > test5.md

DENGKUAT@MacBookPro GitAdvanced % git add test5.md

DENGKUAT@MacBookPro GitAdvanced % git commit -m "Implemented test 5"
[ft/branch 790bf8f] Implemented test 5
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

DENGKUAT@MacBookPro GitAdvanced % git checkout main
M       readme.md
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

DENGKUAT@MacBookPro GitAdvanced % git checkout main
M       readme.md
Already on 'main'
Your branch is up to date with 'origin/main'.

DENGKUAT@MacBookPro GitAdvanced % git cherry-pick 790bf8f
[main 4faafe4] Implemented test 5
 Date: Tue Sep 9 15:23:25 2025 +0200
 1 file changed, 1 insertion(+)
 create mode 100644 test5.md

DENGKUAT@MacBookPro GitAdvanced % git checkout main
M       readme.md
Already on 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)
```
