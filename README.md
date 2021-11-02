patrik@DESKTOP-8NVOMRK:~/branching$ git remote add origin https://github.com/AlexeyGrv/branching.git
patrik@DESKTOP-8NVOMRK:~/branching$ touch merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ touch rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ nano merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git add *
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'prepare for merge and rebase'
[master (root-commit) 7eb7acd] prepare for merge and rebase
 2 files changed, 16 insertions(+)
 create mode 100644 merge.sh
 create mode 100644 rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git branch -M main
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin main
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 354 bytes | 177.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/AlexeyGrv/branching.git
 * [new branch]      main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ git switch -c git-merge
Switched to a new branch 'git-merge'
patrik@DESKTOP-8NVOMRK:~/branching$ nano merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ cat merge.sh
#!/bin/bash
# display command line options

count=1
for param in "$@"; do
    echo "\$@ Parameter #$count = $param"
    count=$(( $count + 1 ))
done
patrik@DESKTOP-8NVOMRK:~/branching$ git st
On branch git-merge
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   merge.sh

no changes added to commit (use "git add" and/or "git commit -a")
patrik@DESKTOP-8NVOMRK:~/branching$ git add merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'merge: @ instead *'
[git-merge 7b52454] merge: @ instead *
 1 file changed, 2 insertions(+), 2 deletions(-)
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-merge
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 333 bytes | 166.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'git-merge' on GitHub by visiting:
remote:      https://github.com/AlexeyGrv/branching/pull/new/git-merge
remote:
To https://github.com/AlexeyGrv/branching.git
 * [new branch]      git-merge -> git-merge
Branch 'git-merge' set up to track remote branch 'git-merge' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ nano merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git add merge.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'merge: use shift'
[git-merge d13541d] merge: use shift
 1 file changed, 3 insertions(+), 2 deletions(-)
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-merge
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 403 bytes | 403.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/AlexeyGrv/branching.git
   7b52454..d13541d  git-merge -> git-merge
Branch 'git-merge' set up to track remote branch 'git-merge' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git add rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'git-rebase'
[main 21240de] git-rebase
 1 file changed, 4 insertions(+), 2 deletions(-)
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin main
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 333 bytes | 111.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/AlexeyGrv/branching.git
   7eb7acd..21240de  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --all
21240de (HEAD -> main, origin/main) git-rebase
d13541d (origin/git-merge, git-merge) merge: use shift
7b52454 merge: @ instead *
7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git checkout 7eb7acd
Note: switching to '7eb7acd'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --all
21240de (origin/main, main) git-rebase
d13541d (origin/git-merge, git-merge) merge: use shift
7b52454 merge: @ instead *
7eb7acd (HEAD) prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git switch -c git-rebase
Switched to a new branch 'git-rebase'
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git st
On branch git-rebase
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   rebase.sh

no changes added to commit (use "git add" and/or "git commit -a")
patrik@DESKTOP-8NVOMRK:~/branching$ git add rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'git-rebase 1'
[git-rebase 74b5149] git-rebase 1
 1 file changed, 4 insertions(+), 2 deletions(-)
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-rebase
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 343 bytes | 171.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote:
remote: Create a pull request for 'git-rebase' on GitHub by visiting:
remote:      https://github.com/AlexeyGrv/branching/pull/new/git-rebase
remote:
To https://github.com/AlexeyGrv/branching.git
 * [new branch]      git-rebase -> git-rebase
Branch 'git-rebase' set up to track remote branch 'git-rebase' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git add rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'git-rebase 2'
[git-rebase 1788632] git-rebase 2
 1 file changed, 1 insertion(+), 1 deletion(-)
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-rebase
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 316 bytes | 158.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/AlexeyGrv/branching.git
   74b5149..1788632  git-rebase -> git-rebase
