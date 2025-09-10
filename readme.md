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

### 9. Visualizing Commit History (Bonus):
```bash
    DENGKUAT@MacBookPro GitAdvanced % git log --graph --oneline --all
* 6d4d75c (HEAD -> main, origin/main)  Cherry-Picking Commits:
* 1ab013e  Cherry-Picking Commits:
*   8b9c0f1 Merge branch 'ft/branch'
|\  
| * 790bf8f Implemented test 5
* | 4faafe4 Implemented test 5
|/  
* e3ee35b challenege 7
* 43416d2 Dropped commit message
* becc4d1 complete challnege 5 advanced squashing
* e9e6d3f Remove old conflicting README files
| *   202fd7c (refs/stash) WIP on (no branch): 65
7793d complete challnege 5 advanced squashing
| |\  
| | * 8e5c04a index on (no branch): 657793d compl
ete challnege 5 advanced squashing
| |/  
| * 657793d complete challnege 5 advanced squashi
ng
|/  
*   9d5cceb Merge commit 'ced368e'
|\  
| * ced368e completed challenge 5 advanceed sqaus
hing
| * 128ee9b Create third and fourth files
* | 856b990 challenge 5
* | 7cd7169 challenge 4 spliting a commit into 2 
separate commits
* | 5258535 Create Third File
|/  
* a80e7ca chore: Squash intial and second commits
(END)
```

