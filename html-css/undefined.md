---
description: 모바일에서 보장해야 하는 최소 터치 영역
---

# 모바일 최소 터치 영역

#### 설명

유저 사용성을 위해서는 최소 터치영역이 보장이 되어야하는데 간혹 모바일을 보다보면 최소 터치영역을 대응하지 않아서 터치(클릭)하기가 어려울 때가 있다.

모바일은 최소 터치 영역을 보장해 줘야 좋은 사용성을 가지지만\
피씨의 경우는 마우스로 컨트롤 하기 때문에 최소 클릭 영역을 보장 해줘야 한다는 말은 없는 것 같다.

하지만 내 생각엔 피씨여도 클릭 영역이 최소 높이가 14\~18px은 돼야 하지 않을까 싶다. 그래서 항상 작업시 나만의 기준을 가지고 작업을 진행 진행한다.

#### 터치영역에 대한 연구 및 지침

**연구에 따르면**

* 손가락을 사용한 효율적이고 정확한 상호 작용을 위한 최소 대상 영역은 6x6mm(약 23픽셀).
* 사용자들은 크기가 10x10mm(약 38픽셀)이면 속도와 정확도가 향상되고 사용자에게 더 편안하게 느낌.

**지침**

* Apple의 iPhone 휴먼 인터페이스 지침에서는 최소 대상 크기를 44x44픽셀로 권장합니다.
* Microsoft의 Windows Phone UI 디자인 및 상호 작용 가이드에서는 최소 터치 대상 크기가 26px인 터치 대상 크기를 34px로 제안합니다.
* Nokia의 개발자 지침에 따르면 대상 크기는 1x1cm 정사각형 또는 28x28픽셀 이상이어야 합니다.

#### 최종 모바일 터치 영역 가이드

마크업 작업을 하면서 디자인 시안에도 협의가 가능했던 있었던 터치영역 크기는 아래와 같이 진행 해왔다.

* 최소 영역 크기 : 23x23픽셀, 26x26픽셀 (엄지 터치)
* 기본 영역 크기 : 30x30픽셀, 40x40픽셀, 44x44픽셀
* 각 터치영역 요소 사이 여백은 최소 4픽셀 기본은 8픽셀

#### 참고

* [microsoft > control-sizes-and-touch](https://docs.microsoft.com/ko-kr/windows/win32/uxguide/inter-touch#control-sizes-and-touch-targeting)
* [Finger-Friendly Design: Ideal Mobile Touchscreen Target Sizes](https://www.smashingmagazine.com/2012/02/finger-friendly-design-ideal-mobile-touchscreen-target-sizes/)
* [모바일 UI 디자인 기본 요소 - 버튼](https://brunch.co.kr/@chulhochoiucj0/23)