Branch 'git-rebase' set up to track remote branch 'git-rebase' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --all
1788632 (HEAD -> git-rebase, origin/git-rebase) git-rebase 2
74b5149 git-rebase 1
21240de (origin/main, main) git-rebase
d13541d (origin/git-merge, git-merge) merge: use shift
7b52454 merge: @ instead *
7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --decorate --graph --all
* 1788632 (HEAD -> git-rebase, origin/git-rebase) git-rebase 2
* 74b5149 git-rebase 1
| * 21240de (origin/main, main) git-rebase
|/
| * d13541d (origin/git-merge, git-merge) merge: use shift
| * 7b52454 merge: @ instead *
|/
* 7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
patrik@DESKTOP-8NVOMRK:~/branching$ git merge git-merge
hint: Waiting for your editor to close the file...

Use "fg" to return to nano.

[2]+  Stopped                 git merge git-merge
patrik@DESKTOP-8NVOMRK:~/branching$ git merge git-merge
fatal: You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you merge.
patrik@DESKTOP-8NVOMRK:~/branching$ git st
On branch main
Your branch is up to date with 'origin/main'.

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
        modified:   merge.sh

patrik@DESKTOP-8NVOMRK:~/branching$ git commit -m 'merg fix'
[main a617521] merg fix
patrik@DESKTOP-8NVOMRK:~/branching$ git merge git-merge
Already up to date.
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --decorate --graph --all
*   a617521 (HEAD -> main) merg fix
|\
| * d13541d (origin/git-merge, git-merge) merge: use shift
| * 7b52454 merge: @ instead *
* | 21240de (origin/main) git-rebase
|/
| * 1788632 (origin/git-rebase, git-rebase) git-rebase 2
| * 74b5149 git-rebase 1
|/
* 7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin main
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 295 bytes | 98.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0)
To https://github.com/AlexeyGrv/branching.git
   21240de..a617521  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ cat merge.sh
#!/bin/bash
# display command line options

count=1
while [[ -n "$1" ]]; do
    echo "Parameter #$count = $1"
    count=$(( $count + 1 ))
    shift
done
patrik@DESKTOP-8NVOMRK:~/branching$ git checkout git-rebase
Switched to branch 'git-rebase'
Your branch is up to date with 'origin/git-rebase'.
patrik@DESKTOP-8NVOMRK:~/branching$ git rebase -i main
Auto-merging rebase.sh
CONFLICT (content): Merge conflict in rebase.sh
error: could not apply 74b5149... git-rebase 1
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 74b5149... git-rebase 1
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git add rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git rebase --continue
Auto-merging rebase.sh
CONFLICT (content): Merge conflict in rebase.sh
error: could not apply 1788632... git-rebase 2
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 1788632... git-rebase 2
patrik@DESKTOP-8NVOMRK:~/branching$ nano rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ cat rebase.sh
#!/bin/bash
# display command line options

count=1
for param in "$@"; do
    echo "\$@ Parameter #$count = $param"
    count=$(( $count + 1 ))
done

echo "====="
patrik@DESKTOP-8NVOMRK:~/branching$ git add rebase.sh
patrik@DESKTOP-8NVOMRK:~/branching$ git rebase --continue
Successfully rebased and updated refs/heads/git-rebase.
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-rebase
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
To https://github.com/AlexeyGrv/branching.git
 ! [rejected]        git-rebase -> git-rebase (non-fast-forward)
error: failed to push some refs to 'https://github.com/AlexeyGrv/branching.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
patrik@DESKTOP-8NVOMRK:~/branching$ git push -u origin git-rebase -f
Username for 'https://github.com': AlexeyGrv
Password for 'https://AlexeyGrv@github.com':
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/AlexeyGrv/branching.git
 + 1788632...a617521 git-rebase -> git-rebase (forced update)
Branch 'git-rebase' set up to track remote branch 'git-rebase' from 'origin'.
patrik@DESKTOP-8NVOMRK:~/branching$ git log --oneline --decorate --graph --all
*   a617521 (HEAD -> git-rebase, origin/main, origin/git-rebase, main) merg fix
|\
| * d13541d (origin/git-merge, git-merge) merge: use shift
| * 7b52454 merge: @ instead *
* | 21240de git-rebase
|/
* 7eb7acd prepare for merge and rebase
patrik@DESKTOP-8NVOMRK:~/branching$ git checkout main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
patrik@DESKTOP-8NVOMRK:~/branching$ git merge git-rebase
