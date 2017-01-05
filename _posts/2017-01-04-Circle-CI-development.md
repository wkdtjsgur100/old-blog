---
layout: post
section-type: post
title: Circle-CI
category: tech
tags: [ 'tag1', 'tag2' ]
---

# CI(Continuous Integration)란?

  소프트웨어 공학에서, 지속적 통합(continuous integration, CI)은 지속적으로 퀄리티 컨트롤을 적용하는 프로세스를 실행하는 것이다. - 작은 단위의 작업, 빈번한 적용. 지속적인 통합은 모든 개발을 완료한 뒤에 퀄리티 컨트롤을 적용하는 고전적인 방법을 대체하는 방법으로서 소프트웨어의 질적 향상과 소프트웨어를 배포하는데 걸리는 시간을 줄이는데 초점이 맞추어져 있다. 대표적인 CI 툴에는 젠킨스(Jenkins)가 있다.

  언젠가는 저장소가 개발자들의 베이스라인과는 너무 많이 달라지게 되는 "통합의 지옥"[1] 이라 불리는 상황에 빠지게 된다. 이 경우, 작업하는 시간보다 작업 내용을 통합하는데 걸리는 시간이 더 걸리게 되어, 최악의 경우 개발자들이 자신들의 변경 내용들을 취소하고 작업들을 완전히 처음부터 다시하는 것이 나을 수도 있다.

  지속적인 통합은 초기에 그리고 자주 통합해서 "통합의 지옥"의 함정을 피하는 것을 내포하고 있다. 지속적인 통합은 재작업을 줄여서 비용과 시간을 줄이는데 초점이 맞추어져 있다.

## CI Tools
* CircleCI : 무료. 빌드는 한번에 하나만 돌릴 수 있다는 단점.
* Jenkins : 설치, 관리가 어려움. 대기업에서 주로 사용
* TravisCI : 학생은 무료.

## 위 CI Tool들 중에서 Circle-CI에 대해서 알아보자.

자세한 내용은 밑의 링크에서 확인할 수 있다.<br>
Tutorial Link : https://circleci.com/docs/getting-started/

위의 튜토리얼을 살펴보며 얻었던 지식들을 대략 정리해보자

* circleci 대쉬보드를 이용해 repo를 선택하게 되면 no tests란 에러가 뜨게 된다. 그 이유는 말 그대로 test가 정의되지 않아서 인데, test는 repo의 루트 디렉터리에 있는 circle.yml 파일에 정의하면 된다고 한다.

* repo에 커밋이 될 때마다 자동으로 CI가 작동되게 된다. 성공적으로 빌드가 완료되게 되면 fixed란 메세지가 뜬다.

* 먼저 circle.yml 파일을 잘 이해할 필요가 있어서, circle.yml이 어떤 기능을 하고 어떤 것을 정의 해야 하는지 알 필요가 있다.

##### Circle.yml
![phase](/screenshot/test_phase.png)
