# v-if & v-show 디렉티브

#### v-if & v-show 디렉티브

* [vuejs - conditional](https://kr.vuejs.org/v2/guide/conditional.html)
* 조건부의 값에 따라 화면에 엘리먼트를 표시하기 위해 사용
* 표현식이 true 값을 반환할 때 보여짐

&#x20;

#### v-if 디렉티브

* 표현식이 true 값을 반환할 때만 렌더링됨

```
<h1 v-if="awesome">Vue is awesome!</h1>
<h1 v-else>Oh no 😢</h1>

// true html 렌더링
<h1>Vue is awesome!</h1> 

// false html 렌더링
<h1>Oh no 😢</h1>
```

&#x20;

#### v-show 디렉티브

* 표현식이 true 값을 반환할 때 엘리먼트를 `display` 로 `none, block`하여 CSS 속성을 토글해서 보여줌
* 개발자 도구를 확인 해보면 항상 렌더링 되고 DOM에 남아있다는 점이 `v-if`와의 차이점

```
<h1 v-show="awesome">Vue is awesome!</h1>
<h1>Oh no 😢</h1>

// true html 렌더링 
<h1>Vue is awesome!</h1> // css display: block; 로 컨트롤
<h1>Oh no 😢</h1>

// false html 렌더링 
<h1>Vue is awesome!</h1> // css display: none; 로 컨트롤
<h1>Oh no 😢</h1>
```
