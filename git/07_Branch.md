# 07. Branch

- Git을 이용하여 여러 사람이 협업을 하면, push, pull을 하는 과정에서 충돌 할 수 있다. 이 때 branch를 이용하여 해결하는 방법이있다. (i.e. 다른 사용자가 올린 작업의 상관없이 push, pull이 가능하다.

- 각자의 작업이 완료되면 branch를 병합해야한다.(다음 장에 배움)

- `git branch` : 브랜치 목록 확인한다.

- `git branch [브랜치 명]` : `브랜치 명`의 branch 생성한다.

  - ```bash
    # login 이름의 브랜치를 생성한다.
    $ git branch login
    ```

  <br>

-  `git switch [브랜치 명]` : `브랜치 명`을 갖는 branch로 이동한다.

  ```bash
  # login 이름의 브랜치로 이동한다.
  $ git switch login
  Switched to branch 'login'
  ```

<br>

- `git log --oneline --graph --all` 

  - 모든 브랜치들을 그래프와 함께 한 줄로 요약하여 보여준다. 

  <br>

- `git switch -c login` : 브랜치를 만들면서 바로 이동한다.

  - `git branch login` + `git switch login`

  <br>

- 구버전

  - `git checkout login` : login 브랜치로 이동한다.
  - `git checkout -b login` : loging 브랜치를 생성하면서 바로 이동한다.