# 변수 할당과 리스트 복사

`Python`에서는 변수에 값을 할당할 때, 해당 값이 있는 메모리 위치를 참조하게 됩니다. 이는 변수가 단순히 해당 값의 `'레퍼런스'`를 가리키게 됨을 의미합니다.

&nbsp;

```py
a = [[10, 20], [30, 40]]
b = a
```

- 여기서 `a`와 `b`는 동일한 리스트 객체를 가리키게 됩니다.
- 즉, `a`와 `b`는 모두 `[[10, 20], [30, 40]]`이라는 리스트를 가리키는 것입니다.

`b`를 통해 리스트의 값을 변경하면 `a`에도 영향을 미칩니다.

```py
b[0][0] = 500
```

&nbsp;

리스트의 원본을 변경하지 않고 복사본을 만들어야 할 때는 다음과 같은 방법을 사용할 수 있습니다.

```py
# 슬라이싱을 이용한 복사본 생성
b = [row[:] for row in a]
```

또는 `copy` 모듈을 사용하여 깊은 복사를 수행할 수도 있습니다.

```py
import copy
b = copy.deepcopy(a)  # 깊은 복사를 이용한 복사본 생성
```

- b를 변경하더라도 a는 영향을 받지 않습니다.

> 리스트의 복사본을 만들면, 원본 리스트와 별개의 메모리 위치를 가지므로 한 쪽에서의 변경이 다른 쪽에 영향을 미치지 않습니다.