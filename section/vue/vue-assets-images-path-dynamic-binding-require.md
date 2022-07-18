---
description: 버튼 컴포넌트에서 `src/assets/images/...` 디렉토리 내부 이미지 소스 적용시 동적 바인딩 관련 이슈
---

# vue assets images path dynamic binding - require()

#### 상황

현재 뷰 환경에서 버튼이 중구난방으로 작업되어 있고 버튼 컴포넌트로 분리 되어있지 않아서 만들기로 했다.\
그러다가 텍스트 앞에 아이콘이 있는 디자인이 있는데 넣으려고 보니 아이콘 이미지 소스도 정리도 안되어있고, 이미지 파일명도 너무나 중구 난방.. 흠.. 이미지의 확장자 `.png`라는것만 공통되어 있었다.

난 한달뒤면 철수하는 상황이기에 최대한 유지보수가 좋은 방향을 찾아야 했고\
아이콘 컴포넌트를 만들어서 만들까 하다가 버튼에 `iconName prop`을 받아서 해야겠다 마음을 먹었다.

&#x20;

#### 컴포넌트 분리 처음 코드

아래 코드의 우려사항이 만약 아이콘 버튼이 새로 추가 하면 아이콘 이미지를 추가하고 화면에 버튼 요소도 추가하고 또 버튼 컴포넌트에 스타일로 아이콘 경로까지 넣고 총 3번을 건들여야 한다. 맘에 안든다.

```
<template>
  <button ... class="button">
    <i v-if="iconName" :class="['icon', iconName]"></i>
    button
  </button>
</template>

<style lang="scss" scoped>
.button {
  .icon {
    ...
    background: no-repeat center center / contain;

    &.plus {
      background-image: url(assets/images/icon_plus.png);
    }
  }

  &:hover {
    .icon {
      ...
      &.plus {
        background-image: url(assets/images/icon_plus_hover.png);
      }
    }
  }
}
</style>

// 사용
<Button iconName="plus" ...>
  추가
</Button>
```

&#x20;

#### 컴포넌트 개선 코드

이미지를 정리할 수 없는 상황이고 이미지의 파일명도 뒤죽 박죽 통일성 하나 없다. 그리고 피씨 전용 화면이기 때문에 마우스 `hover` 상태디자인이 필요해서 이미지가 변경이 되어야 한다. 어떤분이 유지보수 하게 될지 모르지만 사용성이 좋아야한다.

선택한 방법은\
`iconName prop`를 받을때 이미지 파일명을 받아서 인라인 스타일로 `background-image url`로 넣어 주는 방법이다. 그리고 상태디자인은 `iconHover prop`까지 받아서 관리해주기로

`iconHover` 프롭이 추가 된게 오버 스펙일까 싶지만 정리되지 않은 디자인들 때문에 매번 버튼컴포넌트가 변경되야하는게 더 싫을것 같았다.

```
<template>
  <button ...>
    <i
      v-if="iconName"
      :style="[
        iconName && {
          backgroundImage: 
            `url(${require('@/assets/images/' +
            (isHover ? iconHover : iconName) +
            '.png')})`,
        },
      ]"
    ></i>
    button
  </button>
</template>

<style lang="scss" scoped>
.button {
  .icon {
    ...
    background: no-repeat center center / contain;
  }
}
</style>

// 사용
<Button iconName="plus" iconHover="plus_hover" ...>
  추가
</Button>
```

&#x20;

#### require() 사용

백그라운드 이미지 유알엘에 `require()`을 사용하게 되었는데 사용하지 않으면 렌더링이 아래와 같이 `'@/assets/...'` 이렇게 경로가 나오기 때문이다.\
이유는 `src/assets` 디렉토리에 있는 정적인 소스는 동적으로 불러오지 못한다.

```html
<i style="background-image: url('@/assets/images/plus.ong');"></i>
```

이를 해결하기 위해 서칭해보니 해당 이미지 경로를 `import` 해야한다고 하면서 `require()`를 사용했다. 아래와 같이 수정했더니 원하는 방식대로 이미지가 잘 불러와 졌다.

```
<i :style="backgroundImage: `url(${require('@/assets/images/' + iconName + '.png')})`"></i>

// html 렌더링
<i style="background-image: url('data:image....');"></i>
```

&#x20;

#### 모르겠고 아쉬운점

`url(${require('@/assets/images/' + iconName + '.png')})` 에서\
백틱을 사용하고 `${}` 보관법을 사용해 `require()`를 사용했는데 그 내부에 또 다른 변수 `iconName`을 받고 싶은데 어떻게 표현할지 몰라서 `'텍스트' + 변수명 + '텍스트'` 이렇게 작성했는데 보관법안에 보관법은 사용 못하나요..? 😢

&#x20;

#### 참고

* [vue javascript 내에서 정적 자산을 참조하는 방법](http://daplus.net/javascript-vue-javascript-%EB%82%B4%EC%97%90%EC%84%9C-%EC%A0%95%EC%A0%81-%EC%9E%90%EC%82%B0%EC%9D%84-%EC%B0%B8%EC%A1%B0%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95/)
* [\[Vue.js\] img 태그 src 속성 사용 시 이미지가 나타나지 않는 경우 해결](https://lifere.tistory.com/entry/Vuejs-img-%ED%83%9C%EA%B7%B8-src-%EC%86%8D%EC%84%B1-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80%EA%B0%80-%EB%82%98%ED%83%80%EB%82%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0-%ED%95%B4%EA%B2%B0)
* javascript require()
