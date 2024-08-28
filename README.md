# ⛄ 202230133 정지호

## 8월 28일 강의

### npm vs yarn
* yarn 설치: ```$ npm i -g yarn```
* yarn 확인: ```$ yarn -v```
* yarn 삭제: ```$ npm uni -g yarn```

### Pages Router vs App Router
* React로 개발하다 처음 Next를 사용하면 제일 먼저 놀라는 기능.
* Next.js **13.4**에서부터 **App Router**가 **stable**하게 지원하기 시작.
### [ Pages Router ]
* **pages 디렉토리**가 **root**이고, **index.js**가 **index page**가 됨.
* about.js는 /about, team.js는 /team 경로로 라우팅
* **클라이언트 중심**의 라우팅입니다.
### [ App Router ] => 강의 진행
* **app 디렉토리**가 **root**이고,  **page.js**가 **index page**가 됨.
* /about/page.js는 /about, /login/page.js는 /page 경로로 라우팅.
* **서버 중심**의 라우팅입니다.
* 번들 사이즈가 작음.

### Next.js 13 vs 14
* Pages Router -> App Router
* Date Fetching: 13까지는 getServerSideProps, getStaticProps 메소드를 이용해 구현했으나, 
14에서는 SSG(정적 사이트 생성), SSR(서버 측 렌더링) 및 ISR(증분적 정적 재생성)에서 **하나의 API**만을 사용해 구현할 수 있게됨.
* **이미지 최적화**: 13까지는 **도구**를 사용했으나, 14부터는 **자체적**으로 지원하기 시작
* **보안 강화**: XSS 공격에 대한 보호 기능이 강화되고, 보안 관련 헤더 설정을 더욱 쉽게 만듦.

### Ch01. Next.js 알아보기
* Next.js는 리액트를 위해 만든 오픈소스 **자바스크립트 웹 프레임워트**
* 리액트에는 없는 **다양한 기능 제공**
    - 서버 사이드 렌더링(SSR: Server Side Rendering)
    - 정적 사이트 생성(SSG: Static Site Generation)
    - 증분 정적 재생성(ISR: Incremental Static Regeneration)
```html
SSG(정적 페이지 생성) 미리 만들어 놓은 페이지를 서비스 하기에 속도는 빠르나,
한 번 생성 후엔 수정이 불가능.
이러한 단점을 보완하고자 나온 것이 ISR(증분 정적 재생성).
이미 생성된 페이지를 일정 시간이 지난 후에 다시 생성.(최신 데이터로 업데이트)
```

#### [CH01의 주요 내용]
* Next.js.소개 / 다른 프레임워크와의 비교 / 리액트와의 차이점
* 기본 구조 타입 스크립트를 사용하는 방법
* 바벨과 웹팩 설정 커스터 마이징 ( Next.js 14는 Webpack에서 Tubopack으로 바뀜)

### 1.1 준비하기
* Node.js와 npm을 설치하거나, codesandbox.io 혹은 repl.it 등의 사이트를 이용.
<br>
**잠시 확인을 위한 것이면 사이트 이용도 괜찮으나, 그렇지 않다면 local에 환경설정하는 것이 BEST** 

### 1.2 Next.js란?
Angular, React, Vue와 같은 프레임워크가 등장하며 웹 개발 분야는 급속도로 변화함. 
* 리액트는 메타(페이스북)의 조던 발케가 만들어, 2013년 오픈소스를 발표.
#### [ Next.js가 제공하는 새로운 기능들 ]
* **코드 분할(Splitting):** 페이지를 로딩 할 때 번들을 여러 조각으로 나누어 필요한 부분만 전송.
<br><br>
* 파일 기반 라우팅 (React에서는 React-Router-Dom사용)
<br><br>
* 경로 기반 **프리페칭(Prefetching):** 사용자가 다음에 이동할 수 있는 페이지를 미리 가져오는 기술.
<br><br>
* **서버 사이드 렌더링(SSR):** 페이지 요청이 올때 마다 사전 렌더링. (페이지 요청 시 Fetching 요소 적용하여 렌더링)
<br><br>
* **정적 사이트 생성(SSG):** 빌드하는 동안 페이지를 사전 생성. (Fetching 요소 적용하려면 재 빌드 해야함.)
<br><br>
* **증분 정적 콘텐츠 생성(ISR)** 배포 후에도 재 배포 없이 계속 없데이트 (일정 시간마다 SSG를 재렌더링)
<br><br>
* 타입스크립트 기본 지원
<br><br>
* **자동 폴리필(Polyfill)적용:** 이전 브라우저에서 최신 기능을 제공하는 데 필요한 코드를 제공.
<br><br>
* **이미지 최적화:** Next/image 컴포넌트로 제공하는 이미지 최적화 기술 ( laxy loading-지연, 이미지 사이즈 최적화-webp 변환, placeholder-영역 확보)
<br><br>
* 웹 애플리케이션의 국제화 지원: **다국어 지원** (local에 맞는 URL로 라우팅)
<br><br>
* Next.js는 현재 넷플릭스, 트위치, 틱톡, 나이키, 우버, 엘라스틱 등 사이트에서 사용 중임.

### 1.3 Next.js와 비슷한 프레임워크
#### [ Gatsby ]
* 정적 웹 사이트를 만들 수 있는 프레임워크
* 정적 사이트 생성만 지원
* 클라이언트 사이드 렌더링만 지원
* 동적으로 변하는 복잡한 웹 사이트 제작 불가

#### [ Razzle ]
* 서버 사이드 랜더링이 가능한 자바스크립트 애플리케이션 개발 가능
* CRA와 유사하게 프로젝트를 구성할 수 있다는 장점 (create-razzle-app)
* React, Preact, Reason-React, Angular 및 Vue와 함께 사용O

#### [ Nuxt.js ]
* Vue를 사용한 웹 애플리케이션 개발에서 리액트의 Next.js에 해당하는 프레임워크
* Nuxt.js나 Next.js 모두 같은 목표를 갖는 프레임워크지만 Nuxt.js는 더 많은 설정 필요
* 만약 Vue 개발자가 서버 사이드 렌더링이 필요하다면 Nuxt.js도 추천함.

#### [ Angular Universal]
* 정적 사이트 생성과 서버 사이드 렌더링 지원
* Nuxt나 Next와는 달리 대기업 Google에서 만듦.
* Angular로 개발하는 경우 Angular Universal을 사용하는 것이 대부분.

