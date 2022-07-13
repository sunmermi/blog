---
description: 리액트에서 Component 를 만들 때 class와 function 차이
---

# Component (Class, Function)

#### class, function 방식의 차이

| 16.8 이전 버전 | class 방식 | function 방식          |
| ---------- | -------- | -------------------- |
| \~ 이전 버전   |          |                      |
| state      | 상태관리 가능  | 상태관리 불가, 정적데이터 보여줄 때 |
| 라이프사이클     | 매서드 존재   | 없음                   |

| 16.8 버전부터 | class 방식 | function 방식                                                                                    |
| --------- | -------- | ---------------------------------------------------------------------------------------------- |
|           | 기존과 동일   | [React 공식 - Hooks](https://ko.reactjs.org/docs/hooks-intro.html)를 이용해서 상태관리, 라이프사이클을 사용할 수 있다. |



#### 함수 방식 유행 이유

* [React 공식 - hooks 도입 이유](https://ko.reactjs.org/docs/hooks-intro.html#motivation)
* 클래스 방식 어려움,
* `this`의 반복 사용
* 라이프사이클 사용시 반복 코드 많아짐, 복잡해지고 이해가 어려워짐
* 함수형 프로그래밍이 유행



#### class 방식

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

#### function 방식

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```



#### 참고

* [React 공식 - 함수 컴포넌트와 클래스 컴포넌트](https://ko.reactjs.org/docs/hooks-intro.html#motivation)
