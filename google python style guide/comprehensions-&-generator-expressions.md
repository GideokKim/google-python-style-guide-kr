## 2.7 컴프리헨션 & 제너레이터 표현식
상황이 단순하다면 사용해도 좋습니다.

### 2.7.1 정의
리스트(List), 딕셔너리(Dict), 집합(Set) 컴프리헨션(coprehension)과 제너레이터(generator) 표현식은 기존의 반복문, `map()`, `filter()`, 또는 `lambda`에 의존하지 않고 컨테이너 타입과 이터레이터를 생성하는 간결하고 효율적인 방식을 제공합니다.

### 2.7.2 장점
단순한 컴프리헨션이 dict, list, 또는 set을 생성하는 다른 기술보다도 더 명확할 수 있습니다. 제너레이터 표현식은 list 전체를 생성하는 것을 예방하므로 매우 효율적일 수 있습니다. 

### 2.7.3 단점
복잡한 컴프리헨션이나 제너레이터 표현식은 가독성을 떨어트릴 수 있습니다.

### 2.7.4 권장 사항
컴프리헨션의 사용은 허용되지만, 여러 개의 `for` 절과 필터(filter) 표현식은 용인되지 않습니다. 간결함이 아니라, 가독성을 위해 코드를 최적화하세요.


```python
Yes:
  result = [mapping_expr for value in iterable if filter_expr]

  result = [
      is_valid(metric={'key': value})
      for value in interesting_iterable
      if a_longer_filter_expression(value)
  ]

  descriptive_name = [
      transform({'key': key, 'value': value}, color='black')
      for key, value in generate_iterable(some_input)
      if complicated_condition_is_met(key, value)
  ]

  result = []
  for x in range(10):
    for y in range(5):
      if x * y > 10:
        result.append((x, y))

  return {
      x: complicated_transform(x)
      for x in long_generator_function(parameter)
      if x is not None
  }

  return (x**2 for x in range(10))

  unique_names = {user.name for user in users if user is not None}
```
```python
No:
  result = [(x, y) for x in range(10) for y in range(5) if x * y > 10]

  return (
      (x, y, z)
      for x in range(5)
      for y in range(5)
      if x != y
      for z in range(5)
      if y != z
  )
```
