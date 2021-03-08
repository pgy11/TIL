# Puyo Puyo

### 1.요약

4가지 색의 뿌요(R, G, P, Y)가 위에서 아래로 떨어진다. 뿌요들이 바닥에 놓여진 후, 상하좌우로 인접한 같은 색의 뿌요가 4개 이상일 경우, 해당 뿌요들은 폭발한다 그리고 연쇄가 하나 증가한다. 폭발 후, 위에 남은 뿌요들이 있다면 아래로 떨어진다. 차례대로 아래로 떨어지고 만약 다시 폭발한다면, 연쇄가 또 하나 증가한다. 여기서 우리는 연쇄 횟수를 구해야한다.(단, 한 번에 여러번 폭발해도 1연쇄로 간주한다.)

<br/>

## 2. 아이디어

>
>
>문제에서 주어진 절차대로 구현하되, 한 번에 여러번 폭발해도 1연쇄로 간주한다는 사실에 주의해야한다.
>
><br/>
>
>반복문을 돌면서 폭발할 수 있는 것들은 먼저 폭발시킨다. 그 다음 공중에 떠있는 뿌요들을 아래로 내려 놓아야한다. 더 이상 폭발하지 않을 때까지 계속 반복한다.

<br/>

### 3. 코드

```python
import sys
from collections import deque

r, c = 12, 6
arr = []
answer = 0
d = [[0,1], [0,-1], [1,0], [-1,0]]

for i in range(r):
    x = list(sys.stdin.readline().rstrip())
    arr.append(x)

def isin(y,x):
    if -1<y<r:
        if -1<x<c: return True
    return False

def erase(sy, sx):
    global arr
    visited = [[False for _ in range(c)] for _ in range(r)]
    copy_arr = [[arr[i][j] for j in range(c)] for i in range(r)]
    q = deque()
    q.append([sy, sx])
    visited[sy][sx] = True
    cnt = 1

    while q:
        y, x = q.popleft()

        for i in range(4):
            ny = y + d[i][0]
            nx = x + d[i][1]

            if isin(ny, nx):
                if not visited[ny][nx]:
                    visited[ny][nx] = True

                    if arr[ny][nx] == arr[sy][sx]:
                        cnt += 1
                        q.append([ny, nx])
                        copy_arr[ny][nx] = '.'
    
    if cnt >= 4:
        copy_arr[sy][sx] = '.'
        arr = [[copy_arr[i][j] for j in range(c)] for i in range(r)]
        return True
    
    return False


def _down(y, x, ch):
    global arr
    ny = y
    
    while True:
        if ny+1 == r:
            arr[y][x] = '.'
            arr[ny][x] = ch
            break
            
        if arr[ny+1][x] != '.':
            arr[y][x] = '.'
            arr[ny][x] = ch
            break
         
        ny += 1
          
    
def down():
    global arr

    for j in range(c):
        for i in range(r-1, -1, -1):
            if arr[i][j] != '.': _down(i, j, arr[i][j])


while True:
    bombed = False
    
    for i in range(r):
        for j in range(c):
            if arr[i][j] != '.':
                if erase(i, j):
                    bombed = True
                    
    if bombed:
        answer += 1
        down()
        
    else: break

print(answer)
```

