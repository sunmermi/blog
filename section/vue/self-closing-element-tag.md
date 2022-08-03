# self closing element(tag)

#### Vue component self closing

* 컴포넌트 내부에 자식요소가 없는 단일 컴포넌트는 셀프 클로징이 가능하다.
* [뷰 셀프클로징](https://v2.vuejs.org/v2/style-guide/?redirect=true#Self-closing-components-strongly-recommended)

```
// Bad
<!-- In single-file components, string templates, and JSX -->
<MyComponent></MyComponent>
<!-- In DOM templates -->
<my-component />


// Good
<!-- In single-file components, string templates, and JSX -->
<MyComponent />
<!-- In DOM templates -->
<my-component></my-component>
```
