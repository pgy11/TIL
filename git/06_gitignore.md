# 06. gitignore

- 우리가 **git으로 관리하고 있지않은 파일들을 제외시키는 방법**

  - 우리가 원하지 않은 파일들을 제외한다.
  - 외부에 공개되면 안되는 것들(key, secret)

  <br>

- `.gitignore`

  - `.gitignore`에 작성된 파일들은 git으로 관리하지 않겠다.(ignore)

  <br>

- 작성방법

  ```bash
  # 제외할 파읻들을 .gitignore에서 작성한다.
  .DS_Store # Mac OS에서 사용되는 파일
  f.txt # 특정파일
  secret/ # 특정 폴더
  *.png # 특정 확장자, 모든 png는 빼고
  !profile.png # profile.png는 넣고
  ```

  <br>

- 이미 commit을 한 파일들을 제외 시키는 방법
  1. `.gitignore`에다가 파일 명시
  2. `git rm --cached [파일명]`
     - `git`에서 더 이상 관리하지 않겠다.
     - WD에서 삭제해서 더 이상 관리하지 않겠다.