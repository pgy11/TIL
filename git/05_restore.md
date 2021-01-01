# 05. 취소하기

1. Staging 영역에 등록된 파일 등록해제하기 (Git add 취소하기)

   

   ```bash
   # f.txt가 staging 영역에 등록된 상황.
   $ git status
   On branch main
   Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
           new file:   f.txt
   
   ```

   

   ```bash
   # staging 영역에 등록된 f.txt를 등록 해제하기위한 명령어 
   $ git restore --staged f.txt
   ```

   

   - 구버전

   ```bash
   # staging 영역에 등록된 f.txt를 등록 해제하기위한 명령어 (구버전)
   $ git reset HEAD f.txt
   ```

   

   - 결과

   ```bash
   # f.txt가 staging 영역에 없다는 것을 확인.
   $ git status
   On branch main
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
           f.txt
   
   nothing added to commit but untracked files present (use "git add" to track)
   ```

   

2. 이전 commit으로 되돌아가기(Git commit 취소)

   ```bash
   # 내가 돌아가고 싶은 커밋에 대한 hash를 입력(대괄호는 입력x)
   # 기본 옵션은 --mixed 이다.
   # hash는 commit에 대한 키 값이다. (git log --oneline 에서 가장 왼쪽에 있는 값)
   $ git reset (--mixed) [돌아갈 commit의 hash]
   e.g. $ git reset 0935e32
   ```

   

   - 옵션

     - **--mixed**

     ```bash
     # 취소된 commit과 관련된 파일이 staging 영역에서 제거되지만, 파일은 남아있다.
     $ git reset --mixed hash
     ```

     

     - **--soft**

     ```bash
     # 취소된 commit과 관련된 파일이 staging 영역에 남아있다.
     $ git reset --soft [hash]
     ```

     

     - **--hard**

     ```bash
     # 취소된 commit과 관련된 파일이 staging 영역에서 제거 될 뿐만아니라, 파일도 제거된다.
     $ git reset --hard [hash]
     ```

     

   - HEAD의 상대 위치를 이용한 commit 되돌리기

     - HEAD가 가리키는 시점부터 숫자만큼 뒤로 이동하여, 이전의 commit으로 이동한다.
     - HEAD~숫자 
       - HEAD~1 (`HEAD~`)
       - HEAD~2 

     ```bash
     # HEAD가 가리키는 commit의 바로 직전의 commit으로 이동한다.
     $ git reset HEAD~
     ```


   

3. WD(Working Directory) 변경 내용 취소하기, 복원

   - WD : 지금 우리가 작업 중인 공간 
   - == Git이 관리하고 있는 공간
   - == 기록이 한 번이라도 된 파일들이 있는 공간.

   ```bash
   $ git restore [파일명]
   $ git restore a.txt
   
   # old version
   $ git checkout -- [파일명]
   $ git checkout -- a.txt
   ```

   