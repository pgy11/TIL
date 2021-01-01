# 00. Basic CLI

1. `ls` : 목록 조회 (list)

   ```bash
   $ ls
   00_basic_cli.md  a.txt  b/  c.txt  d.txt  e.txt  images/  markdown.md
   ```

   `ls -al` : 상세 목록 조회

   ```bash
   $ ls -al
   total 25
   drwxr-xr-x 1 Admin 197121   0 Dec 29 15:05 ./
   drwxr-xr-x 1 Admin 197121   0 Dec 29 13:30 ../
   drwxr-xr-x 1 Admin 197121   0 Dec 29 14:03 .git/
   -rw-r--r-- 1 Admin 197121   2 Dec 29 15:05 00_basic_cli.md
   -rw-r--r-- 1 Admin 197121   0 Dec 29 11:44 a.txt
   drwxr-xr-x 1 Admin 197121   0 Dec 29 11:46 b/
   -rw-r--r-- 1 Admin 197121   0 Dec 29 11:44 c.txt
   -rw-r--r-- 1 Admin 197121   0 Dec 29 13:40 d.txt
   -rw-r--r-- 1 Admin 197121   0 Dec 29 13:40 e.txt
   drwxr-xr-x 1 Admin 197121   0 Dec 29 14:34 images/
   -rw-r--r-- 1 Admin 197121 969 Dec 29 15:04 markdown.md
   ```

   

2. `cd` : 폴더 변경(chage directory)

   1. `cd` : ~ 폴더(home 폴더)로 이동
   2. `cd 폴더명` : `폴더명`으로 이동
      - `cd 폴더명/폴더명/폴더명` : 여러개의 폴더를 한번에 이동

      - `cd ..` : 상위 폴더로 이동

      

3. `mkdir` : 폴더 생성(make directory)

   - `mkdir A` : `A`이라는 폴더를 생성

   

4. `touch` : 파일 생성

   - `touch A.txt` : `A.txt` 파일을 생성 (빈 파일)
   - `mv A.txt C.txt` : `A.txt`파일의 이름을 `C.txt`로 변경

   

5. `Tab` : 자동 완성

6. 방향키 위, 아래 : 명령어 기록 (History)



