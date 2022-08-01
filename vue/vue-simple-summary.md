---
description: 간단한 개념 및 관련 공식 문서 또는 참고 링크
---

# Vue Simple Summary

#### v-if

* [vuejs - conditional](https://kr.vuejs.org/v2/guide/conditional.html)
* 조건에 따라 블록을 렌더링하기 위해 사용
* 표현식이 true 값을 반환할 때만 렌더링

```
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>
```

&#x20;

#### v-show

* [vuejs - conditional](https://kr.vuejs.org/v2/guide/conditional.html)
* 엘리먼트를 조건부로 표시하기 위한 또 다른 옵션은 `v-show` 디렉티브입니다.
* 항상 렌더링 되고 DOM에 남아있다는 점이 `v-if`와의 차이점
* 표현식이 true 값을 반환할 때 엘리먼트에 `display` CSS 속성을 토글합니다.





```
<h1 v-show="ok">안녕하세요!</h1>
```
