---
layout: post
section-type: post
title: (Django) 모델에 initial data를 넣는 방법 (fixture, RunPython, RunSQL)
category: django
tags: [ 'django', 'python', 'ORM' ]
---

> [장고 공식 문서](https://docs.djangoproject.com/en/1.10/howto/initial-data/)를 참고해 작성

# fixture를 사용

fixture란 django가 DB에서 import하는 방식을 알고 있는 데이터들의 집합이라고 한다.(이게 뭔소리지)
이미 몇몇 데이터를 가지고 있고 fixture를 생성하는 가장 직관적인 방법은 ```manage.py dumpdata``` 명령어를 사용하면 된다.  
fixture는 json,xml,yaml으로 작성될 수도 있다.

예를 들면, Person model의 이런 json 문서가 있을 수 있다.

``` json
[
  {
    "model": "myapp.person",
    "pk": 1,
    "fields": {
      "first_name": "John",
      "last_name": "Lennon"
    }
  },
  {
    "model": "myapp.person",
    "pk": 2,
    "fields": {
      "first_name": "Paul",
      "last_name": "McCartney"
    }
  }
]
```

yaml은 이런 식이 될 수 있다.  

```
- model: myapp.person
  pk: 1
  fields:
    first_name: John
    last_name: Lennon
- model: myapp.person
  pk: 2
  fields:
    first_name: Paul
    last_name: McCartney
```

이 데이터들을 로딩하는 방법은 간단하다.

``` text
manage.py loaddata <fixturename>
```

를 사용하면 되고, <fixturename>은 생성한 inital-data의 파일이 되겠다.
loaddata를 실행할 때마다 데이터는 fixture에서 읽혀질꺼고 DB로 다시 로드된다.
이는 fixture에서 생성된 열중 하나를 바꾸고 다시 loaddata를 실행한다면 예전에 만들었던 그 파일을 제거할 것이란 걸 알아두자.

# migrations으로 initial-data 넣기

fixture를 사용하지 않고 자동적으로 initial-data를 넣고 싶다면 RunPython 혹은 RunSQL을 이용해 앱의 migration을 생성하자.

## RunPython

## RunSQL  
