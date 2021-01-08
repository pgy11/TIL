# 08. Merge Branch

- 병합
  
  - 각 브랜치 상에서 작업이 모두 완료되면, 이들을 병합을 해야한다.
  - 충돌이 발생하면, 팀원들끼리 합의해야한다.
  - `git merge {브랜치 이름}`
  
  

1. Fast-Forward

   - 브랜치가  나누어져있지만, 오직 하나의 브랜치에서 작업이 이루어지다가 병합 된 경우
   - Fast-Forward 예제

   ```bash
   (main) $ git swtich -c login
   (login) $ touch login.txt
   (login) $ git add 
   (login) $ git commit
   (login) $ git switch main
   (main) $ git merge login
   ```

   <br>

   ```bash
   $ git log --oneline --graph --all
   * e5f7dd5 (HEAD -> login) login.txt added
   * 0fc8535 (main) b.txt added
   * fc005c9 a.txt added
   ```

   <br>

2. 3-Way Merge

   - 각작의 브랜치에서 작업하고 나서, 문제 없이 병합 된 경우

   <br>

3. Merge Conflict

   - 충돌은 각 브랜치에서 같은 파일 작업을 했을 때 발생하며, 합의가 필요하다.
   - 브랜치들을 병합하려고 했지만 충동 결과 발생

   ```bash
   $ git merge signup
   CONFLICT (add/add): Merge conflict in READ.md
   Auto-merging READ.md
   Automatic merge failed; fix conflicts and then commit the result.
   
   ```

   <br>

   - READ.md 파일 내용
   - 어디서 충돌이 발생했는 지 알려줌 -> 이를 토대로, 팀원들 간의 합의가 필요하다.

   ```
   <<<<<<< HEAD
   - A code from main
   =======
   A code from signup
   >>>>>>> signup
   ```

   <br>

   - 충돌 결과를 git status 명령어를 이용하여 출력

   ```bash
   $ git status
   On branch main
   You have unmerged paths.
     (fix conflicts and run "git commit")
     (use "git merge --abort" to abort the merge)
   
   Unmerged paths:
     (use "git add <file>..." to mark resolution)
           both added:      READ.md
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

   



