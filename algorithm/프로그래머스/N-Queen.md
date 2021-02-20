# N-Queen

### 1. 요약

`N`개의 퀸을 `NxN`의 체스판에 배치할 때, 처음부터 서로 공격하지 않게하는 경우의 수를 구하는 문제.

<br/>

### 2. 아이디어

>
>
>하나의 퀸을 `[y, x]`에 배치 할 때, 다른 퀸은 `[y, 임의의 열]`, `[임의의 행, x]`, `|y-i|==|x-i|`를 만족하는 곳에 둘 수 없다.
>
><br/>
>
>백트래킹으로 구현 시, 하나의 행에서 퀸이 둘 수 있는 위치를 찾는 함수를 만든다.
>
><br/>
>
> 그리고 위치를 찾게되면, 다음 행에서 퀸을 둘 수 있는 위치를 찾을 수 있도록 재귀적으로 구현한다. 그리고 행과 퀸의 개수는 같으므로, 퀸의 개수가 행이되면 경우의 수를 하나 증가시키고 함수를 종료한다.

<br/>

```python
answer = 0
cols = []

def backtrack(k, n):
    global answer 

    if k == n:
        answer += 1
        return

    for i in range(n):
        if i not in cols:
            ok = True
            for row, col in enumerate(cols):
                if abs(k-row) == abs(i-col):
                    ok = False
                    break
            
            if ok:
                cols.append(i)
                backtrack(k+1, n)
                cols.pop()
    
def solution(n):
    global answer
    backtrack(0, n)
    return answer
```

