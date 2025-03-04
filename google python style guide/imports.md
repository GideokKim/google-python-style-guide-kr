## 2.2 Imports

패키지와 모듈에 대해서만 import 문을 사용하고, 개별 타입, 클래스 또는 함수에 대해서는 사용하지 않습니다.

### 2.2.1 정의

한 모듈에서 다른 모듈로 코드를 공유하기 위한 재사용성(Reusable) 메커니즘입니다.

### 2.2.2 장점

네임스페이스 관리 규칙이 단순합니다. 각 식별자의 출처는 일관된 방식으로 표시됩니다. 예를 들어 x.Obj는 객체 Obj가 모듈 x에 정의되어 있음을 나타냅니다.

### 2.2.3 단점

모듈 이름이 서로 충돌할 수 있습니다. 일부 모듈 이름은 사용하기에 불편할 정도로 길 수 있습니다.

### 2.2.4 권장 사항

- 패키지와 모듈을 가져올 때는 `import x` 를 사용합니다.
- 패키지 접두사가 `x` 이고, 접두사가 없는 모듈 이름 `y` 를 가져올 때는 `from x import y` 를 사용합니다.
- 다음과 같은 상황에서는 `from x import y as z` 를 사용합니다:
  - (동일한 이름을 가진) 두 개의 모듈 `y` 를 가져와야 할 때.
  - `y` 가 현재 모듈에서 정의된 최상위 이름과 충돌할 때.
  - `y` 가 공개 API의 일부인 공통 매개변수 이름(예, `features` )과 충돌할 때.
  - `y` 가 사용하기에 불편할 정도로 길 때.
  - `y` 가 코드의 맥락에서 너무 일반적일 때 (예, `from storage.file_system import options as fs_options` ).
- `z` 가 표준 약어인 경우에만 `import y as z` 를 사용합니다. (예, `import numpy as np` ).

예를 들어, 모듈 `sound.effects.echo` 는 다음과 같이 가져올 수 있습니다:

```python
from sound.effects import echo
...
echo.EchoFilter(input, output, delay=0.7, atten=4)
```

import의 관계있는 이름을 사용하지 않습니다. 모듈이 같은 패키지 내에 있더라도 전체 패키지 이름을 사용합니다. 이는 패키지가 의도치 않게 중복으로 임포트(import) 하는 것을 방지하는 데 도움이 됩니다.

##### 2.2.4.1 예외

이 규칙의 면제 사항:

- 다음 모듈의 심볼들(symbols)은 정적 분석 및 타입 검사를 지원하기 위해 사용됩니다:
  - [`typing` 모듈](https://google.github.io/styleguide/pyguide.html#typing-imports)
  - [`collections.abc` 모듈](https://google.github.io/styleguide/pyguide.html#typing-imports)
  - [`typing_extensions` 모듈](https://github.com/python/typing_extensions/blob/main/README.md)
- [six.moves 모듈](https://six.readthedocs.io/#module-six.moves) 의 리디렉션(redirects).
