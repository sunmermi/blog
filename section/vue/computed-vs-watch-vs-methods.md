---
description: Computed vs Watch vs Methods 언제 어떻게 사용할까?
---

# Computed vs Watch vs Methods

####

#### Computed vs Watch vs Methods 언제쓸까?

#### Computed는

* [vuejs - Computed](https://kr.vuejs.org/v2/guide/computed.html)
* 데이터다
* 간단한 연산일 때
* `data`의 데이터들과 의존성
* `computed` 속성은 의존(종속) 대상을 따라 \*\*저장(캐싱)\*\*된다
* 의존되어(종속) 있는 데이터가 변했을 경우에만 재 렌더링 한다.
* 데이터가 변경되지 않는 한, `computed` 속성 함수들은 계산을 다시 하지 않고 계산되어 있던 결과를 반환
* `return` 되는 값으로 셋팅됨.
* 페이지가 처음 렌더링될 때 데이터를 업데이트 하려고 한다면 사용

```
// Vue.js 공식 홈페이지에 나와있는 예제
<template>
  <div>
    <p>원본 메시지: "{{ message }}"</p>
    <p>역순으로 표시한 메시지: "{{ reversedMessage }}"</p>
  </div>
</template>

<script>
export default {
  data(){
    return {
      message: '안녕하세요'
    }
  },
  computed: {
    // 계산된 getter
    reversedMessage: function () {
      return this.message.split('').reverse().join('')
    }
  }
}
</script>
```

* computed 프로퍼티를 보면 reverseMessage 라는 프로퍼티에 값으로 익명함수가 할당되어있다.
* computed에 정의하는 이 익명함수는 반드시 값을 리턴하도록 작성되야한다.

&#x20;

#### Watch는

* [vuejs - Watch](https://kr.vuejs.org/v2/guide/computed.html#watch-%EC%86%8D%EC%84%B1)
* 콜백함수
* 인자를 받거나 특정 액션이 필요한 경우
* 감시할 데이터가(특정 프로퍼티) 변경되면 함수가 실행됨
* 계속해서 데이터가 빈번하게 바뀔때

```
// Vue.js 공식 홈페이지에 나와있는 예제
<template>
  <div>
    <p>원본 메시지: "{{ message }}"</p>
    <p>역순으로 표시한 메시지: "{{ reversedMessage }}"</p>
  </div>
</template>

<script>
export default {
  data(){
    return {
      message: '안녕하세요',
      reversedMessage: ''
    }
  },
  watch: {
    message: function (newVal, oldVal) {
      this.reversedMessage = newVal.split('').reverse().join('')
    }
  }
}
</script>
```

* `watch`는 아무 프로퍼티도 생성하지 않고 익명함수는 단순히 콜백함수로의 역할을 한다.
* `watch`에 명시된 프로퍼티는 감시할 대상을 의미할 뿐이다.

&#x20;

#### methods는

* 업데이트 라이프 사이클이 동작한(=아무 변수나) 변수 변경이 있을때 마다 무조건 항상 함수를 실행
* 인자를 받고 액션이 필요한 경우, 혹은 인자를 받고 그 값을 이용해서 다른값을 내야할때

```
// Vue.js 공식 홈페이지에 나와있는 예제
<template>
  <div>
    <p>원본 메시지: "{{ message }}"</p>
    <p>역순으로 표시한 메시지: "{{ reversedMessage }}"</p>
  </div>
</template>

<script>
export default {
  data(){
    return {
      message: '안녕하세요',
      reversedMessage: ''
    }
  },
  methods: {
    reversedMessage: function () {
      return this.message.split('').reverse().join('')
    }
  }
}
</script>
```

&#x20;

#### 캐싱이 필요한 이유

코드를 작성하다보면 자주 바뀌지는 않지만 중요한 계산이 필요할 때가 있다. 그때 `methods`를 사용하면 렌더링 될때마다 계산을 진행해야한다. 따라서 이 경우에는 `computed` 를 사용해 변경시에만 호출하도록 하는 것이 좋다.

&#x20;

#### computed와 methods와의 차이점\*\*

* `template`에서 호출시 ()를 적지 않아야 된다.
* `return` 값이 반드시 존재해야한다.
* 파라미터를 받을 수 없다.

&#x20;

#### 참고

* [watch와 computed 의 차이와 사용법](https://blog.jeongwoo.in/vue-js-watch%EC%99%80-computed-%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%99%80-%EC%82%AC%EC%9A%A9%EB%B2%95-e2edce37ec34)
* [참고링크1](https://medium.com/@hozacho/%EB%A7%A8%EB%95%85%EC%97%90vuejs-computed-vs-watch-%EC%96%B8%EC%A0%9C%EC%8D%A8%EC%95%BC%ED%95%A0%EA%B9%8C-d25316c4ef42)
* [참고링크2](https://kamang-it.tistory.com/entry/Vue23computed-%EA%B7%B8%EB%A6%AC%EA%B3%A0-methods%EC%99%80%EC%9D%98-%EC%B0%A8%EC%9D%B4featwatch)
