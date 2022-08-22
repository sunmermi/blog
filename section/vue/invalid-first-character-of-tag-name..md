---
description: 'Parsing error: invalid-first-character-of-tag-name.'
---

# invalid-first-character-of-tag-name.

#### 상황

> 에러코드 - vue Parsing error: invalid-first-character-of-tag-name.

작업을 하는 도중 `{{ count < 0 ? 0 : count }}` 코드에서 위와 같은 에러가 떴다.\
검색을 해보니 관계연산자(`<`) 에러였다.

`html` 작업시 `<` 는 태그를 작성할때 여는 문법으로 사용되기 때문에 그걸로 인식 하면서 생긴 오류인 것 같다.

&#x20;

#### 해결 방안

뚜렷한 방안이 있는것 같지 않은 느낌인데...

2가지의 방법은..

1. 린트 수정한다.
2. `{{ 0 > count ? 0 : count }}` 와 같이 부호를 `<` 대신 `>` 를 사용한다. (빨간줄이 뜨지만 에러는 나지 않고 빌드가 잘 되었다.)

&#x20;

#### 참고

* [구글 검색](https://www.google.com/search?q=vue+Parsing+error%3A+invalid-first-character-of-tag-name.\&newwindow=1\&sxsrf=ALiCzsb8HYgylsI3qxgLK\_c0PE3yzG8O3g%3A1660208264042\&ei=iMT0Yt\_9AfrN2roP7f-N0AM\&ved=0ahUKEwjf4dLetb75AhX6plYBHe1\_AzoQ4dUDCA4\&uact=5\&oq=vue+Parsing+error%3A+invalid-first-character-of-tag-name.\&gs\_lcp=Cgdnd3Mtd2l6EAMyBAgAEB4yBggAEB4QCDoHCAAQRxCwA0oECEEYAEoECEYYAFD7CVj7CWCrDmgCcAF4AIABeIgBeJIBAzAuMZgBAKABAqABAcgBCsABAQ\&sclient=gws-wiz)
* [vuejs/eslint-plugin-vue/issues...](https://github.com/vuejs/eslint-plugin-vue/issues/370) &#x20;

