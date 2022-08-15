# v-for 와 v-if 동시사용

#### v-if와 v-for 디렉티브의 우선순위

* [뷰 공식문서 지침](https://v3.ko.vuejs.org/guide/migration/v-if-v-for.html#frontmatter-title)
* 권장하는 방법은 아니지만, 필요한 경우가 있을 수 있기에...
* 2.x 구문
  * 2.x에서는 동일한 엘리먼트에 `v-if`와 `v-for`를 함께 사용할 때, `v-for`가 더 높은 우선순위를 갖습니다.
* 3.x 구문
  * 3.x에서는 `v-if`가 항상 `v-for` 보다 더 높은 우선순위를 갖습니다.

#### :warning: 같이 사용하는건 No

* [v-for with v-if](https://vuejs.org/guide/essentials/list.html#v-for-with-v-if)
* 아래 코드와 같이 작성하는걸 권장한다.

```
// as-is
<li v-for="todo in todos" v-if="!todo.isComplete">
  {{ todo.name }}
</li>

// to-be
<template v-for="todo in todos">
  <li v-if="!todo.isComplete">
    {{ todo.name }}
  </li>
</template>
```

```
// as-is
<li v-if="todos.length" v-for="todo in todos">
  {{ todo.name }}
</li>

// to-be
<template v-if="todos.length">
  <li v-for="todo in todos">
    {{ todo.name }}
  </li>
</template>
<li v-else> None List </li>
```

&#x20;