### 10. Understanding Reflogs (Bonus):
```bash
    DENGKUAT@MacBookPro GitAdvanced % git reflog
6d4d75c (HEAD -> main, origin/main) HEAD@{0}: commit: Cherry-Picking Commits:
1ab013e HEAD@{1}: commit: Cherry-Picking Commits:
8b9c0f1 HEAD@{2}: merge ft/branch: Merge made by the 'ort' strategy.
4faafe4 HEAD@{3}: checkout: moving from ft/branch to main
790bf8f HEAD@{4}: checkout: moving from main to ft/branch
4faafe4 HEAD@{5}: checkout: moving from ft/branch to main
790bf8f HEAD@{6}: checkout: moving from rebase-pr
actice to ft/branch
43416d2 HEAD@{7}: rebase (abort): returning to re
fs/heads/rebase-practice
4faafe4 HEAD@{8}: checkout: moving from main to m
ain
4faafe4 HEAD@{9}: cherry-pick: Implemented test 5
e3ee35b HEAD@{10}: checkout: moving from main to 
main
e3ee35b HEAD@{11}: checkout: moving from ft/branc
h to main
790bf8f HEAD@{12}: commit: Implemented test 5
e3ee35b HEAD@{13}: checkout: moving from main to 
ft/branch
e3ee35b HEAD@{14}: commit: challenege 7
43416d2 HEAD@{15}: checkout: moving from rebase-p
ractice to main
43416d2 HEAD@{16}: checkout: moving from main to 
rebase-practice
43416d2 HEAD@{17}: checkout: moving from 1fc232f8
8cb6445acaa31a3f66c6bb39987418b9 to main
1fc232f HEAD@{18}: commit: challenege 7
f348c39 HEAD@{19}: rebase (start): checkout f348c
39f86cdb1c4cc1be2af331a1833fad5cf7d
43416d2 HEAD@{20}: checkout: moving from main to 
rebase-practice
43416d2 HEAD@{21}: checkout: moving from main to 
main
43416d2 HEAD@{22}: rebase (abort): returning to r
efs/heads/main
bce9894 HEAD@{23}: rebase (pick): completed chall
enge 5 advanceed sqaushing
7cd7169 HEAD@{24}: rebase (start): checkout HEAD~
5
43416d2 HEAD@{25}: rebase (finish): returning to 
refs/heads/main
43416d2 HEAD@{26}: rebase (finish): refs/heads/ma
in onto 9d5ccebc3e7f950f5b4e54443fb53b0451b4c2c9
43416d2 HEAD@{27}: checkout: moving from main to 
main
43416d2 HEAD@{28}: checkout: moving from becc4d15
0009f0adb24992f38df4e7c0ba9eeb10 to main
becc4d1 HEAD@{29}: reset: moving to origin/main
657793d HEAD@{30}: rebase (pick): complete challn
ege 5 advanced squashing
9d5cceb HEAD@{31}: rebase (start): checkout HEAD~
3
43416d2 HEAD@{32}: commit: Dropped commit message
becc4d1 HEAD@{33}: pull: Fast-forward
7cd7169 HEAD@{34}: rebase (finish): returning to 
refs/heads/main
7cd7169 HEAD@{35}: rebase (start): checkout HEAD~
3
856b990 HEAD@{36}: reset: moving to HEAD
856b990 HEAD@{37}: rebase (abort): returning to r
efs/heads/main
856b990 HEAD@{38}: rebase (abort): returning to r
efs/heads/main
becc4d1 HEAD@{39}: reset: moving to HEAD
becc4d1 HEAD@{40}: commit: complete challnege 5 a
dvanced squashing
e9e6d3f HEAD@{41}: commit: Remove old conflicting
 README files
9d5cceb HEAD@{42}: commit (amend): Merge commit '
ced368e'
73d64e7 HEAD@{43}: commit (amend): Merge commit '
ced368e'
92a34cb HEAD@{44}: merge ced368e: Merge made by t
he 'ort' strategy.
856b990 HEAD@{45}: checkout: moving from ced368e2
39855af0c00063a7360a2ba016dc7c27 to main
ced368e HEAD@{46}: commit: completed challenge 5 
advanceed sqaushing
128ee9b HEAD@{47}: commit (amend): Create third a
nd fourth files
5258535 HEAD@{48}: rebase: fast-forward
a80e7ca HEAD@{49}: rebase (start): checkout HEAD~
3
856b990 HEAD@{50}: rebase (finish): returning to 
refs/heads/main
856b990 HEAD@{51}: rebase (pick): challenge 5
7cd7169 HEAD@{52}: rebase (pick): challenge 4 spl
iting a commit into 2 separate commits
5258535 HEAD@{53}: rebase (squash): Create Third 
File
7d4f47d HEAD@{54}: rebase: fast-forward
a80e7ca HEAD@{55}: rebase: fast-forward
82623de HEAD@{56}: rebase (start): checkout 82623
deb6f8691edc4cbad964942d9250f5bb7b4
3f94a5e HEAD@{57}: commit: challenge 5
be5a61d HEAD@{58}: commit: challenge 4 spliting a
 commit into 2 separate commits
388391b HEAD@{59}: commit: Create Fourth File
7d4f47d HEAD@{60}: commit: Create Third File
a80e7ca HEAD@{61}: reset: moving to HEAD
a80e7ca HEAD@{62}: reset: moving to 07a06aa^
865f855 HEAD@{63}: commit: squash intial and seco
nd commits
a56d534 HEAD@{64}: reset: moving to HEAD
a56d534 HEAD@{65}: reset: moving to HEAD~1
160a933 HEAD@{66}: rebase (finish): returning to 
refs/heads/main
160a933 HEAD@{67}: rebase (squash): change before
 rebase
0fd5652 HEAD@{68}: rebase (pick): change before r
ebase
a56d534 HEAD@{69}: rebase (pick): stages and adde
d the test4.md
07a06aa HEAD@{70}: rebase (pick): chore: Create t
hird and fourth files
a80e7ca HEAD@{71}: rebase (squash): chore: Squash
 intial and second commits
750d9d6 HEAD@{72}: rebase: fast-forward
98553cc HEAD@{73}: rebase (start): checkout 98553
ccf7db25909d2a994217c697ef3c1a9edf6
b115be0 HEAD@{74}: rebase (finish): returning to 
refs/heads/main
b115be0 HEAD@{75}: rebase (start): checkout HEAD~
5
b115be0 HEAD@{76}: rebase (finish): returning to 
refs/heads/main
b115be0 HEAD@{77}: rebase (start): checkout HEAD~
5
b115be0 HEAD@{78}: commit: before squashing
30ae2c3 HEAD@{79}: rebase (finish): returning to 
refs/heads/main
30ae2c3 HEAD@{80}: rebase (pick): change before r
ebase
ea91149 HEAD@{81}: rebase (pick): stages and adde
d the test4.md
86df9dc HEAD@{82}: rebase (pick): chore: Create t
hird and fourth files
9d57a6c HEAD@{83}: commit (amend): Create second 
file
28d7bd4 HEAD@{84}: rebase: fast-forward
750d9d6 HEAD@{85}: rebase (start): checkout HEAD~
4
9499f6f HEAD@{86}: rebase (finish): returning to 
refs/heads/main
9499f6f HEAD@{87}: rebase (start): checkout HEAD~
4
9499f6f HEAD@{88}: rebase (finish): returning to 
refs/heads/main
9499f6f HEAD@{89}: rebase (start): checkout HEAD~
3
9499f6f HEAD@{90}: rebase (finish): returning to 
refs/heads/main
9499f6f HEAD@{91}: rebase (start): checkout HEAD~
3
9499f6f HEAD@{92}: commit: change before rebase
b3c743c HEAD@{93}: commit (amend): stages and add
ed the test4.md
e338a47 HEAD@{94}: commit: created repo and intia
lized the environment
287d0bc HEAD@{95}: commit: chore: Create third an
d fourth files
28d7bd4 HEAD@{96}: commit: chore: Create another 
file
750d9d6 HEAD@{97}: commit (initial): chore: Creat
e initial file
(END)
```

