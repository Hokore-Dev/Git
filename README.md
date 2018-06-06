# Git
Git 다운로드 : https://git-scm.com/

## 사용자 설정
<pre><code>➜ git config --global user.name "사용자명"
➜  git config --global user.email "메일 주소"
</code></pre>

## 프로젝트 생성
<pre><code>➜ $git init 
Initialized empty Git repository in /Volumes/PartitionDrive/test1/.git/
➜  git:(master)
</code></pre>

## Clone
<pre><code>➜ git clone https://github.com/haminjun/test1.git
Cloning into 'test1'...
remote: Counting objects: 83, done.
remote: Total 83 (delta 0), reused 0 (delta 0), pack-reused 83
Unpacking objects: 100% (83/83), done.
</code></pre>

## Commit
<pre><code>➜ git:(master) git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	test.rtf

nothing added to commit but untracked files present (use "git add" to track)
</code></pre>
Untacked, Stage 영역 확인
<pre><code>➜  test1 git:(master) ✗ git add test.rtf
</code></pre>
커밋할 파일을 stage 영역에 추가
<pre><code>➜  test1 git:(master) ✗ git commit -m "테스트 파일 추가"
[master (root-commit) eb95301] 테스트 파일 추가
 1 file changed, 8 insertions(+)
 create mode 100644 test.rtf
</code></pre>

## Push
<pre><code>➜ git:(master) git push
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 469 bytes | 469.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/haminjun/test1.git
 * [new branch]      master -> master
</code></pre>

## Pull
<pre><code>➜ git:(master) git pull
remote: Counting objects: 3, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/haminjun/test1
   eb95301..3878343  master     -> origin/master
Updating eb95301..3878343
Fast-forward
 test.rtf | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
</code></pre>

## Stash
<pre><code>➜ git:(master) ✗ git stash
Saved working directory and index state WIP on master: 3878343 Update test.rtf
</code></pre>
Untacked -> Stash
<pre><code>➜ git:(master) git stash apply
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   test.rtf

no changes added to commit (use "git add" and/or "git commit -a")
</code></pre>
Stash -> Untracked

## Branch
<pre><code>➜ git:(master) ✗ git branch dev_test
➜  test1 git:(master) ✗ git checkout dev_test
M	test.rtf
Switched to branch 'dev_test'
</code></pre>

## Merge
<pre><code>➜ git:(master) git merge dev_test
Updating 3878343..e23abdc
Fast-forward
 test.rtf  | 2 +-
 test1.rtf | 8 ++++++++
 2 files changed, 9 insertions(+), 1 deletion(-)
 create mode 100644 test1.rtf
</code></pre>

## Cherry-pick
<pre><code>➜ git:(dev_test) git log
commit c576f03bbacaeba99cb3a4ed2c66db5dd82059aa (HEAD -> dev_test)
Author: minjun.ha <haminjun0@gmail.com>
Date:   Wed Jun 6 16:24:07 2018 +0900

    commit 2
    
➜ git:(master) git cherry-pick c576f03bbacaeba99cb3a4ed2c66db5dd82059aa
[master 1a7ca32] commit 2
 Date: Wed Jun 6 16:24:07 2018 +0900
 1 file changed, 8 insertions(+)
 create mode 100644 test2.rtf
</code></pre>
커밋 고유 아이디를 입력해서 사용 가능

## Revert
<pre><code>➜ git:(master) git log
commit 1a7ca325a9fd97c3901ae68d46a620466f01c6ad (HEAD -> master)
Author: minjun.ha <haminjun0@gmail.com>
Date:   Wed Jun 6 16:24:07 2018 +0900

    commit 2

Revert "commit 2"

➜  git:(master) git revert 1a7ca325a9fd97c3901ae68d46a620466f01c6ad

This reverts commit 1a7ca325a9fd97c3901ae68d46a620466f01c6ad.

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
# Your branch is ahead of 'origin/master' by 2 commits.
#   (use "git push" to publish your local commits)
#
# Changes to be committed:
#       deleted:    test2.rtf
#
:wq
</code></pre>

## Reset 
<pre><code>➜  git:(master) git reset --mixed e23abdc1bfba7716954a284eabdbd004a4f7305d
</code></pre>

## Tag
<pre><code>➜ git:(master) git tag v1.0.1
➜  test1 git:(master) git tag
v1.0.1
(END)
</code></pre>

## Rebase
<pre><code>➜ git:(dev_test) git rebase master dev_test
First, rewinding head to replay your work on top of it...
➜  test1 git:(dev_test) git log
commit b7c7545fd77d26224fc968b056db65b90420becf (HEAD -> dev_test, origin/master, master)
Author: minjun.ha <haminjun0@gmail.com>
Date:   Wed Jun 6 16:31:13 2018 +0900

    commit 3
</code></pre>

## Fetch
<pre><code>➜ git:(dev_non_server) ✗ git fetch --all
Fetching origin
</code></pre>
