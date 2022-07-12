---
description: <a> 요소 사용 할 때 title 속성을 작성 하는 것이 접근성 대응에 필수인가? 좋은건가?
---

# Anchor 요소에서 Title 속성사용이 Accessibility(접근성)에 좋다고?

#### 상황

> `a`요소 `target="_blank"` 일 때는 무조건 `title="새창으로 열림"` 이라고 해줘야 접근성에 안걸려\~ 라고 말하시더라.. 몇년전에 접근성기관에 넘겼을 때 다 걸렸다고 하시면서..&#x20;

저 말을 듣고 흠.. 무조건 이라고?? 🧐 \
나는 최근에 `target="_blank"` 라고 쓴 기억이 없는것 같은데 나 이제까지 잘못한건가?... 싶어서 찾아 보기 시작했다.

#### 결론

a 요소 내부에 텍스트나 대체 텍스트가 명확하게 링크에 대해 표현되고 있지 않다면 넣어 주는 것이 좋다. 하지만 `target="_blank"` 일때는 **무조건** `title="새창으로 열림"`을 해줘야 한다는 말은 **오류다.**

```
// 기본 target="_self"
// 지향
<a href="https://www.유튜브...">
  <span class="hidden">유튜브 보기</span>
</a>
// 지양
<a href="https://www.유튜브..." title="유튜브 보기"></a>

// target="_blank"
// 지향
<a href="https://www.유튜브..." target="_blank">
  <span class="hidden">유튜브 새 창 열림</span>
  보기
</a>
// 지양
<a href="https://www.유튜브..." target="_blank" title="유튜브 새 창 열림">보기</a>
```



몇가지 덧붙이자면&#x20;

[널리 - Title 속성 사용을 지양해야 하는 이유](https://nuli.navercorp.com/community/article/1132934) (터치 기기 대응 안됨, 키보드 탐색 미대응, 스크린리더기 마다 다른 대응, 추측 가능성 등..) 이러한 이유로 인해 `title=""` 사용하기 보다는 대체텍스트를 명확하게 표현해주는 방법이 좋은것 같다.

`a`요소 사용에 있어서 대체 텍스트로 명확하게 표기해주고 있는 [대한항공](https://www.koreanair.com/kr/ko)을 참고 하면 좋을 것 같다.



#### 참고

* [널리-지침 적절한 링크 텍스트](https://nuli.navercorp.com/guideline/s02/g16)&#x20;
* [웹접근성연구소 - 적절한 대체 텍스트 제공](https://www.wah.or.kr:444/Participation/technique.asp)&#x20;
* [하이브랩블로그 - title 속성의 바람직한 사용방법](http://blog.hivelab.co.kr/%EA%B3%B5%EC%9C%A0-title-%EC%86%8D%EC%84%B1%EC%9D%98-%EB%B0%94%EB%9E%8C%EC%A7%81%ED%95%9C-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95/)

