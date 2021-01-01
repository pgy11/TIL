# 03. Git Remote

+ `git remote` : `Remote repository` 주소 등록(여기서는 `GitHub Repo`)

  + `git remote add origin 주소` :  Remote repo의 주소를 `origin`이라는 별칭으로 등록

  + `git remote -v` : 등록된 Remote 주소 확인

    ```bash
    $ git remote -v
    origin  https://github.com/pgy11/TIL.git (fetch)
    origin  https://github.com/pgy11/TIL.git (push)
    ```



+ `git push [별칭] [브랜치이름]` : `별칭`으로 `브랜치`를 전송한다.
+ `git push origin main` `origin`으로 `main` 브랜치를 전송

+ `git clone 주소` :  주소로부터 Repo 가져오기

+ `git pull [별칭] [브랜치 이름]` : `별칭`으로부터 `브랜치`를 가져온다.

