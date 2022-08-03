# self closing element(tag)

#### React JSX component self closing

* JSX : 태그는 꼭 닫혀있어야 한다는 규칙이 존재
* [참고](https://ko.reactjs.org/docs/introducing-jsx.html#gatsby-focus-wrapper)
* 컴포넌트 내부에 자식요소가 없는 단일 컴포넌트는 셀프 클로징이 가능하다.

```jsx
// Bad
<img> // error
<MyComponent></MyComponent>

// Good
<img />
<MyComponent />
```
