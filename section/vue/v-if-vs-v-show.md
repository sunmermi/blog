# v-if VS v-show

#### v-if & v-show 디렉티브 공통

* [vuejs - conditional](https://kr.vuejs.org/v2/guide/conditional.html)
* 조건부의 값에 따라 화면에 엘리먼트를 표시하기 위해 사용
* 표현식이 true 값을 반환할 때 보여짐

&#x20;

#### v-if VS v-show 디렉티브 차이

* [v-if VS v-show](https://vuejs.org/guide/essentials/conditional.html#v-if-vs-v-show)

> 일반적으로 말하면 v-if는 토글 비용이 더 높은 반면 v-show는 초기 렌더 비용이 더 높습니다.\
> 따라서 무언가를 매우 자주 전환해야 하는 경우에는 v-show를 선호하고 실행 시 조건이 변경될 가능성이 낮으면 v-show를 선호합니다.

&#x20;

#### v-if 디렉티브 (v-else-if, v-else)

* 표현식이 true 값을 반환할 때만 렌더링됨
* 초기값에 한하여!
* 내부에 다른 컴포넌트, 다른 디렉티브(`v-for...` 등) 많이 포함할 경우
* 예 : 로그인, 로그아웃 버튼
* [v-if](https://vuejs.org/api/built-in-directives.html#v-if)

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
* 토글 빈도가 높은 경우, 내부 컴포넌트 없고 디렉티브 사용도 없는 경우
* 예 : 모달
* [v-show](https://vuejs.org/api/built-in-directives.html#v-show)

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
