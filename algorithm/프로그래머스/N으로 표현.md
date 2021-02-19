# N으로 표현

### 1. 요약

숫자 `N`이 주어졌을 때, 피연산자로 `N`, `NN`, `NNN`, `NNNN`, ...을 활용 할 수 있다. 원하는 피연산자들을 선택하고, 사칙연산(`+`, `-`, `*`, `/`)을 하여 `number`을 구할 때, `N`사용 횟수를 최소로 해야한다.(i.e. 피연산자들을 하나로 이어 붙였을 때, 길이가 가장 짧은 것)

<br/>

### 2. 아이디어

> N의 사용횟수를 리스트의 인덱스로 사용하고, 사칙연산 결과들을 저장한다.
>
> `pos = []`
> 1개의 `N`으로 표현 할 수 있는 숫자 -> `pos[0] = [N]`
> 2개의 `N`으로 사칙연산하여 나온 숫자들 -> `pos[1] = [N+N, N/N, N-N, N*N]`
> 3개의 `N`으로 사칙연산하여 나온 숫자들 -> `pos[2] = [N+N+N, N*N/N, ...]`
> 4개의 `N`으로 사칙연산하여 나온 숫자들 -> `pos[3] = [N+N+N+N, N-N+N*N, ...]`
> ...
> 8개의 `N`으로 사칙연산하여 표현 할 수 있는 숫자들 -> `pos[7] = [...]`
>
>
> 반복문을 돌면서, `number`을 찾으면 인덱스+1를 반환한다.
>
> 4개의 `N`으로 사칙연산하여 표현할 수 있는 숫자들을 살펴보자.
> 이 때, 사칙연산에 나올 수 있는 피연산자들을 `[]`을 이용하여 표현하면, `[N, NNN]`, `[NN,NN]`, `[NNN, N]`, `[NNNN]`이 나온다. 구체적으로 설명하면, 아래와 같다.
>
> `NN`: 2개의 `N`으로 사칙연산하여 나온 숫자들
> `NNN`: 3개의 `N`으로 사칙연산하여 나온 숫자들
> `NNNN`: 4개의 `N`으로 사칙연산하여 나온 숫자들
> 여기서, `NNNN`을 제외하고, 이전의 사칙연산에서 나온 결과들을 재활용하는 것을 확인 할 수 있다. 이를 토대로 구현하면 된다.

<br>

### 3. 코드

```python
def solution(N, number):
    if number == N: return 1

    answer = -1

    # pos = [{N}, {NN}, {NNN}, ..., {NNNNNNNN}]
    pos = [set([int(str(N) * i)]) for i in range(1, 9)]
    pos_len = len(pos)

    for i in range(1, pos_len):
        for j in range(i):
            for op1 in pos[j]:
                for op2 in pos[i-j-1]:
                    pos[i].add(op1+op2)
                    pos[i].add(op1-op2)
                    pos[i].add(op2-op1)
                    pos[i].add(op1*op2)

                    if op2 != 0: pos[i].add(op1//op2)
                
        if number in pos[i]:
            answer = i + 1
            break

    return answer
```

