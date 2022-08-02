# word-wrap VS overflow-wrap 그리고 word-break

#### 상황

줄바꿈 설정 할 때\
`word-wrap: break-word` 만 쓸 줄 알았지\
`overflow-wrap` 는 첨봤네,, 이미 나온지 좀된 것 같은데,, 무지했군 😭\
그러면서 알아보았다.

&#x20;

#### word-wrap VS overflow-wrap

* 둘 다 같은 역할을 한다. 부모 박스에서 문자열이 넘치면 줄바꿈의 여부를 판단한다.
* `word-wrap: break-word;` 과 `overflow-wrap: break-word;`는 동의어랜다.

&#x20;

#### word-break

* 텍스트를 공백/띄어쓰기 아니면 음절 중 어떤 기준으로 분리해서 줄바꿈에 관여할지 결정한다.
* [참고 👍 포스팅](https://wit.nts-corp.com/2017/07/25/4675)
* [MDN word-break](https://developer.mozilla.org/ko/docs/Web/CSS/word-break)
* `word-break: break-word;` 는 더이상 사용되지 않음으로 `overflow-wrap: break-word;` 를 사용한다.

&#x20;

#### word-wrap

* 텍스트가 박스 가로 영역을 넘칠때 줄바꿈의 유무를 결정한다.
* [참고 👍 포스팅](https://wit.nts-corp.com/2017/07/25/4675)
* [MDN 문서도 없다. word-wrap과 관련하여 overflow-wrap에서 아래와 같이 이야기 한다.](https://developer.mozilla.org/ko/docs/Web/CSS/overflow-wrap)

> 이 속성은 처음에 마이크로소프트에서 표준이 아니고 접두어가 없는 word-wrap으로 나왔고, 대부분 브라우저에서 똑같은 이름으로 구현되었습니다. 요즘은 overflow-wrap으로 다시 지어지고, word-wrap은 동의어가 되었습니다.

&#x20;

#### overflow-wrap: break-word;

* 텍스트가 박스 가로 영역을 넘칠때 줄바꿈의 유무를 결정한다.
* [overflow-wrap](https://developer.mozilla.org/ko/docs/Web/CSS/overflow-wrap)
* 주로 띄어쓰기 공백 등이 없는 텍스트 (예: asdsdsdsadsadsadsdsadadsa, 123232321312, ########## ) `overflow-wrap: break-word;` 를 사용한다.

&#x20;

#### 결론

```html
// 음절
한·글·좋·아·요 // 한글 기본
h·e·l·l·o·s·u·m·m·e·r

// 공백
한글·좋아요
hello·summer // 영문 기본
```

&#x20;\
텍스트를 쪼갤때\
**한글은 (중국어 일본어)**

* 기본이 음절 쪼갬
* 음절로 쪼개기 때문에 박스 넘침 없음
* 공백 단위로 쪼갤거 아니면 `word-break: keep-all`을 사용할 일이 없다.

&#x20;\
**영문은 그리고 그외 언어들**

* 기본이 공백 쪼갬
* 공백이 없으면 박스 넘침
* 단어를 음절마다 쪼갤거 아니면 `word-break: break-all`을 사용할 일이 없다.

&#x20;\
**박스넘침**

* 한글은 박스넘침 없음
* 하지만!! 공백없는 영문, 숫자, 특수문자 등은 박스 넘침
* 이때는 `overflow-wrap: break-word;` 를 사용한다.

&#x20;

#### 참고 할 만안 블로그 포스팅

* [word-break 속성과 word-wrap 속성 알아보기](https://wit.nts-corp.com/2017/07/25/4675)
* [word-break / overflow-wrap(=word-wrap)](https://mill-study.tistory.com/329)
* [overflow-wrap 긴 단어 처리 방법](https://velog.io/@leyuri/CSS-overflow-wrap-%EA%B8%B4-%EB%8B%A8%EC%96%B4-%EC%B2%98%EB%A6%AC-%EB%B0%A9%EB%B2%95)
