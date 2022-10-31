---
description: 간단한 개념 및 관련 공식 문서 또는 참고 링크
---

# React Simple Summary



#### React

* [React 특징](https://sunmermi.gitbook.io/blog/section/react/react.js)
* 컴포넌트들로 만들어진 UI 라이브러리



#### framework and library

* 프레임워크는 이미 완성품으로 정해진 롤대로 사용 해야 합니다. 예로 앵귤러
* 라이브러리는 내 입맛에 맞게 기능을 골라서 사용 할 수 있습니다. 예로 리액트



#### Components

* [Components에 관해](https://sunmermi.gitbook.io/blog/section/react/components)
* 독립적, 고립적, 재사용성, 복잡하고 긴 로직을 작게 분리

&#x20;

#### Virtual DOM

* [Virtual DOM에 관해](https://sunmermi.gitbook.io/blog/section/react/virtual-dom)
* 상태가 변경되면 이전에 저장된 돔트리와 비교해서 실제 업뎃되어야 하는 부분만 모아서 다시 렌더링 한다.



#### props

* 부모로부터 전달된 프로퍼티이고 읽기 전용
* 상황에 따라 주어진 데이터를 받고 그 데이터에 맞게 UI를 보여준다.
* 재사용 높인다.
* [React 공식 - props](https://ko.reactjs.org/docs/components-and-props.html#props-are-read-only)

&#x20;

#### state

* 컴포넌트에서 본인이 가지고 있는 데이터
* 상태가 변경되면 render() 함수가 재실행된다.
* [React 공식 - State 라이프사이클](https://ko.reactjs.org/docs/state-and-lifecycle.html)
* [React 공식 - State](https://ko.reactjs.org/docs/react-component.html#state)

&#x20;

#### 라이프 사이클

* 특정 시점에 코드가 실행되도록 설정하는 메서드
* [React 공식](https://ko.reactjs.org/docs/react-component.html#the-component-lifecycle)

&#x20;

#### 리액트 훅

* 함수형 컴포넌트를 사용할 때 상태 및 라이프 사이클 관리할 수 있도록 도움.
* [React 공식](https://ko.reactjs.org/docs/hooks-overview.html)
* [React 공식 - hooks 도입 이유](https://ko.reactjs.org/docs/hooks-intro.html#motivation)
* [추가해서 볼만한 블로그 포스팅](https://defineall.tistory.com/900)

&#x20;

#### JSX

* 자바스크립트를 확장하여 사용한 문법으로 JS에서 html 문법을 사용함.
* JavaScript이기 때문에 JS의 기능을 사용사용 하여 마크업 가능.
* [React 공식 - JSX](https://ko.reactjs.org/docs/introducing-jsx.html)
* [추가해서 볼만한 블로그 포스팅](https://velog.io/@gyumin\_2/React-JSX%EB%9E%80%EC%A0%95%EC%9D%98-%EC%9E%A5%EC%A0%90-%EB%AC%B8%EB%B2%95-%ED%8A%B9%EC%A7%95-%EB%93%B1)

&#x20;

#### Ref

* `Ref`는 `render` 메서드에서 생성된 DOM 노드나 React 엘리먼트에 접근하는 방법을 제공합니다.
* [reactjs - refs](https://ko.reactjs.org/docs/refs-and-the-dom.html)
* [ref.md](ref.md "mention")