# Part 2: Branching Basics (10 Challenges)
### 1.Feature Branch Creation:
```bash
    DENGKUAT@MacBookPro GitAdvanced % git checkout -b ft/new-feature
    Switched to a new branch 'ft/new-feature'
    DENGKUAT@MacBookPro GitAdvanced % 
    DENGKUAT@MacBookPro GitAdvanced % git branch
* ft/new-feature
  main
DENGKUAT@MacBookPro GitAdvanced % 
```

### 2. Working on the Feature Branch:
```bash
DENGKUAT@MacBookPro GitAdvanced % echo "content added to new branch as it is created" > feature.txt 
DENGKUAT@MacBookPro GitAdvanced % 
DENGKUAT@MacBookPro GitAdvanced % git add feature.txt
DENGKUAT@MacBookPro GitAdvanced % git commit -m "Implemented core functionality for new feature"
[ft/new-feature ab1aba8] Implemented core functionality for new feature
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
DENGKUAT@MacBookPro GitAdvanced % 
```

### 3. Switching Back and Making More Changes:
```bash
DENGKUAT@MacBookPro GitAdvanced % git checkout ma
in
M       readme.md
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
DENGKUAT@MacBookPro GitAdvanced % 
DENGKUAT@MacBookPro GitAdvanced % echo "Wagwan to readme.txt" > readme.txt
DENGKUAT@MacBookPro GitAdvanced % git add readme.txt
DENGKUAT@MacBookPro GitAdvanced % git commit -m "Updated project readme"
[main 4433680] Updated project readme
 1 file changed, 1 insertion(+)
 create mode 100644 readme.txt
DENGKUAT@MacBookPro GitAdvanced % git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 296 bytes | 296.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/Dengkuat/GitAdvanced.git
   fb05364..4433680  main -> main
DENGKUAT@MacBookPro GitAdvanced % 
```

### 4. Local vs. Remote Branches:
```bash
Done
```

### 5. Branch Deletion:
```bash
    DENGKUAT@MacBookPro GitAdvanced % git checkout ma
in
M       readme.md
Already on 'main'
Your branch is up to date with 'origin/main'.
DENGKUAT@MacBookPro GitAdvanced % git merge ft/new-feature
hint: Waiting for your editor to close the file..
Merge made by the 'ort' strategy.
 feature.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 feature.txt
 DENGKUAT@MacBookPro GitAdvanced % git branch -d ft/new-feature
Deleted branch ft/new-feature (was ab1aba8).
DENGKUAT@MacBookPro GitAdvanced % 
```

### 6. Creating a Branch from a Commit:
```bash
DENGKUAT@192 GitAdvanced % git checkout -b ft/new-branch-from-commit 339b6a0
Switched to a new branch 'ft/new-branch-from-commit'
``` 

