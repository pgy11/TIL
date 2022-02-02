# K번째 수

**Java 함수형 프로그래밍 / 스트림 연습입니다**

<br/>

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.IntStream;


class Solution {
        public int[] solution(int[] array, int[][] commands) {
            List<Integer> answer = new ArrayList<>();
            Arrays.stream(commands).forEach(x -> {
                List<Integer> list = new ArrayList<>();
                IntStream.range(x[0], x[1]+1).forEach(i -> list.add(array[i-1]));
                int k = list.stream().sorted().collect(Collectors.toList()).get(x[2]-1);
                answer.add(k);
            });

            return answer.stream().mapToInt(i -> i).toArray();
        }
    }
```