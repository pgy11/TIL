# 04. Push Error

- Push error에는 다양한 원인 있지만, 여기서는 remote repository로 부터 pull을 하지 않았을 때 발생 할 수 있는 에러를 살펴본다.

  - Remote repository에서 다른 사용자에 의해 새로운 commit이 추가
  - Push를 하려는 사람은 이 commit에 관련된 파일을 갖고 있지 않을 때 다음의 에러가 발생한다.

  ```bash
  # Remote repository에서 새로운 파일이 있다. push하는 사람은 이 파일을 갖고 있지 않다.
  # 따라서 push 할 때, 에러가 발생한다.
  # 이를 해결하기 위해, push하기 전에 pull을 해야한다.
  $ git push origin main
  To https://github.com/pgy11/TIL-test.git
   ! [rejected]        main -> main (fetch first)
  error: failed to push some refs to 'https://github.com/pgy11/TIL-test.git'
  hint: Updates were rejected because the remote contains work that you do
  hint: not have locally. This is usually caused by another repository pushing
  hint: to the same ref. You may want to first integrate the remote changes
  hint: (e.g., 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.
  ```

<br>

- 위의 문제를 해결하기 위해, pull을 먼저 해야하는데, remote repository의 HEAD와 사용자의 HEAD가 다르기 때문에 병합을 해야한다.

```bash
Merge branch 'main' of https://github.com/pgy11/TIL-test # message has already been written.
# Please enter a commit message to explain why this merge is necessary,
# especially if it merges an updated upstream into a topic branch.
#
# Lines starting with '#' will be ignored, and an empty message aborts
# the commit.
```

```bash
$ git pull origin main
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 2 (delta 1), reused 2 (delta 1), pack-reused 0
Unpacking objects: 100% (2/2), 241 bytes | 21.00 KiB/s, done.
From https://github.com/pgy11/TIL-test
 * branch            main       -> FETCH_HEAD
   548cbee..0cfe22a  main       -> origin/main
Merge made by the 'recursive' strategy. # 병합이 되었음
 d.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 d.txt
```



