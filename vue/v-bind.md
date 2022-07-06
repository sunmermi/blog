# v-bind

#### 공식 문서 &#x20;

* 스타일 바인딩 : [https://kr.vuejs.org/v2/guide/class-and-style.html#인라인-스타일-바인딩](https://kr.vuejs.org/v2/guide/class-and-style.html#%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EC%8A%A4%ED%83%80%EC%9D%BC-%EB%B0%94%EC%9D%B8%EB%94%A9)&#x20;
* 클래스 바인딩 : [https://kr.vuejs.org/v2/guide/class-and-style.html#HTML-클래스-바인딩하기](https://kr.vuejs.org/v2/guide/class-and-style.html#HTML-%ED%81%B4%EB%9E%98%EC%8A%A4-%EB%B0%94%EC%9D%B8%EB%94%A9%ED%95%98%EA%B8%B0)&#x20;

#### 바인딩 방법 &#x20;

* 기본적으로 [객체](https://kr.vuejs.org/v2/guide/class-and-style.html#%EA%B0%9D%EC%B2%B4-%EA%B5%AC%EB%AC%B8), [배열](https://kr.vuejs.org/v2/guide/class-and-style.html#%EB%B0%B0%EC%97%B4-%EA%B5%AC%EB%AC%B8) 구문&#x20;
* `data(), computed()` 를 활용 할 수 있 &#x20;
* 컴포넌트에 사용자가 또 다시 `class`를 적용하 컴포넌트에 정의된 클래스와 함께 추가됨. [link](https://kr.vuejs.org/v2/guide/class-and-style.html#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8%EC%99%80-%ED%95%A8%EA%BB%98-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)&#x20;

#### 궁금했던 점&#x20;

* `:class`  할 때 객체방식과 배열방식 사용 차이&#x20;

```
// 객체 방식 : 
ass="{'클래스명': '조건'}"
:class="{'클래스명'조건', '클래스명' :'조건'}"
:class="{isAction: isAction}"


// 배열 방식 : 좀더 플렉서블하다 조건 구문 사용 가능
:class="[조건? 'ture일 경우 class name' : 'false일 경우 class name']"
:class="[조건? 'ture' : 'false', 조건? 'ture' : 'false']"
// + 디폴트 클래스네임이 필요한 경
:class="['디폴트클래스네임', 조건? 'ture' : 'false']"
:class="['btn', 조건? 'ture' : 'false' ]"

// 여러개의 조건의 클래스가 있는 경우 배열 구문 내에서 객체 구문을 사용할 수 있다.
:class="[{ active: isActive, disabled: disabled, open: open }, errorClass]

// 스타일 바인
:style="{ 스타일명: 스타일값, 스타일명: 스타일값}"
:style="{ color: activeColor, fontSize: fontSize + 'px' }"
:style="[iconSrc && { backgroundImage: `url(${iconSrc})` }]"
```



#### 추가로 알게된 점

* `:class=""`  와  `class=""` 함께 사용할 수 있다.

```
// 1 예로 Button 컴포넌트 만들때로 가정 
// 데이터를 바인딩 할 수 있는 :class 와 일반 class 를 동시에 작성
<button 
    class="btn_open"
    :class="['btn', size && `${size}`, {round: round, disabled: disabled}]"
>
    버튼
</button>

// 2 사용자가 Button 컴포넌트에 또 다시 클래스를 추가할 경우  
<Button class="new_class">버튼</Button>


// 최종 render 버튼  
<button class="btn_open btn new_class">버튼</button>

```



