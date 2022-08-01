# Ref

#### Ref

* `Ref`는 `render` 메서드에서 생성된 DOM 노드나 React 엘리먼트에 접근하는 방법을 제공
* [React 공식 - refs](https://ko.reactjs.org/docs/refs-and-the-dom.html)
* [ref 사용주의](https://ko.reactjs.org/docs/refs-and-the-dom.html#when-to-use-refs)

&#x20;\
**DOM 컨트롤**

```jsx
// 일반적인
<input type="text" className="input" />
const inputText = document.querySelector('.input');

// react Ref 사용
// Class
<input ref={this.inputRef} type="text" />
inputRef = React.createRef(); // 멤버변수

// Function
<input ref={inputRef} type="text" />
const inputRef = useRef();
```

