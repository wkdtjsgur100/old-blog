---
layout: post
section-type: post
title: pytest [작성중]
category: pytest
tags: [ 'pytest', 'tdd','python','test' ]
---

> pytest [공식 문서](http://doc.pytest.org/en/latest/contents.html)를 바탕으로 요약 정리 한 문서

# 설치

``` text
pip install -U pytest
```

# 예제

``` python
# content of test_sample.py
def func(x):
    return x + 1

def test_answer():
    assert func(3) == 5
```

# 실행

test_sample.py 파일이 있는 경로에서 pytest 입력  
아래는 실행 결과이다.  
![실행 결과](/assets/pytest1.png)

pytest에서 test 파일을 감지하는 방법은 [pytest convention rule](http://doc.pytest.org/en/latest/goodpractices.html#test-discovery)에 나와있는데 간단히 요약하면 다음과 같다.

* 기본적으로 arg가 없으면 현재 디렉터리에 있는 test파일을 찾지만, 옵션으로 줄 수도 있다.
* recursive dir가 아니면([norecursedirs](http://doc.pytest.org/en/latest/customize.html#confval-norecursedirs)) 재귀적으로 디렉터리를 탐색한다.
* 디렉터리를 탐색할 때 ``` test_*.py ``` 또는 ``` *_test.py ``` 를 찾는다.
* 위에서 찾은 파일을 바탕으로, 아래와 같은 test 요소들을 수집한다.
  * 이름이 test_ 로 시작하는 클래스 외부의 function.
  * 클래스 이름이 Test로 시작하는 클래스 내에서 이름이 test_로 시작하는 메서드(``` __init__ ```이 없어야 함)
* 파이썬 모듈에서는, 표준 [unittest.TestCase](http://doc.pytest.org/en/latest/unittest.html#unittest-testcase) 을 사용해 테스트들을 감지한다.

# 다중 테스트 실행

## 특정 exception이 일어나는 것을 assert 해보자

``` python
# content of test_sysexit.py
import pytest
def f():
    raise SystemExit(1)

def test_mytest():
    with pytest.raises(SystemExit):
        f()
```

[with 구문](http://ingorae.tistory.com/505)을 사용해서 예외를 raises를 시킨 코드이다.
위의 프로그램을 -q 옵션(로그를 간단히 표시하는 옵션)을 통해 실행해 보면, 아래와 같다

```
$ pytest -q test_sysexit.py
.
1 passed in 0.12 seconds
```

# Going functional: requesting a unique temporary directory

Functional 테스트의 경우 몇몇 파일을 만들어서 어플리케이션에 넘겨야 합니다.
