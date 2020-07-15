# Java8 중복된 값만 골라내기

 - List의 값들을 key(element),value(갯수) 쌍인 Map으로 변환한다.
 - Map 에서 value가 1개이상인 Key값들을 Set에다가 저장.

```java
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.Set;
import java.util.function.Function;
import java.util.stream.Collectors;

/**
 * @author zzai_sang
 * @version 0.1.0
 * @since 2020/07/14
 */
public class DuplicateElement {

    public static void main(String[] args) {

        final List<String> nameList = Arrays.asList("김상재", "김상재", "김상재", "짜이상", "상짜이", "짜이상");

        final Set<String> dupRemoveSet = nameList
                .stream()
                .collect(
                        Collectors.groupingBy(Function.identity(), Collectors.counting())
                ).entrySet().stream()
                .filter(v -> v.getValue() > 1)
                .map(Map.Entry::getKey)
                .collect(Collectors.toSet());

        System.out.println(nameList);
        System.out.println(dupRemoveSet);

    }
}

```

 - 결과값
```text
[김상재, 김상재, 김상재, 짜이상, 상짜이, 짜이상]
[짜이상, 김상재]
```