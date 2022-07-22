# 후속편(after that...)

#### 상황

다이나믹 컴포넌트의 예시를 버튼컴포넌트로 들었는데, (뭐 실제로 그렇게 사용하려고 했었고,,)\
추가적으로 작업하다보니 버튼(`button`)과 링크(`router-link`)를 겸용으로 쓸 수 없겠다 라고 판단 해버린 상황이 왔다.

&#x20;&#x20;

예를 들어, 링크 역활을 하는 요소가 어떠한 액션으로 인해 이벤트 적용이 되야 한다고 치면\
`button`은 `@이벤트=""` 이렇게 주면 되지만\
`router-link`는 `@이벤트.native=""` 해야한다.\
그래서 아래와 같은 코드가 만들어진다. :disappointed\_relieved:

```
<component
    :is="href ? 'router-link' : 'button'"
    ...
    @mouseover="isHover = true"
    @mouseout="isHover = false"
    @mouseover.native="isHover = true"
    @mouseout.native="isHover = false"
> ... </component>
```

&#x20;&#x20;

이건 아니다 싶었고 그냥 버튼디자인으로 생겨먹은 링크는 버튼 컴포넌트를 활용하되\
`role="link"` 을 주도록 하고 라우터는 `@click="..."`을 사용하는 방향으로 노선을 변경했다.

&#x20;

#### 개선된 코드 방향

```
<button
    type="button"
    ...
    @mouseover="isHover = true"
    @mouseout="isHover = false"
> ... </button>


// 컴포넌트 사용시
<Button role="link" @click="$router.push(`/project/link`)">
  링크버튼
</Button>
```
