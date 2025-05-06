## 2.4 예외

예외는 허용되지만, 신중하게 사용해야 합니다.

### 2.4.1 정의

예외는 오류나 기타 예외적인 조건을 처리하기 위해 정상적인 제어 흐름에서 벗어나는 수단입니다.

### 2.4.2 장점

일반적인 동작을 하는 코드의 흐름이 오류 처리 코드로 인해 복잡해지지 않습니다. 또한 특정 조건이 발생하면 여러 함수 호출 프레임을 한 번에 건너뛸 수 있도록 합니다. 예를 들어, 오류 코드를 단계별로 전달할 필요 없이, N개의 중첩된 함수 호출을 한 번에 종료할 수 있습니다.

### 2.4.3 단점

제어 흐름이 혼란스러워질 수 있습니다. 라이브러리 호출 시 오류 처리를 놓치기 쉽습니다.

### 2.4.4 권장사항

예외는 특정 조건을 따라야 합니다:

- 특정 조건을 충족하는 경우 기본 예외 클래스를 사용합니다. 예를 들어, 함수 인수를 검증할 때 사전 조건이 만족되지 않는 등 프로그래밍 실수를 나타낼 경우 `ValueError`를 발생시킵니다.

- `assert` 문을 조건문이나 사전 조건 검증 용도로 사용하지 않습니다. `assert`문은 애플리케이션의 핵심 로직에서 중요한 역할을 해서는 안 됩니다. 이를 판단하는 방법으로, `assert` 문을 제거해도 코드가 정상적으로 동작해야 합니다. 즉, `assert` 조건문은 [not guaranteed](https://docs.python.org/3/reference/simple_stmts.html#the-assert-statement) 항상 실행된다는 보장이 없습니다. 다만, [pytest](https://docs.pytest.org/en/stable/) 기반 테스트에서는 `assert` 문을 사용하여 기대값을 검증하는 것이 일반적이며, 이를 사용하는 것이 권장됩니다. 예를 들어 :

```python
# Yes(권장):
  def connect_to_next_port(self, minimum: int) -> int:
    """다음 사용 가능한 포트에 연결합니다.

    매개변수(Args):
      minimum: 1024 이상이어야 하는 포트 값.

    반환값(Returns):
      새로운 최소 포트 값.

    예외(Raises):
      ConnectionError: 사용 가능한 포트를 찾을 수 없을 경우 발생.
    """
    if minimum < 1024:
      # `ValueError`를 발생시키는 경우가 문서 문자열의 "Raises:" 섹션에
      # 명시되지 않은 이유는, API 오용에 대한 특정한 동작을
      # 보장하는 것이 적절하지 않기 때문입니다.
      raise ValueError(f'최소 포트 번호는 1024 이상이어야 합니다. 현재 값: {minimum}.')
    port = self._find_next_open_port(minimum)
    if port is None:
      raise ConnectionError(
          f'{minimum}번 포트 또는 그 이상에서 서비스에 연결할 수 없습니다.')
    # `assert`의 결과에 코드가 의존하지 않습니다.
    assert port >= minimum, (
        f'최소 포트가 {minimum}이어야 하는데, 예상치 못한 포트 {port}가 반환되었습니다.')
    return port
```

```python
# No(주의):
  def connect_to_next_port(self, minimum: int) -> int:
    """다음 사용 가능한 포트에 연결합니다

    매개변수(Args):
      minimum: 1024 이상이어야 하는 포트 값.

    반환값(Returns):
      새로운 최소 포트 값.
    """
    assert minimum >= 1024, '최소 포트 번호는 적어도 1024 이상이어야 합니다.'
    # 아래 코드가 이전 `assert`에 의존합니다.
    port = self._find_next_open_port(minimum)
    assert port is not None
    # 반환문(return statement)에 대한 타입 검사가 `assert`에 의존합니다.
    return port
```

- 라이브러리나 패키지는 자체적인 예외를 정의할 수 있습니다. 이때 반드시 기존 예외 클래스를 상속해야 합니다. 예외 클래스의 이름은 `Error`로 끝나야 하며, `foo.FooError`처럼 불필요한 반복을 포함해서는 안 됩니다.

* 포괄적으로 모든 예외를 잡는 `except:` 문이나 `Exception`, `StandardError`를 사용하지 않습니다. 다만, 다음과 같은 경우에는 예외적으로 허용됩니다.

  - 예외를 다시 발생시키는 경우(re-raising the exception)
  - 예외가 전파되지 않고 기록되거나 무시되도록 하는 격리 지점을 만드는 경우. 예를 들어, 프로그램의 특정 부분이 예외로 인해 중단되지 않도록 보호하는 용도로 사용할 수 있습니다.  
    (예: 스레드의 최상위 블록을 감싸 충돌을 방지하는 경우)

Python은 이 부분에서 매우 관대하며, `except:`문은 오타가 난 변수명, sys.exit() 호출, Ctrl+C 인터럽트, unittest 실패 등 원하지 않는 다양한 예외까지 처리할 수 있습니다.

- `try`/`except` 블록 내의 코드 양을 최소화합니다. `try` 블록이 커질수록, 예상치 못한 코드에서 예외가 발생할 가능성이 높아지며, 이 경우 실제 오류를 숨길 위험이 있습니다.
- `try` 블록에서 예외 발생 여부와 관계없이 특정 코드를 실행하려면 `finally` 블록을 사용합니다. 이는 파일 닫기와 같은 정리(cleanup) 작업을 수행할 때 유용합니다.
