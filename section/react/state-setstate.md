# state, setState

#### state

* 컴포넌트에서 본인이 가지고 있는 데이터
* 상태가 변경되면 `render()` 함수가 재실행된다.
* 주의사항
  * 상태 데이터를 직접 수정하면 좋지 않다.\
    (비동기적으로 동작하기 때문에 예상치 못 한 이슈 존재하고, PureComponent에서 정상적으로 동작 하지 않는다.)
  * 데이터 변경이 필요한 경우는 새로운 state 객체를 만들어서 수정하는 것이 좋다. (아래 코드 참고)

```jsx
// 예제로 카운드 증가
export default class CountComponent extends Component {
  state = {
    data: [
      { id: 0, count: 0 },
      { id: 1, count: 0 },
      { id: 2, count: 0 },
    ],
  };

  // as-is : 직접 수정 No 
  handleIncrement = (data) => {
    data.count++;
    this.setState(this.state);
  };

  // to-be
  handleIncrement = (data) => {
    // 새로운 배열을 만들고 Spread Syntax를 이용해서 this.state를 복사
    const localNewArray = [...this.state.data]; 

    // 인자로 전달된 data가 localNewArr에서 몇번째 인덱스 일까? 
    const index = localNewArray.indexOf(data);

    // 로컬 배열 인덱스에 해당하는 카운트를 증가
    localNewArray[index].count++;

    // 새로운 상태 오브젝트를 넣어줌.
    this.setState({data: localNewArray});
  };
  ...
}
```

&#x20;

**setState()**

* [reactjs - setState()](https://ko.reactjs.org/docs/react-component.html#setstate)
* `state` 를 변경할 때 `setState()` 함수를 사용해서 변경해야 한다.
* `setState()` 함수가 호출이 되면 리액트는 `this.state` 현재 상태와,\
  `setState(새로 업데이트되는 상태)` 함수의 인자로 전달된 새로운 오브젝트를 비교해서 업데이트가 필요한 경우 해당 컴포넌트의 `render()`를 호출해서 UI를 다시 그린다.



