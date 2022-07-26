# Object Type Spread Syntax

#### object 할당 + spread

```js
const countNumber = 1; // 1 이 할당
const arrayData = [ // 주소값(참조값) 할당 (예. 123)
  { id: 0, count: 0 }, // 주소값 할당 (예. 111)
  { id: 1, count: 0 }, // 주소값 할당 (예. 222)
  { id: 2, count: 0 }, // 주소값 할당 (예. 333) 
]
```

`arrayData` 데이터에는 총 4개의 참조값이 생김

&#x20;\
**arrayData를 다른 변수에 할당하면**

* arrayData의 주소값인 (예. 123)을 참조한다.

```js
const arrayDataCopy = arrayData;
```

&#x20;\
**arrayData를 다른 변수에 spread 하면**

* [MDN - spread](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread\_syntax)
* `arrayDataSpread`에 새로운 주소값이 생성되고
* 내부의 데이터는 `arrayData > 내부데이터` 의 값이 그대로 복사된다.
* 새로운 `arrayDataSpread`의 내부 데이터의 참조값은 `arrayData > 내부데이터`는 동일함.
* 즉, 껍데기만 새로운 것.

```js
const arrayDataSpread = {...arrayData};

const arrayDataSpread = [ // 새로운 주소값(참조값) 할당 (예. 456)
  { id: 0, count: 0 }, // 참조값 (예. 111)
  { id: 1, count: 0 }, // 참조값 (예. 222)
  { id: 2, count: 0 }, // 참조값 (예. 333) 
]
```
