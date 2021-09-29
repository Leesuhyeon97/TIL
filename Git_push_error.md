# push error

## 에러 상황

```bash
$ git push origin master
To https://github.com/edutak/0928.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/edutak/0928.git'
# Updates 거절.
# 원격저장소 작업이 로컬에 없어서 
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
# 다시 push하기 전에, 원격저장소 변경사항들을 먼저 통합하는 것을 원할 것..
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

## 해결

### 1. pull

```bash
$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 2.04 KiB | 208.00 KiB/s, done.
From https://github.com/edutak/0928
 * branch            master     -> FETCH_HEAD
   2a71213..c143740  master     -> origin/master
hint: Waiting for your editor to close the fiMerge made by the 'recursive' strategy.
 22.md | 159 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 159 insertions(+)
 create mode 100644 22.md

```

* 커밋 메시지(merge)가 발생

  ```bash
  $ git log --oneline
  9f0d621 (HEAD -> master) Merge branch 'master' of https://github.com/edutak/0928
  772310c Add d.txt
  c143740 (origin/master) Add files via upload
  2a71213 Update
  
  ```

  

* 충돌 발생시 해결이 필요

### 2. push

```bash
$ git push origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 482 bytes | 482.00 KiB/s, done.
Total 4 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/edutak/0928.git
   c143740..9f0d621  master -> master
```













