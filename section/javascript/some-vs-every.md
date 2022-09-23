# 배열처리 some() VS every()

#### some() VS every()

* 조건을 만족하는지 배열 내부를 순회하면서 검사한다.
* 조건에 맞으면 그 즉시 Boolean 값을 반환한다. (조건에 맞으면 순회중에 값을 반환하고 종료.)

&#x20;

#### every()

* 배열 안의 모든 요소가 조건에 모두 만족해야 True 반환
* [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/every)

```js
[12, 5, 8, 130, 44].every(elem => elem >= 10); // false
[12, 54, 18, 130, 44].every(elem => elem >= 10); // true
```

&#x20;

#### some()

* 배열 안의 어떤 요소라도 조건에 한개라도 맞으면 True 반환
* [MDN](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array/some)

```js
[2, 5, 8, 1, 4].some((x) => x > 10);  // false
[12, 5, 8, 1, 4].some((x) => x > 10); // true
```

&#x20;

#### 참고

* [MDN Array Methods](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/Array)
* Arr.map() : 콜백함수가 실행되고 새로운 배열 반환
* Arr.filter() : 콜백함수가 실행되고 그 조건에 맞는 요소만 새로운 배열로 반환
* Arr.reduce() : 콜백함수가 실행되고 그 누적계산값 반환
* Arr.includes() : 특정 요소를 포함하고 있는지 확인후 Boolean 값 반환
* Arr.concat() : 배열 + 인자로 전달된 배열과 합쳐서 새별열 반환
* Arr.find() : 콜백함수를 실행하고 요소에서 조건에 맞는 첫 번째 요소 값을 반환
* Arr.findIndex() : 콜백함수를 실행하고 요소에서 조건에 맞는 첫 번째 요소의 인덱스 값을 반환
* Arr.indexOf() : 인자로 전달된 값과 동일한 첫번째 요소의 인덱스를 반환하고 존재하지 않으면 -1을 반환
* Arr.join() : 배열의 모든 요소를 전달된 인자로 연결해서 하나의 문자열로 반환
* Arr.pop() : 배열에서 마지막 요소를 제거하고 변경된 요소를 반환
* Arr.push() : 배열의 끝에 전달된 인자값을 추가하고, 변경된 배열을 반환
* Arr.splice() : 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 변경된 배열 반환
* Arr.slice() : 배열의 시작, 끝을 인자로 (음수,정수) 전달하여 그에 맞는 요소들을 추출해 새로운 배열로 반환
* Arr.sort() : 배열의 요소를 정렬한 후 그 배열을 반환 (정렬 순서는 문자열의 유니코드 코드 포인트)
* ... 등등