### 7. Branch Merging:
``` bash
    DENGKUAT@192 GitAdvanced % git checkout main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

DENGKUAT@192 GitAdvanced % git merge ft/new-branch-from-commit
Auto-merging readme.md
CONFLICT (content): Merge conflict in readme.md
Automatic merge failed; fix conflicts and then commit the result.
DENGKUAT@192 GitAdvanced % git add readme.md
DENGKUAT@192 GitAdvanced % git commit -m "merged the branch created from the commit to the main"
[main b901f93] merged the branch created from the commit to the main
``` 

### 8. Branch Rebasing:
``` bash
DENGKUAT@192 GitAdvanced % git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'
DENGKUAT@192 GitAdvanced % git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
DENGKUAT@192 GitAdvanced % git add readme.md
DENGKUAT@192 GitAdvanced % git rebase --continue
fatal: No rebase in progress?
DENGKUAT@192 GitAdvanced % git log --oneline --graph --decorate 
* 7abbe87 (HEAD -> ft/new-branch-from-commit, main) merged the branch created from the commit to the main
*   b901f93 merged the branch created from the commit to the main
|\  
| * 390220f final updates before merging
| * 21caf3b added changes
* | bd5820d creating a branch form a commit
* | e043d47 (origin/main) deleting future branch after merging it to the main
* | b9e3d1b deleting future branch after merging it to the main
|/  
*   339b6a0 Merge branch 'ft/new-feature'
|\  
| * ab1aba8 Implemented core functionality for new feature
* | 05d232e part 2 challenege 3
* | 4433680 Updated project readme
|/  
* fb05364 complicated git challenges part 1
* 6d4d75c  Cherry-Picking Commits:
* 1ab013e  Cherry-Picking Commits:
*   8b9c0f1 Merge branch 'ft/branch'
|\  
| * 790bf8f Implemented test 5
* | 4faafe4 Implemented test 5
|/  
* e3ee35b challenege 7
* 43416d2 Dropped commit message
* becc4d1 complete challnege 5 advanced squashing
* e9e6d3f Remove old conflicting README files
*   9d5cceb Merge commit 'ced368e'
|\  
| * ced368e completed challenge 5 advanceed sqaushing
| * 128ee9b Create third and fourth files
* | 856b990 challenge 5
* | 7cd7169 challenge 4 spliting a commit into 2 separate commi
ts
* | 5258535 Create Third File
|/  
* a80e7ca chore: Squash intial and second commits
(END)
``` 

### 9. Renaming Branches
```bash
 DENGKUAT@192 GitAdvanced % git checkout ft/new-branch-from-commit
M       readme.md
Already on 'ft/new-branch-from-commit'
DENGKUAT@192 GitAdvanced % git branch -m ft/new-branch-from-commit ft/improved-branch-name
DENGKUAT@192 GitAdvanced % git branch
* ft/improved-branch-name
  main
DENGKUAT@192 GitAdvanced % 
``` 

### 10. Checking Out Detached HEAD:
```bash
    DENGKUAT@192 GitAdvanced % git checkout bd5820d
    HEAD is now at bd5820d creating a branch form a commit
``` 

# Part 3: Advanced Workflows (10+ Challenges)
### 1. Stashing Changes:
``` bash
DENGKUAT@MacBookPro GitAdvanced % git checkout mai
n
M       readme.md
Already on 'main'
Your branch is up to date with 'origin/main'.
DENGKUAT@MacBookPro GitAdvanced % git stash
Saved working directory and index state WIP on main: b76fd34 Part 2: Branching Basics all challenges completed
DENGKUAT@MacBookPro GitAdvanced % git stash stash
``` 

### 2. Retrieving Stashed Changes
``` bash
DENGKUAT@MacBookPro GitAdvanced % git stash list 
stash@{0}: WIP on main: b76fd34 Part 2: Branching Basics all challenges completed
stash@{1}: WIP on (no branch): 657793d complete challnege 5 advanced squashing
stash@{2}: WIP on (no branch): 657793d complete challnege 5 advanced squashing
DENGKUAT@MacBookPro GitAdvanced % git stash pop
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.md

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (c834e5ec47953b6b99ecfbf5bfec4e792da9e0ef)
DENGKUAT@MacBookPro GitAdvanced % 
``` 

### 3. Branch Merging Conflicts (Continued)
``` bash

``` 

this line is intially made in the main branch