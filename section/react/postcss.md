# PostCSS

#### 공식문서 링크 &#x20;

* [PostCSS](https://postcss.org/)
* [PostCSS Plugins](https://www.postcss.parts/)
* [PostCSS Github](https://github.com/postcss/postcss/blob/master/docs/plugins.md)

&#x20;

#### CSS 전처리기

* 순수한 CSS 가 아니고
* Sass, Lass 제공하는 문법에 맞춰 작성하면 컴파일러를 통해 순수 css로 변환해준다.
* 순수 CSS로 처리하지 못하는 중복되는 스타일, 조건문, 반복문, 변수 선언 믹스인 함수등을 사용하여 스타일을 적용할 수 있다.
* 스타일을 모듈화 하여 관리할 수 있다.

&#x20;

#### Sass, Lass VS PostCSS

* `Sass, Lass`는 제공되는 것만 사용가능
* `PostCSS`는
  * 다양한 플러그인이 존재
  * 필요한 것만 다운받아 사용
  * `npm` 에서 다운로드 수가 높고 선호도가 계속 올라가고 있다. Create React App 으로 초기 셋팅을 하면 기본적으로 설치되어 있을 정도로 많은 사람들이 사용하고 있다는 걸 알 수 있다.

&#x20;

#### PostCSS 간단한 예제

* 각각 다른 버튼1, 버튼2라는 컴포넌트에서 `.button` 라는 같은 클래스 네임으로 스타일을 적용 했을 때 CSS 캐스캐이딩 때문에 뒤에 선언되어진 클래스가 적용되는데 아래 예제에서는 버튼1, 버튼2 모두 배경색은 오렌지가 되어있다.

```css
// button1.css
.button {
  background-color: orange;
}

// button2.css
.button {
  background-color: green;
}
```

```jsx
// button1.jsx
@import "button1.css";

class Button1 extends Component {
  render(){
    return {
      <button className="button">button1</button>
    }
  }
}

// button2.jsx
...

// app.jsx
class App extends Component {
  render(){
    return {
      <>
        <Button2 />
        <Button1 />
      </>
    }
  }
}
```

&#x20;\
**PostCSS 사용방법**

* 기존 `파일명.css` 파일을 `파일명.module.css` 변경

```css
// button1.module.css
.button {
  background-color: orange;
}

// button2.module.css
.button {
  background-color: green;
}
```

&#x20;

* 리액트 `jsx` 파일에서는 스타일 파일을 `styles` 이름으로 임폴트하고 클래스네임에는 문자열이 아니고 제공하는 임폴트한 `styles.안에있는스타일네임` 코드로 연결한다.

```jsx
// button1.jsx
@import styles from "button1.module.css";

class Button1 extends Component {
  render(){
    return {
      <button className={styles.button}>button1</button>
    }
  }
}

// button2.jsx
@import styles from "button2.module.css";

class Button2 extends Component {
  render(){
    return {
      <button className={styles.button}>button2</button>
    }
  }
}

// app.jsx
class App extends Component {
  render(){
    return {
      <>
        <Button2 />
        <Button1 />
      </>
    }
  }
}
```

이제 원하는 대로 버튼1은 오렌지, 버튼2는 그린으로 배경컬러가 보여질 것이다.

&#x20;

#### ✍️ 끄적끄적

리액트에서 작업할 때 `autoprefixer`가 `PostCSS`로 인해서 되는지는 몰랐다. 그냥 리액트는 자동으로 되는 건줄 알았다는,,😅
