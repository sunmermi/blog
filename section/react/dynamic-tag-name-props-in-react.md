---
description: Dynamic Tag Name Props in React
---

# Dynamic Tag Name Props in React

#### 상황

[Vue > Dynamic Components](https://app.gitbook.com/s/DPKt0tyjAJEzGVm6AJue/\~/changes/9ZqzoNhp827M1R8hnw4Q/vue/dynamic-components-is-attribute) 의 연장선으로 작성하게 되었다.

위에 내요은 뷰에서 한개의 컴포넌트로 조건에 따라 렌더링 되는 태그를 변경하고 싶었다.

이전에 리액트에서 작업할 때는 `styled-components` 사용을 하고 있었기 때문에 `styled-components` 제공하는 `as` 프롭을 사용해서 쉽게 렌더링 태그를 변경할 수 있었다.

하지만 `styled-components` 않는다면? 어떻게 해야하나? 궁금증이 생겼다.

#### `styled-components` 사용시

아래와 같이 `as` 를 사용하면 된다.

```tsx
// button 컴포넌트
<button 
  as={href && 'a'}
  className={ href ? 'link' : 'button'}
  {...props}
> {children} </button>

// 사용시
<Button as="a" href="/">a 태그로 렌더링</Button> 
<Button>button 태그로 렌더링</Button> 
```

####

#### React 사용으로만

구글링을 했을땐 제일 많이 나오는 방법은 [이 방법](https://blog.hackages.io/conditionally-wrap-an-element-in-react-a8b9a47fab2)이였고

내가 원하는 방법은 [Dynamic Tag Name Props in React (with TypeScript)](https://www.aleksandrhovhannisyan.com/blog/dynamic-tag-name-props-in-react/) 이거다.

위 방법을 참고해서 만든 [코드](https://codesandbox.io/s/react-dynamic-tag-render-hjtvb9)

**1. DynamicTag 컴포넌트 만들기**

```tsx
interface Props
  extends React.AllHTMLAttributes<any>,
    PropsWithChildren<unknown> {
  children?: React.ReactNode;
  className?: string;
  tagName?: React.ElementType<any>;
}

export const DynamicTag = ({
  children,
  tagName: Tag = "div",
  className,
  ...props
}: Props): ReactElement => {
  return (
    <Tag className={className} {...props}>
      {children}
    </Tag>
  );
};
```

**2. DynamicTag 컴포넌트를 사용해서 Button 만들기**

```tsx
import { DynamicTag } from "./dynamicTag";

interface Props extends PropsWithChildren<unknown> {
  className?: string;
  href?: string | undefined;
}

export const Button = ({
  children,
  href,
  className,
  ...props
}: Props): ReactElement => {
  return (
    <DynamicTag
      tagName={href ? "a" : "button"}
      className={className}
      href={href}
      {...props}
    >
      {children}
    </DynamicTag>
  );
};
```

**3. DynamicTag, Button 컴포넌트 사용하기**

```tsx
// DynamicTag 컴포넌트
<DynamicTag tagName="a" href="/">
  a 로 렌더링
</DynamicTag>
<DynamicTag tagName="p"> p 로 렌더링 </DynamicTag>
<DynamicTag> div 로 렌더링 </DynamicTag>

// Button 컴포넌트
<Button href="/">a 렌더링</Button>
<Button>button 렌더링</Button>
```

####

#### 더 연구해 볼 것

사실 위와 같은 방법이 올바른 방법인지는 모르겠다. 참고해서 작업하긴 했지만 오류에 계속 직면했다.

예를 들면 `DynamicTag` 컴포넌트에서 `...props` 를 전달하였음에도 `href` 속성값을 넣으면 `ts` 오류가 떴다. 다른 속성값도 마찬가지로 오류가 뜸.

구글링을 해보고 이리저리 껴 맞춰보고 해서 오류는 안뜨게 했는데 논리적으로 왜 저렇게 해야하는 건지 사실 방법은 잘 모른다. ㅠㅠ

`React.AllHTMLAttributes` 흠..

```tsx
// DynamicTag 에서 Props
interface Props extends React.AllHTMLAttributes<any> {
  children?: React.ReactNode;
  className?: string;
  tagName?: React.ElementType<any>;
}

// 사용시
<DynamicTag tagName="a" href="/">
  a 로 렌더링
</DynamicTag>
```

####

#### 참고

* [Dynamic Tag Name Props in React (with TypeScript)](https://www.aleksandrhovhannisyan.com/blog/dynamic-tag-name-props-in-react/)
* [How to conditionally wrap an element in React](https://blog.hackages.io/conditionally-wrap-an-element-in-react-a8b9a47fab2)
* [Writing Type-Safe Polymorphic React Components (Without Crashing TypeScript)](https://blog.andrewbran.ch/polymorphic-react-components/)
* [babel-plugin-react-html-attrs](https://github.com/DefinitelyTyped/DefinitelyTyped/blob/78120d1d515a1cd7bcd3145424b1a17be15310a9/types/babel-plugin-react-html-attrs/index.d.ts#L1742)
* [AllHTMLAttributes](https://www.programcreek.com/typescript/?api=react.AllHTMLAttributes)
