# some() VS every()

* 조건을 만족하는지 배열 내부를 순회하면서 검사한다.
* 조건에 맞으면 그 즉시 Boolean 값을 반환한다. (조건에 맞으면 순회중에 값을 반환하고 종료.)

&#x20;

#### every()

* 배열 안의 모든 요소가 조건에 만족해야 True 반환
* [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/every)

```js
[12, 5, 8, 130, 44].every(elem => elem >= 10); // false
[12, 54, 18, 130, 44].every(elem => elem >= 10); // true
```

&#x20;

#### some()

* 배열 안의 요소들이 조건에 단 한 개라도 맞으면 True 반환
* [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/some)

```js
[2, 5, 8, 1, 4].some((x) => x > 10);  // false
[12, 5, 8, 1, 4].some((x) => x > 10); // true
```
