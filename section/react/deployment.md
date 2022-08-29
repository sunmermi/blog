# Deployment

#### create-react-app Deployment

* 온라인강의를 듣다가 배포방법을 알려주길래 정리해봄.. 😊
* [create-react-app/deployment](https://create-react-app.dev/docs/deployment)
* [github-pages](https://create-react-app.dev/docs/deployment/#github-pages)
* [netlify](https://create-react-app.dev/docs/deployment/#netlify)
* aws, 히로쿠, 등등... 여러가지 서비스들이 있다.

&#x20;

#### netlify로 배포방법

* `yarn build`를 한 후 build 디렉토리가 생성된걸 확인!
*   [netlify](https://create-react-app.dev/docs/deployment/#netlify)에 나온 순서대로 진행

    ```shell
    $ npm install netlify-cli -g
    $ netlify deploy
    ```
* 깃허브로 회원가입 > `netlify deploy` 승인
* 터미널에서 > 해당 디렉토리 사이트 연결관련 선택조항이 있음 > 기존에 있는 링크로 연결할지, 새로운 사이트로 만들지 방향키로 선택 (새로운거\~)
* 팀이름 (회원가입시 정한 팀 이름)
* 사이트 이름을 지정
* 퍼블리시 디렉토리 > `build`
*   배포하면 검증용 유알엘이 만들어짐 `Website Draft URL: https://.....netlify.app` 이런식..\
    보통 개발후 디벨롭 혹은 스테이징 환경에서 이슈가 없는지 확인후 배포하는데\
    여기서는 `Website Draft URL` 에서 확인하고 아래 나온 문구처럼 이슈가 없으면\
    `netlify deploy --prod` 명렁어를 통해 최종 배포를 한다.

    > If everything looks good on your draft URL, deploy it to your main site URL with the --prod flag.\
    > netlify deploy --prod
* 완료되면 `Website URL: https://사이트이름.netlify.app` 최종 유알엘이 나옴 👏👏👏

&#x20;&#x20;

#### ✍️ 강의 따라 테스트 해본 것

* https://sunmermi-habits.netlify.app

&#x20;
