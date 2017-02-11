---
layout: post
section-type: post
title: pytest를 사용해보자 (2)
category: pytest
tags: [ 'pytest', 'tdd','python','test' ]
---

# Setting a breakpoint / aka set_trace()

breakpoint를 설정하고 ```pdb.set_trace()```를 입력하려면 helper를 사용할 수 있습니다.

``` python
import pytest
def test_function():
  ...
  pytest.set_trace()  # invoke PDB debugger and tracing
```

pytest 버전 2.0.0 이전에 ```pytest -s``` 명령어로 캡처하는 것을 비활성화 시키면 PDB tracing을 입력 할 수 있었지만, 그 이후의 버전은 pytest가 자동적으로 비활성화 시켜준다.

* 다른 테스트들의 출력 캡처는 영향을 미치지 않는다.
* 이미 캡쳐 된 이전 테스트 출력은 그대로 처리됩니다.
* 동일한 테스트 내 에서 생성된 이후의 출력은 캡처되지 않고 직접적으로 ```sys.stdout```에 보내집니다. 대화형 PDB 추적 세션을 종료하고 정기적인 테스트 실행을 계속 한 후 테스트 출력 발생 조차도 true가 유지된다는 점에 주목해야 합니다.
