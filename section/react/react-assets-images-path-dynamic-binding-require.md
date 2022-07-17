---
description: 컴포넌트에서`src/assets/...` 디렉토리 내부 이미지소스 적용시 동적 바인딩 관련
---

# react assets images path dynamic binding - require()

#### 상황

[Vue - assets images path dynamic binding](../vue/vue-assets-images-path-dynamic-binding-require.md) 의 연장선으로 작성하게 되었다.

위 내용은 버튼 컴포넌트에서 아이콘 타입 디자인을 작업 하다가 생긴 이슈였다.\
아이콘 이미지 소스가 정리가 되어있거나 정리할 상황도 아니였고 언제 추가되고 뭐가 삭제되고 할지 모르는 상황이라\
아이콘 이미지를 아예 `<i style=".."></i>` 인라인 스타일로 박아 버리기로 했고 그것과 관련해서 assets 이미지 경로 때문에 생긴 이슈를 다뤘다.

&#x20;

#### 리액트에서는?

이전에 리액트를 작업하면서 버튼 컴포넌트 작업을 할때는 CSS-in-JS styled-components를 사용해 왔어서\
컴포넌트에서 prop 으로 받아서 위에 Vue 에서 인라인스타일로 박을 필요없이 스타일로 제어를 하면 됐었다.

외부에 이미지 서버가 따로 있다면 이미지 경로를 그냥 넣으면 되는데\
`src/assets` 디렉토리에 있는 정적인 소스를 동적으로 불러오려면 뷰에서와 마찬가지로\
사용되 이미지 각각을 `import ... from ...;` 을 하던가 `require()` 를 사용해야 한다.

&#x20;

#### 테스트 해본 예제 코드 1 - 컴포넌트 사용시 `iconSrc`에 값을 넣을때 `require()` 사용.

```tsx
import React, {ReactElement} from 'react';
import styled, {css} from 'styled-components';
...

interface Props {
  ...
  iconSrc?: string;
}

const ButtonEl = styled.button<Props>`
  ...
  ${({iconSrc}) => iconSrc &&
    css`
      i {
        ...
        background: url(${iconSrc}) no-repeat 0 0 / contain;
      }
    `}
  ...
`;

export const Button = ({
  iconSrc,
  ...props
}: Props): ReactElement => {
  ...
  return (
    <ButtonEl
      iconSrc={iconSrc}
      {...props}
    >
      {iconSrc && <i></i>}
      {children}
    </ButtonEl>
  );
};

// 사용
<Button iconSrc={require('./assets/이미지경로.png')}>Icon Button</Button>
<Button iconSrc='https://이미지경로.png'>Icon Button</Button>
```

&#x20;

#### 테스트 해본 예제 코드 2 - 버튼 컴포넌트 내부에서 `iconSrc`에 값을 받아서 `require()` 처리

```tsx
import React, {ReactElement} from 'react';
import styled, {css} from 'styled-components';
...

interface Props {
  ...
  iconSrc?: string;
}

const ButtonEl = styled.button<Props>`
  ...
  ${({iconSrc}) => iconSrc &&
    css`
      i {
        ...
        background: url(${
          iconSrc?.startsWith('http') 
            ? iconSrc 
            : require(`./assets/${iconSrc}`
          )}) no-repeat 0 0 / contain;
      }
    `}
  ...
`;

export const Button = ({
  iconSrc,
  ...props
}: Props): ReactElement => {
  ...
  return (
    <ButtonEl
      iconSrc={iconSrc}
      {...props}
    >
      {iconSrc && <i></i>}
      {children}
    </ButtonEl>
  );
};

// 사용
<Button>Button</Button>
<Button iconSrc='이미지경로.png'>Icon Button</Button>
<Button iconSrc='https://이미지경로.png'>Icon Button</Button>
```

&#x20;

#### 두가지 경우를 해본 이유

처음에 1번과 같이 작업했다가, 버튼 만들때마다 저렇게 넣어줘야할까? 버튼컴포넌트에서 작업되면 어떠나 싶어서 테스트 해본거다.\
플젝 내부 구성이 어떻게 되는지에 따라 알잘딱깔센?이랄까..😊

&#x20;

#### 참고

* [Create-react-app 프로젝트에서 이미지 경로를 설정하는 4가지 방법](https://velog.io/@rimo09/React-Create-react-app-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90%EC%84%9C-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EA%B2%BD%EB%A1%9C%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-4%EA%B0%80%EC%A7%80-%EB%B0%A9%EB%B2%95)
* [React Img src 방법](https://www.delftstack.com/ko/howto/react/react-img-src/)
* [MDN startsWith()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global\_Objects/String/startsWith)
