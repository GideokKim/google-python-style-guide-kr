## 2.11 조건식(Conditional Expressions)

간단한 경우에는 사용해도 괜찮습니다.

### 2.11.1 정의

조건식(“삼항 연산자”라고도 함)은 if 문을 짧은 문법(syntax)으로 표현하는 메커니즘입니다. 예 : `x = 1 if cond else 2`.

### 2.11.2 장점

if 문보다 더 짧고 편리합니다.

### 2.11.3 단점

if 문보다 가독성이 떨어질 수 있습니다. 표현이 길어지면 조건을 찾기 어려울 수 있습니다.

### 2.11.4 권장 사항

간단한 경우에는 사용해도 괜찮습니다. 각 부분은 한 줄에 들어가야 합니다: 참(true) 표현식, if 표현식, else 표현식. 표현식이 복잡해지면 일반적인 if 문을 사용하세요.

```python
Yes:
  one_line = 'yes' if predicate(value) else 'no' slightly_split = ('yes' if predicate(value)
                    else 'no, nein, nyet')
  the_longest_ternary_style_that_can_be_done = (
      'yes, true, affirmative, confirmed, correct'
      if predicate(value)
      else 'no, false, negative, nay')
```

```python
 No:
  bad_line_breaking = ('yes' if predicate(value) else
                       'no')
  portion_too_long = ('yes'
                      if some_long_module.some_long_predicate_function(
                          really_long_variable_name)
                      else 'no, false, negative, nay')
```
