# try...catch...finally and throw

#### 예외 처리

* `try...catch...finally` 문은 자바스크립트의 예외 처리 기법이다.
* `throw` 연산자는 예외상황(에러)를 발생시킨다.(예외를 강제로 발생시켜야 경우)

```js
try {
  // 실행될 선언들
} catch (err) {
  // try 블록에서 예외가 발생했을 때 실행될 선언들
} finally {
  // try 선언이 완료된 이후에 실행된 선언들. 이 선언들은 예외 발생 여부와 상관없이 실행된다.
}
```

&#x20;

#### async & await + 예외 처리

```js
export default Vue.extend({
  ...
  methods: {
    async onClickCreate() {
      this.isLoading = true;
      const data = {
        title: this.title,
        ...
      };

      try {
        if (!this.title) {
          throw Error("필수 항목입니다.");
        }

        const response = await api.post('..api url..', data);
        if (response.status === 200) {
          console.log("Success");
        } else {
          console.log(response.status);
          CommonUIControl.ShowErrorToast(response.status);
        }
      } catch (error) {
        console.log(error);
      } finally {
        console.log('finally');
      }
    },
  }
  ...
});
```

&#x20;

#### 참고

* [MDN - try...catch...finally](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/try...catch)
* [MDN - throw](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/throw)
* [모던 JavaScript 튜토리얼 - try-catch](https://ko.javascript.info/try-catch)
* [try/catch/finall - 자세하게 설명이 되어진 블러그 포스팅](https://webclub.tistory.com/71)
* [모던 JavaScript 튜토리얼 - async-await](https://ko.javascript.info/async-await)
* [async/await - 자세하게 설명이 되어진 블러그 포스팅](https://joshua1988.github.io/web-development/javascript/js-async-await/)

&#x20;

#### ✍️ 끄적끄적

오늘은 일을 하다가 프론트 개발자 분이

> 이거 한번 다른 코드 참고해서 api 다루는 부분 개선 해볼래? 라고 하셨다.

항상 그렇듯이 시키면 하는 나는요 ㅋㅋ

> 네!!

사실 말이 참고지 그냥 복붙..하는 수준으로 이건 모지 이건 몰까? 하면서 검색도 해보면서 작업을 해보았다. 고대로 복붙하는 수준이였는데 그래도 오류가 있긴하네..😂\
검색해봐도 이해 안된는건 개발자분한테 물어봤고.. 사실 100% 이해는 못했지만 난 언제나 그렇듯 자주 보다보면 알겠지 하고 이 정도에서 아하!💡 하고.. 넘어간다.\
오늘도 즐거운 하루였다.\
(Promise, 비동기, 동기 도 다 연관된거라 다 자세히 봐야겠지만 오늘은 일단 넘어가고 나중으로...)
