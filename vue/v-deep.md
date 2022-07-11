# ::v-deep 딥셀렉터

#### 상황

버튼 컴포넌트를 만들고 적용하는데 스타일을 커스텀해야하는 상황이 생겼다. 컴포넌트에서 공통으로 수정하기엔 오버 스펙인것 같았고 너무 단발적인 스타일 변화였다.

그래서 사용하는 다른 컴포넌트에서 버튼컴포넌트의 클래스네임을 셀렉해서 스타일을 수정하면 되겠지 싶었는데 마음대로 안됐다.. 아예 적용이 안됐다.

####

#### 이슈 발생 이유

`vue-loader` 에서 제공하는 기능인 스타일 캡슐화(Scoped CSS) 때문이라고 한다.

옛날 방식의 스타일 코드들을 보면 코드를 통으로 잡아서 넣기 때문에 전역으로 스타일이 적용된다. (+ `scoped` 를 안해도 마찬가지..) 때문에 유지 보수시 css 캐스캐이딩(우선순위) 때문에 스타일을 적용하기 위해서 자꾸만 css 셀렉터 구문이 길어지고 본의 아니게 다른곳에 영향을 끼쳐서 스타일이 망가지는 일들이 다분했다.

하지만 뷰에서는 아래와 같이 `scoped` 를 사용해서 스타일을 캡슐화 할 수 있어서 해당 컴포넌트에서만 스타일이 적용되고 다른곳에 영향을 끼치지 않는다.

```
<style scoped>
.example {
  color: red;
}
</style>

<template>
  <div class="example">안녕</div>
</template>

// 렌더링된 코드는 [data-v-....]이 붙는다. 그래서 저기에 적용이 되는것
<style>
.example[data-v-f3f3eg9] {
  color: red;
}
</style>

<template>
  <div class="example" data-v-f3f3eg9>안녕</div>
</template>
```

####

#### 해결방법 ::v-deep 사용

스타일 캡슐화된 하위 컴포넌트의 스타일을 수정할 수 있는 방법은 `::v-deep` 를 사용하면 된다.

```
<style scoped>
.a >>> .b { /* ... */ }
</style>

<style scoped>
.a /deep/ .b { /* ... */ }
</style>

// 권장 방법 : scss, sass 와 같은 전처리기에서 위 구문을 인식하지 못할 수 있기 때문에 아래 방법 권장
<style scoped>
.a::v-deep .b { /* ... */ }
</style>
```



#### 이슈 코드

```
// 버튼 컴포넌트
<template>
  <button class="button">
    <i v-if="icon" class="icon"></i>
    <slot></slot>
  </button>
</template>

// 이슈 코드 : 스타일 적용 안됨
<Button icon="add">버튼</Button>

<style scoped>
.button {
  .icon {
    width: 30px;
    height: 30px;
  }
}
</style>

// 수정 코드
<Button icon="add">버튼</Button>

<style scoped>
.button {
  ::v-deep .icon {
    width: 30px;
    height: 30px;
  }
}
</style>
```

####

#### Scoped CSS 이슈 - `::v-deep` 사용이 필요한 경우

하위 컴포넌트와 `v-html` 사용시 스타일 적용이 필요할 경우 그리고 뷰 UI 라이브러리를 사용해서 커스텀이 필요한 경우에 `::v-deep`을 사용해서 해결할 수 있는데 자세한건 [Vue.js Scoped CSS의 이슈들과 해법을 포스팅한 블러그](https://blog.jeongwoo.in/vue-js-scoped-css-1b77c9a1b8bb) 참고하면 좋을 것 같다.

####

#### 참고

* [Mdn - css cascading](https://developer.mozilla.org/ko/docs/Web/CSS/Cascade)
* [vue loader - scoped css](https://vue-loader-v14.vuejs.org/kr/features/scoped-css.html)
* [vue loader - deep selectors](https://vue-loader.vuejs.org/guide/scoped-css.html#deep-selectors)

