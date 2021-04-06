# 01. Git

+ `git status` : `git`으로 관리 되고 있는 폴더(Repository, 저장소)의 상태를 보여준다.

+ `git config` : `git` 프로그램 설정 담당
  + `git config --global user.email '이메일'`
  + `git config --global user.name '이름'`
  + `git config --global --list` : 현재 `git` 프로그램에 설정된 값들을 확인한다.
  
  <br>
  
  
  
+ `git init` : 현재 폴더를 `git`으로 관리하겠다는 선언(초기화)

+ `git add` : `git`으로 관리할 파일들을 추가
  + `git add A.txt` : `A.txt`파일을 INDEX(Staging 영역)에 등록(폴더도 가능함)
  + `git add .` :  현재 위치한 폴더(.)를 INDEX에 등록. 폴더를 등록하면 내부 모든 파일이 등록된다.
  
  <br>
  
  
  
+ `git commit` : INDEX에 있는 파일들을 가지고 commit(History, 기록)을 남긴다.
  
  + `git commit -m '메세지'` : 기록을 남기면서, 메세지를 남긴다.(필수)
  
  <br>
  
  
  
+ `git log` : 남겨온 commit들을 확인
  
  + `git log --oneline --graph` : 그래프, 한줄 요약하여 기록을 조회

<br>

- `git rm -rf 파일명` : 파일 영구적으로 삭제한다.
  - 이후 `commit`과 `push`를 하면, `remote repository`에도 반영된다. 



