---
description: 조건에 따라 렌더링 되는 html 요소를 변경하고 싶었고 해결방안으로 사용된 Dynamic Components와 :is
---

# Dynamic Components (동적 컴포넌트), :is attribute

#### 상황

버튼 컴포넌트를 작업하면서 생긴 이슈이다.

디자인이 버튼모양으로 역활이 Button, Anchor로도 사용되고 있는 상황이였고 같은 디자인을 가졌는데 굳이 따로 만들 필요가 없을 것 같아서 버튼 컴포넌트 한가지로 링크(href)가 있으면 `a`로도 렌더링되고 `button` 요소로도 렌더링이 되었으면 했다.



**처음 작업한 코드**&#x20;

리뷰해주신 프론트 개발자분이 `a`랑 `button`이 `props`도 마크업구조도 다 동일하다. 라는 리뷰는 해주셨다.&#x20;

그러게요...ㅜㅜ 저도 그 부분이 참 걸렸고 `props`가 추가 될 때 마다 아래위로 다 넣어줘야해서 불편했는데 방법을 찾아보자!

```
<a 
  v-if="href"
  :class="[
    'link',
    {
      round: round,
      liner: liner,
      icon: icon,
      ...
    },
  ]"
  ...props
>
...
</a>
<button 
  v-else
  :class="[
    'button',
    {
      round: round,
      liner: liner,
      icon: icon,
      ...
    },
  ]"
  ...props
>
...
</button>
```

****

**리팩토링한 코드**&#x20;

구글링으로 찾다보니 Dynamic Components가 있었다. 바로 적용을 해보았고 깜끔했다.

아래는 `:is` prop 에는 문자열이나 컴포넌트 이름을 넣을 수 있다. 자세한건 아래 참고 링크들을 면 된다.

```
<component 
  :is="href ? 'a' : 'button'"
  :class="[
    href ? 'link' : 'button',
    {
      round: round,
      liner: liner,
      icon: icon,
      ...
    },
  ]"
  ...props
>
...
</component>
```

####

#### 참고링크&#x20;

* [Vue - Dynamic Components](https://vuejs.org/guide/essentials/component-basics.html#dynamic-components)
* [Vue - `:is`](https://vuejs.org/api/built-in-special-attributes.html#is)
* [Vue Ko - 내장 컴포넌트(Built-In Components)](https://v3.ko.vuejs.org/api/built-in-components.html#component)
* [Vue Ko - 동적 컴포넌트](https://v3.ko.vuejs.org/guide/component-dynamic-async.html#keep-alive%E1%84%85%E1%85%B3%E1%86%AF-%E1%84%89%E1%85%A1%E1%84%8B%E1%85%AD%E1%86%BC%E1%84%92%E1%85%A1%E1%84%82%E1%85%B3%E1%86%AB-%E1%84%83%E1%85%A9%E1%86%BC%E1%84%8C%E1%85%A5%E1%86%A8-%E1%84%8F%E1%85%A5%E1%86%B7%E1%84%91%E1%85%A9%E1%84%82%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3)



