```git
wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console
$ git init
Initialized empty Git repository in D:/csjjg/Snake_console/.git/

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git add Snake_console

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git commit -m "snake_console"
[master (root-commit) 7d1345f] snake_console
 6 files changed, 397 insertions(+)
 create mode 100644 Snake_console/snake.c
 create mode 100644 Snake_console/snake.h
 create mode 100644 Snake_console/snake_main.c
 create mode 100644 Snake_console/snake_main.exe
 create mode 100644 Snake_console/test.c
 create mode 100644 Snake_console/test.exe

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ ssh-keygen -t rsa -C "wangyifan52199@163.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/wkjiaju/.ssh/id_rsa):
/c/Users/wkjiaju/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/wkjiaju/.ssh/id_rsa
Your public key has been saved in /c/Users/wkjiaju/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:vdlESIxc52uZAYFGWOUChm8X/zjca+00ZomKggphKKE wangyifan52199@163.com
The key's randomart image is:
+---[RSA 3072]----+
|     .o=o**..    |
|    ....*o.=     |
|.    . ..oo +    |
|o.    o .o.. =   |
|E.   . .S..+*    |
|o.        +*o. . |
|.    .    o.oo*  |
| .  . .  . .o+.. |
|  ..   .. .. ..  |
+----[SHA256]-----+

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git remote add origin git@github.com:WangYifan321/c.git

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git push -u origin master
Warning: Permanently added the RSA host key for IP address '13.250.177.223' to the list of known hosts.
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 8 threads
Compressing objects: 100% (8/8), done.
Writing objects: 100% (9/9), 33.44 KiB | 4.18 MiB/s, done.
Total 9 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
remote:
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/WangYifan321/c/pull/new/master
remote:
To github.com:WangYifan321/c.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git push origin master
Warning: Permanently added the RSA host key for IP address '13.229.188.59' to the list of known hosts.
Everything up-to-date

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git add score

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git commit -m "score"
[master 1ceb1d8] score
 2 files changed, 10 insertions(+)
 create mode 100644 score/score.txt
 create mode 100644 "score/\346\226\260\345\273\272\346\226\207\346\234\254\346\226\207\346\241\243.txt"

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git push origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 414 bytes | 414.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:WangYifan321/c.git
   7d1345f..1ceb1d8  master -> master

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git branch
* master

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git push main master
fatal: 'main' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git push main
fatal: 'main' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git switch main
fatal: invalid reference: main

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git switch -c new
Switched to a new branch 'new'

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (new)
$ git branch
  master
* new

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (new)
$ git remote
origin

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (new)
$ git push origin new
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'new' on GitHub by visiting:
remote:      https://github.com/WangYifan321/c/pull/new/new
remote:
To github.com:WangYifan321/c.git
 * [new branch]      new -> new

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (new)
$ git branch
  master
* new

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (new)
$ git switch master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git fetch git@github.com:WangYifan321/c.git
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 596 bytes | 45.00 KiB/s, done.
From github.com:WangYifan321/c
 * branch            HEAD       -> FETCH_HEAD

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git log -p FETCH_HEAD
commit 9cb37121f51a0e80cade41180d60f3caf286a81d
Author: WangYifan321 <78241565+WangYifan321@users.noreply.github.com>
Date:   Fri May 7 21:16:16 2021 +0800

    Initial commit

diff --git a/README.md b/README.md
new file mode 100644
index 0000000..e57b53f
--- /dev/null
+++ b/README.md
@@ -0,0 +1,2 @@
+# c
+C语言

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git remote -v
origin  git@github.com:WangYifan321/c.git (fetch)
origin  git@github.com:WangYifan321/c.git (push)

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git switch main
fatal: invalid reference: main

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (master)
$ git checkout -b main
Switched to a new branch 'main'

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git branch
* main
  master
  new

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git merger master
git: 'merger' is not a git command. See 'git --help'.

The most similar command is
        merge

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git merge master
Already up to date.

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git pull origin main
remote: Enumerating objects: 6, done.
remote: Counting objects: 100% (6/6), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), 1.21 KiB | 77.00 KiB/s, done.
From github.com:WangYifan321/c
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
fatal: refusing to merge unrelated histories

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git pull origin main --allow-unrelated-histories
From github.com:WangYifan321/c
 * branch            main       -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 README.md | 2 ++
 testpull  | 1 +
 2 files changed, 3 insertions(+)
 create mode 100644 README.md
 create mode 100644 testpull

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git push origin main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 389 bytes | 389.00 KiB/s, done.
Total 2 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:WangYifan321/c.git
   4c4f5af..9be28ec  main -> main

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git branch -d new
Deleted branch new (was 1ceb1d8).

wkjiaju@LAPTOP-E3G9PRIU MINGW32 /d/csjjg/Snake_console (main)
$ git push origin --delete new
To github.com:WangYifan321/c.git
 - [deleted
```