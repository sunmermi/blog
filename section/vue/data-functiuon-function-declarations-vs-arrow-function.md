# data functiuon - Function Declarations VS Arrow Function

#### 상황

리팩토링 작업을 하던중에 아래 코드와 같이\
같은 `data` 함수인데 어떤 코드엔 ES5 어떤건 ES6 문법인 arrow function으로 작성되어 있었다.\
무슨 차이일까 싶어서 찾아 보았다.

```js
//ES5 문법
export default {
   data (){
      return {
         isShow: false,
      }
   }
}
 

//ES6 문법
export default {
   data: () => ({
      return {
         isShow: false,
      }
   })
}
```

&#x20;

#### 결론

뷰 코드에서\
`props`로 받은 데이터를 사용하려면 화살표함수로 만든 `data: () => {}`는 사용하지 못한다. 이유는 `this`가 vue Instance 이기 때문!!!

`data () => {}` 일반 함수는 `this`는 내부에서 부터 값을 찾아내기 때문에 사용이 가능하다.

```js
export default {
   props: {
      isOpen: {
         type: Boolean,
         default: false,
      },
   },
   data: () => ({
      return {
         isShow: this.isOpen,
      }
   })
}

export default {
   props: {
      isOpen: {
         type: Boolean,
         default: false,
      },
   },
   data (){
      return {
         isShow: this.isOpen,
      }
   }
}
```

&#x20;

#### 참고

* [Vue.js data () { return { } } VS data:() => ({ }), 어떤게 더 좋을까?](https://hj-tilblog.tistory.com/78)
* [Vue JS: Difference of data() { return {} } vs data:() => ({ })](https://stackoverflow.com/questions/48980865/vue-js-difference-of-data-return-vs-data)
* [VueJS에서 Arrow Function이 필요한 이유 \[맨땅에VueJS\]](https://medium.com/@hozacho/vuejs%EC%97%90%EC%84%9C-arrow-function%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EC%95%BC%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0-ec067c342412)
* [함수 선언 참고](https://joshua1988.github.io/web-development/javascript/function-expressions-vs-declarations/)
