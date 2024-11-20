# ⛄ 202230133 정지호

## 11월 20일 강의

## Directory 구조

#### [ features Directory ]

- 특정 기능이나 도메인 별로 코드를 구성하는 데 사용
- 사용자 인증 기능, 프로필 관리 기능 등 각 기능과 관련된 상태 관리, AP 요청, 슬라이스,
  컴포넌트 등을 보관
- 재 사용이 불가능하거나 가능하더라도 많은 수정을 해야 하는 컴포넌트를 관리

## Redux 주요 File의 역할

#### Redux Slice

- Slice는 Redux Toolkit에서 사용되는 용어로, 특정 기능과 관련된 상태와 reducer 함수의 모
  음
- Slice라는 이름은 애플리케이션 상태의 한 부분을 의미
- Redux Toolkit의 createslice 함수를 사용하면 특정 기능과 관련된 상태, 액션, reducer를 한
  곳에서 정의할 수 있어 관리하기가 용이

## Context API vs. Redux

### [ Redux ]

- Redux는 전역 상태를 관리하기 위한 독립적인 state 관리 라이브러리
- 상태의 변경을 예측 가능하게 하고, 전역 state 관리를 더 구조적으로 지원
- store, reducer, action 등의 개념을 사용해 state와 state dispatch를 관리

#### 장점

- 명확한 상태 관리 구조:액션과 reducer를 통해 state dispatch 과정을 예측 가능하게 만들
  고, 코드의 가독성을 높임
- 미들웨어 지원: redux-thunk, redux-saga와 같은 미들웨어를 사용해 비동기 로직을 쉽게
  처리
- 디버깅 도구: Redux DevTools를 통해 상태 변화 및 디버깅이 용이
- 모든 프레임워크와 호환 : React뿐만 아니라 다른 Javascript 프레임워크와도 함께 사용O

#### 단점

- 설정과 코드 복잡도 : Context AP1에 비해 설정이 복잡하며, boilerplate 코드가 많이 필요
- 추가 라이브러리 필요: Redux자체가 외부 라이브러리이므로 설치 및 유지 관리가 필요
- 작은 애플리케이션에는 과한 설정: 단순한 상태 관리가 필요한 작은 애플리케이션에서는
  과도한 설정일 수 있음

## 11월 13일 강의

#### Context API 개요

- Context는 Ux구축에 많이 사용되는 React의 기능
- React는 16.3 버전부터 정식적으로 context api 를 지원
- 일반적으로 props는 부모에서 자식으로 전달되는 단방향 통신을 함.
- Context APl는 특정 component가 props를 사용하지 않고, 하위 component를 포함한 모
  든 component에 데이터를 공유할 수 있는 기능을 제공함.
- 즉 "전역"으로 데이터를 사용할 수 있도록 해줌.
- 사용자의 로그인 상태나, 쇼핑커트의 물품 수량 등을 표시할 때 사용됨.
- Context API는 createContext, Provider, useContext 개념만 알면 적용 가능.

#### Props 흐름의 이해

• Nextjs의 데이터 흐름은 단방향으로 이루어짐.

- 즉, parents에서 child component의 방향으로 props의 흐름이 이뤄짐.
- 따라서 계층 구조가 복잡해 지면 Props Drilling 문제 발생
- Props Driling은 여러 개의 component를 지나 props가 전달 되면서 발생하는 문제

• Props Drilling은 다음과 같은 문제를 발생 시킴.

1. 중간에 위치한 component에 불필요한 props를 전달해야 하는 문제.
2. 타겟 component까지 props가 전달되지 않을 경우 원인 규명의 어려움.
3. 필요 이상으로 코드가 복잡해 지는 문제

#### 이런 문제를 해결하려면 props를 전역으로 사용하면 됩니다.

- Nextjs에서 props를 전역으로 사용하기 위해서 Context API, Redux 등을 사용합니다.

## 11월 06일 강의

### UI 프레임 워크

#### Tailwind CSS

- 다른 프레임워크랑 다르게 css 규칙만 제공
- 자바스크립트 모듈이나 리액트 컴포넌트를 제공하지 않기 때문에 필요한 경우 직접 만들어야함
- 변수값을 조정하여 개성있는 디자인을 만들 수 있다 (자유도 높음)
- dark mode 및 light mode를 쉽게 적용 가능
- 빌드 시점을 사용하지 않는 클래스는 제거 되기 때문에 높은 수준의 최적화 지원

### Headless Ui

- TailwindCSS를 만든 Tailwind Labs 팀의 무료 오픈 소스 프로젝트
- TailwindCSS는 모달이나 버튼 등 동적인 컴포넌트를 만들려면 직접 자바 스크립트 코드를 작성해야하지만 이러한 단점을 보완하기 위해 Headless UI가 만들어짐
- Headless Ui는 CSS 클래스를 제공하는 것이 아니라 동적 컴포넌트만 제공

## 10월 30일 강의

### styled JSX

- styled JSX는 CSS-in-JS 라이브러리(내장 모듈로 설치 X)

### CSS-in-JS

#### 단점

- IDE나 코드 편집기 등 개발 도구에 대한 지원 부족
- 문법 하이라이팅, 자동 완성, 린트(lint) 기능 제공 X
- 코드 내에서 CSS에 대한 의존성이 점점 커지기에 앱 번들도 커지고 느려짐.
- 서버에 미리 CSS를 생성해도 클라이언트에서 리액트 하이드레이션이 끝나면 CSS를 다시 생성해야함.
- 때문에 실행 시점에 부하가 커지며, 웹 앱이 계속 느려지게 됨. 기능을 추가 할 수록 현상이 多;

### SASS

- Next에서 기본으로 지원하는 전처리기(패키지 설치 필요)
- SASS 및 SCSS(Sassy CSS) 문법으로 CSS Modlue 만들고 사용 O

## 10월 25일 강의

### 클라이언트에서 REST API 사용하기

- getServerSideProps나 getStaticProps함수 내에서 REST APIㄹ르 호출하면 서버가 데이터를 가져오지만,
- 그 외의 컴포넌트 내에서 데이터를 불러오는 작업은 클라이언트가 실행
- 클라이언트는 주로 두 가지 시점에 데이터를 불러옴.
  - 1. 컴포넌트가 마운트된 후
  - 2. 특정 이벤트가 발행한 후
- Next라고 하여 React와 다른 특별한 방법을 사용해야 할 필요는 없음.
- 브라우저의 내장 fetch API 혹은 Axios와 같은 외부 라이브러리를 사용해서 HTTP 요청을 보냄.

### TailwindCSS 패키지

- TailwindCSS 코드가 굉장히 기나, 자유롭게 디자인 가능.
- 요즘 현업에서 쓰는 사람들 多

### REST API - 기본 설계 규칙

- URL은 동사보다 명사, 대문자보단 소문자를 사용
- 주소의 마지막에 슬래시(/)를 포함하지 않기.
- 단어를 연결할 때는 하이픈(-)을 사용
- 파일확장자는 URL에 포함하지 않음
- URL에 메소드를 포함하지 않음.

### axios란?

- next.js 에서 REST API를 다룰 때 보통 axios 와 fetch 중 하나를 선택하는 경우 多

### axios

#### 장점

- 간편한 문법
- HTTP 요청 취소
- 요청 및 응답 인터셉터
- 진보된 오류 처리

#### 단점

- 추가 패키지를 설치 해야함.

### Fetch API

#### 장점

- 내장 API: 브라우저에 내장되어 있어 별도의 설치가 필요없음.
- Promise 기반: 비동기 작업 처리에 익숙한 구조
- 스트림 처리: 데이터를 스트리밍을 처리할 수 있는 기능이 있어, 큰 파일을 처리하는데 용이

#### 단점

- json 변환 수동 처리: 응답에서 json으로 변환할 때 res.json()을 호출해야함.
- 에러 처리의 복잡성: HTTP 오류 코드에 대한 처리가 약간 더 복잡.
  - 기본적으로 fetch는 네트워크 오류만들 reject 함.

### Axios 사용하기

- axios 사용법

```js
const res = await axios.get("https://api.example.com");
const products = res.data; // Axios에서 응답 본문의 데이터를 가져옴
```

- Fetch API 사용 예시

```js
fetch("https://api.example.com")
  .then((res) => res.json()) // fetch에서는 .json()으로 데이터를 추출
  .then((data) => {
    console.log(data); // 여기에 실제 응답 데이터가 있음.
  });
```

- asios.get()을 통해 받아온 응답 객체인 res는 단순히 JSON 데이터만 담고 있는 것이 아니라, HTTP 통신과 관련된 여러 정보들을 함께 포함함.
- res.status: HTTP 응답 상태 코드
- res.headers: 서버로부터 받은 헤더 정보
- res.config: 요청에 대한 설정 정보
- res.statusText: 응답 상태에 대한 설명
- res.data: 서버가 실제로 전송한 데이터

#### json

```json
{
  "token": {
    "access_token": "1e4a36bckde5tdfed348trkjy4",
    "userId": 0
  },
  "test": [
    {
      "id": 1,
      "name": "KIM",
      "title": "data.json 파일 만들기",
      "body": "project root에 생성"
    },
    {
      "id": 2,
      "name": "Lee",
      "title": "json 설치",
      "body": "백엔드 만들기 전"
    }
  ]
}
```

#### 사용 예

```jsx
import axios from "axios";

export default async function RestApi() {
  const res = await axios.get("http://localhost:3001/test");
  const users = await res.data;
  return (
    <ul>
      {users.map((user) => (
        <div key={user.id}>
          <h1>{user.id}</h1>
          <h3>{user.name}</h3>
          <h3>{user.title}</h3>
          <h3>{user.body}</h3>
        </div>
      ))}
    </ul>
  );
}
```

- 위 코드는 비동기 데이터 로딩과 상태관리가 제대로 고려되지 않았기에 몇 가지 문제가 있음.
- 특히, Next.js와 같은 리액트 기반 앱에서 비동기 데이터 처리할 떄 렌더링 주기에 맞게 상태 관리 해야함.

- useState: users를 useState로 관리하여, 데이터를 불러온 후 렌더링 할 수 있게 햇음.
- useEffect: 컴포넌트가 처음 렌더링될때 한 번만 데이ㅓㅌ를가져오기 위해 useEffect사용

## 10월 23일 강의

### Static Resource

- 정적 자원 중 이미지 파일은 SEO에 많은 영향을 미침.
- 누적 레이아웃 이동(CLS): 다운로드 시간이 많이 걸리며 렌더링 후 레이아웃 변경되는 등 UX에 영향을 미침.
- Image컴포넌트 사용 => CLS문제 해결
- lazy loading: 이미지 로드 시점을 필요할 때까지 지연시키는 기술

* 이미지 사이즈 최적화로 사이즈를 1/10이하로 줄임
* Placeholder 제공

### Image component -local

- image 컴포넌트 사용하면 다양한 props 전달 가능
- 정적 자원은 기본적으로 public 디렉토리에 저장
- 정적 자원 번들링 이후 변하지 않음
- import 방식으로 image 넣을 시 public부터. 경로 지정 확실히.
- import 방식은 이미지 크기 지정 안 해도 되지만 직접적으로 넣는 것은 지정해줘야함.

```jsx
import Image from "next/image";
import foo from "/public/images/christmas.jpg";

export default function About() {
  return (
    <>
      <h1>About page</h1>
      <Image
        src="/images/fall-4589724_1280.jpg"
        alt="낙엽"
        width={300}
        height={500}
      />
      <Image src={foo} alt="크리스마스" width={500} height={300} />
    </>
  );
}
```

fill 속성을 사용하고싶다면 크기 지정을 빼줘야함.

```jsx
<Image src="/images/fall-4589724_1280.jpg" alt="낙엽" layout="fill" />
```

responsive 속성은 크기 지정 해줘야 함.

```jsx
<Image
  src="/images/fall-4589724_1280.jpg"
  width={300}
  height={500}
  layout="responsive"
/>
```

### Image component - remote

- next.confing.mjs 수정

```jsx
/** @type {import('next').NextConfig} */
const nextConfig = {
  images: {
    remotePatterns: [
      {
        protocol: "https",
        hostname: "cdn.pixabay.com",
      },
    ],
  },
};

export default nextConfig;
```

- 이미지 출력 코드
- 서비스에 따라 도메인 차이 있을 수 있음.
- 이미지 주소 복사 O, 링크 주소 복사 X

### 4장. 디렉토리 구조 구성

- Next.js에선 특정 파일과 디렉토리가 지정된 위치에 있어야 함.
- \_app.js나 \_document.js파일, pages/ public/
- Node_modules/: Next.js 프젝의 의존성 패키지를 설치하는 디렉토리
- pages/: 애플리케이션의 페이지 파일을 저장하고 라우팅 시스템 관리
- public/: 컴파일된 CSS 및 자바스크립트 파일, 이미지, 아이콘 등의 정적 자원 관리
- styles/: 스타일링 포맷(CSS, SASS, LESS 등)과 관계없이 스타일링 모듈 관리

### 컴포넌트 구성

- 컴포넌트는 세 가지로 분류, 각 컴포넌트와 관련된 스타일 및 테스트 파일을 같은 곳에 두어야 함
- 코드를 더 효율적으로 구성하기 위해 아토믹 디자인 원칙에 따라 디렉토리 구성
- **atoms:** 가장 기본적인 컴포넌트 관리
- **molecules:** atom에 속한 컴포넌트 여러 개를 조합해 복잡한 구조로 만든 컴포넌트 관리. <br> **ex )** input, label 합쳐 만든 새로운 컴포넌트
- **organisms:** molecules와 atoms를 섞어 더 복잡하게 만든 컴포넌트 관리
  <br> **ex )** footer, carousel 컴포넌트
- **templates:** 컴포넌트를 어떻게 배치할지 결정해 사용자가 접근할 수 있는 페이지
- Button 컴포넌트를 예를 들면 다음과 같이 최소한 세 개의 파일을 만들어야 함.
- 컴포넌트, 스타일, 테스트 파일
- 이렇게 컴포넌트를 구성하면 필요할 때 컴포넌트를 찾고 수정하기 쉬움.

```
mkdir components/atoms/Button
cd components/atoms/Button
touch index.js
touch button.test.js
touch button.styled.js or style.module.css
```

### 유틸리티 구성

- 컴포넌트를 만들지 않는 코드 파일을 유틸리티 스크립트라고 함.
- 예를 들어 애플리케이션의 log파일을 저장하는 코드가 있다면 이것을 컴포넌트로 만들 필요가 있을까?
- 이렇게 렌더링에 필요한 컴포넌트가 아닌 기타 필요한 스크립트가 있다면 utilities/디렉토리에 별도로 관리하는 것이 좋음
- 각 우틸리티에 맞는 테스트 파일도 만듦.

```
cd utilities/
touch time.js
touch time.test.js
touch localStorage.js
touch localStorage.test.js
```

### 정적 자원의 구성

- 정적 자원은 public/ 디렉토리에서 관리
- 일반적인 웹 애플리케이션에선 다음과 같은 정적 자원 사용
  - 이미지
  - 컴파일한 js파일
  - 컴파일한 css 파일
  - 아이콘
  - manifest.json, robot.txt 등의 정적파일
- public.assets/ 디렉토리를 만들고 파일 유형별로 다시 디렉토리 추가
- 저장된 파일에 접근하고자 하면 예와 같이 public을 제외한 주소를 써주면 됨.
- icons/디렉토리는 주로 웹 앱 매니페스트에 제공할 아이콘을 관리함.

### 스타일 파일 구성

- 스타일 파일은 앱에서 어떤 스타일 관련 기술을 사용하는가에 따라 구성이 달라짐.
- Emotion, styled-components, JSS 와 같은 CSS-in-JS 프레임워크의 경우 컴포넌트별 스타일 파일을 만듦.
- 만일 컬러 팔레트, 테마, 미디어 쿼리와 같은 공통 스타일의 경우 styles/디렉토리를 사용.

### lib 파일 수성

- lib 파일은 서드파티 라이브러리를 감싸는 스크립트를 말함
- lib 파일은 특정 라이브러리에 특화된 것.
- GraphQL을 사용한다면, 클라이언트 초기화 하고, 질의문과 뮤테이션을 저장하는 등의 작업이 필요
- 이런 스크립트를 좀 더 모듈화하기 위해 프로젝트 root에 lib/fraphql/=디렉토리를 만듦.

```
next-js-app
- lib/
  -graphql/
    -index.js
    -queries/
      -query1.js
      -query2.js
    -mutations/
      -mutation1.js
      -mutation2.js
```

### 데이터 불러오기

- Next는 클라이언트와 서버 모두에서 데이터 불러오기 가능
- 서버는 다음 두 가지 상황에서데이터를 불러올 수 있음
  1. 정적 페이지를 만들 때 getStaticProps 함수를 사용해, 빌드 시점에 데이터를 불러올 수 있음
  2. 서버가 페이지를 렌더링 할때 getServerSideProps를 통해, 실행 도중 데이터를 불러올 수도있음.
- 데이터 베이스에서 데이터를 가져 올 수도 있지만 안전하지 않기에 권장X 데이터베이스의 접근은 백엔드에서 처리하는 것이 좋음.
- Next는 프론트만 담당하는 것이 좋음.

### 서버 데이터 불러오기

- 서버에서는 두 가지 방법으로 HTTP 요청을 만들고 처리할 수 있음.

  1. Node의 내장 HTTP 라이브러리 사용

  - 다만 서드파티 HTTP클라이언트와 비교했을때 설정하고 처리해야할 작업이 많음

  2. HTTP 클라이언트 라이브러리 사용 가능 ex) Axios

- Axios 사용이유
  1. 클라이언트 서버 모두에서 동일하게 사용할 수 있고,
  2. 가장 많이 사용.

### 서버에서 REST API 사용하기

- REST API 를 호출할 땐 public API를 호출할 것인지, private API를 호출할 것인지를 먼저 확인해야함.
- Public API는 어떤 인증이나 권한도 필요 없으며 누구나 호출 가능
- Private API는 호출 전 반드시 인증과 권한 검사 과정을 거쳐야 함.
- 구글 API를 사용하고 싶으면 OAuth 2.0을 사용해야함. (거의 산업 표준)
- 이 외 API들도 어떻게 인증과 권한 검사 과정을 거치는지 반드시 확인해야함.

## 10월 4일 강의

### Page Project Layout \_app

- \_app.jsx는 서버에 요청할 때 가장 먼저 실행되는 컴포넌트
- 페이지에 적용할 공통 레이아웃을 선언하는 곳.

#### 기본 코드

```jsx
import "@/styles/globals.css";

export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
```

### Page Project Layout \_document

- \_document.jsx는 \_app.jsx 다음에 실행
- 각 페이지에서 공통적으로 사용될 html, head, body 안에 들어갈 내용을 선언합니다.
- onClick 같은 이벤트나 CSS는 이 곳에 선언하지 않습니다.
- 만일 로직이나 스타일이 필요하다면 \_app.jsx에 선언해야 합니다.

#### 기본 코드

```jsx
import [ Html, Head, Main, NextScript] from 'next/document'

export default function Document() {
  return (
    <Html lang='ko'>
    <Head>
      <meta name="description" content="커스텀 설정"/>

      <script src="..."></script>
    </Head>
    <body>
      <Main/>
      <NextScript/>
    </body>
  )
}
```

- 대문자로 써져있다 => 컴포넌트이다

### App Project Layout \_layout.jsx

- layout.jsx는 app디랙토리 아래에 위치합니다.
- layout.jsx는 Page Project에서 사용하던 \_app.jsx와 \_document.jsx를 대체
- 이 파일은 삭제해도 프로젝트를 실행하면 자동으로 다시 생겨남.

#### 프로젝트를 생성할 때 생성된 기본 기본코드

```jsx
export const metadata = {
  title: "Next.js",
  description: "Generated by Next.js",
};

export default function RootLayout({ children }) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  );
}
```

### App Project Layout \_meta data

```jsx
export const metadata = {
  title: {
    default: "Hello Next.js!!!",
    template: " Daelim.com - %s ",
  },
  description: "Generated by create next app",
};
```

- 각 페이지에 적용된 title이 없다면 default 값 적용
- 각 페이지에 적용된 title이 있으면 template값 적용
- %s 에 각 패이지의 title이 삽입되며 위치는 바뀌어도 됨.

### Link vs. a vs. router.push

- Link component를 이용해서 Navibar component 만듦.
- `<a>` tag는 html 동기식으로 전체가 reload 되기에, 외부 링크를 할 때 사용
- 일반적으로 내부 링크 이동시에는 사용하지 않는 것이 좋음
- router.push는 빌드 후, 이동할 주소가 html 상에 노출되지 않기 때문에 SEO에 취약
- Link 컴포넌트는 빌드 후, a tag로 자동 변환
- a tag 의 장점인 SEO 최적화, prefetch 가능, 우 클릭 기능 등을 갖음.

### 정적 자원 제공

- 정적 자원은 이미지, 폰트, 아이콘, 컴파일한 css, js 등으로 /public 디렉토리 안에 저장
- 정적 자원 중 이미지 파일은 SEO에 많은 영향을 줌
- 불러오는데 많은 시간이 걸리고, 불러온 후에도 이미지 주변의 레이이웃이 변경되는 등 UX 관점에서 좋지 않은 영향을 줌.
- 이를 누적 레이아웃 이동 ( CLS: Cumulative Layout Shift)라고 함.
- 사용자가 2번째 문단을 읽고 있었다면, 위치가 바뀌어 읽던 곳을 놓칠 위험이 있음.
- Image 컴포넌트를 사용해 이와같은 CLS문제를 해결

### 자동 이미지 최적화

- Next.js 10 부터 Image 컴포넌트를 사용해 이미지를 자동 최적화 할 수 있음
- 이 기능을 사용하면 이미지를 Webp와 같은 최신 이미지 포맷으로 제공 할 수 있음.
- 최신 포맷을 지원하지 않는 브라우저의 경우 png나 jpg와 같은 예전 이미지 포맷도 제공함.
- 필요한 경우 이미지 크기를 조정할 수 있음.
- 특히 클라이언트가 이미지를 요구할 때 최적화 작업을 한다는 장점이 있음
- Unsplash나 Pexel과 같은 이미지 서비스로 이미지 제공 가능
- 먼저 next.config.js

## 10월 2일 강의

### Page Routing

- App routing ( Y / **_N_** )
- src / ? ( Y / N )
  - /pages/
  - /src/pages/

* app-router와 page-router는 같이 사용 X

## 9월 25일 강의

### Next.js 기초와 내장 컴포넌트

- Next는 서버사이드 렌더링 외에도 많은 내장 컴포넌트와 함수를 제공.
- React의 React Router, Reach Router 등은 **클라이언트 라우팅**만 구현 가능.
- Next는 파일시스템 기반 페이지와 라우팅을 함.
- 페이지는 /pages 디렉토리 안의 _.js, _.jsx, *ts, *tsx 파일에서 export한 react 컴포넌트

#### 만일 블로그와 같이 컨텐츠를 분리해야 한다면 어떻게 해야할까?

**=> /pages 아래 디렉토리를 만들고 라우팅 규칙을 만들면 됨.**<br/>
**=> /pages 디렉토리 내부에는 계층적 구조로 라우팅 규칙을 만들 수 있음.**<br/>
**=> /pages/ports 안에 index.jsdhk [slug].js를 만들어 jsx를 반환.**<br/>

- /pages/ports/디렉토리 내에 Index.js만 간단히 만들면 O

### 페이지에서 경로 매개변수 사용하기

- 경로 매개변수를 사용해 동적 페이지 쉽게 만들기 가능.
- page/greet/[name].js 파일을 만들어 보겠습니다.
- 내장 getServerSideProps 함수를 통해 URL에서 동적으로 [name] 변수 값을 가져오는 것.
- greet/Mitch 주소로 가면 'HELLO MITCH'라는 문구가 렌더링 됩니다.

#### pages 밖에서는 getServerSideprops나 getStaticProps 함수를 사용치 못하는데, 어떻게 경로 매개변수를 컴포넌트 안에서 사용할 수 있을까요?

**=> useRouter Hook을 이용하면 컴포넌트 안에서 경로 매개변수를 사용할 수 있음**<br/>
**=> useRouter은 next/router에서 가져올 수 있음**<br/>
**=> useRouter Hook을 사용해 query 매개변수를 가져옴**<br/>
**=> 콘솔에 로그를 출력하면 매개 변수와 쿼리 문자열들을 어떻게 전달하는 지 알 수 있음**<br/>

## 9월 11일 강의

- 개발 시 타입스크립트를 주 언어로 사용하고 싶다면 타입스크립트 전용 플러그인 설치 후 설정 변경.

- 웹팩은 특정 라이브러리, 페이지, 기능에 대해 컴파일된 코드를 **전부 포함하는 번들**을 만들어줌.
- SASS, LESS 같은 CSS 전처리기를 사용해 개발하고 싶다면, **웹팩 설정을 수정**해주면 됨.

#### BUT...

설정을 바꿀 일은 많지 않으며, 꼭 수정해야 한다해도 대부분 next.config.js 파일의 기본값을 변경하는 것으로 충분.

### Transpile

- Babel은 ECMAScript와 같은 자바스크립트 최신 버전이나, TypeScript 이전 버전의 코드로 변환시켜 주는 Transplie 도구임.
- 개발자가 작성한 코드 -> Parse -> Transform -> Generate -> 이전버전의 코드
- Babel의 **parser**는 JS를 컴퓨터가 이해할 수 있는 코드 구조인 Abstract Syntax Tree(AST)로 변환하는 역할.
- Babel의 **traverse** 모듈은 전체 트리 상태를 유지하며 노드 교체, 제거, 추가 담당.
- **generator**가 수정된 AST를 일반 코드로 변환해줌.
- **SWC**도 Babel과 같은 JS 트랜스 컴파일러임.
- Next 12 이후 부터 Babel에 SWC교체 되었음.
- SWC는 Rust로 작성되어 있어 Babel에 비해 속도가 훨씬 빠름.

### SWC 적용 방법

- 새로운 프로젝트에 적용하는 것은 다음 명령으로 프로젝트를 생성하면 바로 사용할 수 있음 <br>
  `$npx create-next-app@latest` or `$npx create-next-app@12`
- Next 12 이전 버전의 프로젝트에 적용하려면 다음과 같이 업그레이드 필요 <br>
  `$npm install next@12` <br>
  Babel을 설정했다면 설정 파일(babelrc 또는 babel.config.js)를 삭제해 줌.

### 렌더링 전략

- 렌더링 전략: 웹 페이지 or 웹 애플리케이션을 웹 브라우저에 제공하는 방법
- 정적인 페이지 제작에는 **Gatsby** 를 추천함.
- 서버 사이드 렌더링 전략을 원한다면 다른 프레임워크를 검토
  <br><br>
- Nest.js는 이 모든 방법을 새로운 수준으로 제공
- 빌드 시점에 정적으로, 동적으로 실행할 지 쉽게 정할 수 있음.
- 요청이 있을 때마다 페이지 다시 생성 가능
- 반드시 클라이언트에서 렌더링해야 할 컴포넌트 지정 가능.

### 서버 사이드 렌더링 (SSR)

- 웹 페이지를 제공하는 가장 흔한 방법.
- APM을 이용하는 일반적 웹 페이지 생성
- JS 코드가 적재되면 동적으로 렌더링.
  <br><br>
- Next.js도 이와 같이 동적페이지 렌더링 가능
- 여기에 스크립트 코드를 집어 넣어 나중에 웹 페이지를 동적으로 처리할 수도 있는데 이를 **하이드레이션**이라함.
  <br><br>
  즉, 어떤 사람이 작성한 블로그 글을 한 페이지에 모아 작성해야 한다면 SSR을 이용하는 것이 적당.
- 서버 사이드 렌더링 -> 자바스크립트가 하이드레이션된 페이지를 전송 -> 클라이언트에서 DOM위에 각 스크립트 코드를 하이드레이션: 페이지 새로고침없이 사용자와 웹 페이지 간 상호작용을 가능케함.
- 리액트 하이드레이션 덕에 웹 앱은 싱글 페이지 애플리케이션(SPA)처럼 작동가능.
- CSR과 SSR 장점 모두 갖음.

#### SSR의 장점

- 더 안전한 웹 애플리케이션: 쿠키 관리, 주요 API, 데이터 검증 등과 같은 작업을 서버에서 처리하기에 중요한 데이터를 노출할 필요X
- 더 뛰어난 웹 사이트 호환성: 클라이언트 환경이 자바스크립트를 사용하지 못하거나 오래된 브라우저를 사용하더라도 서비스 제공.
- 더 뛰어난 SEO: 서버가 렌더링한 HTML을 받기에 봇이나 웹 크롤러가 페이지를 렌더링할 필요가 없음.

#### SSR이 최적의 렌더링 전략이 아닌 경우

- 클라이언트가 페이지를 요청할 때마다 페이지를 다시 렌더링할 수 있는 서버 필요.
- 다른 방식에 비해 SSR이 더 많은 자원을 소모하고, 더 많은 부하를 보이며 유지 보수 비용도 증가함.
- 페이지에 대한 요청을 처리하는 시간 증가.
- 페이지가 외부 API 또는 데이터 소스에 접근해야 한다면, 해당 페이지를 렌더링할 때마다 이들 다시 요청해야 함.
- 페이지 간의 이동은 CSR에 비해 느림.
- 중요한 것은 Next.js가 기본적으로 빌드 시점에 정적으로 페이지를 만든다는 것.
  <BR><BR>
  페이지에서 외부 API를 호출하거나 데이터베이스에 접근하는 등 동적 작업을 해야 한다면 해당하는 함수를 페이지에 export해야 합니다.

## 9월 4일 강의

### 프로젝트 생성 방법

- 프로젝트 생성<br>
  ` $ npx create-next-app@latest`
- 안되면 해당 코드 작성 후 재실행 <br>
  `$ npm i -g create-react-app`
- pages를 사용하고 싶다면, App Router를 NO로 설정
- 프로젝트가 생성되면 프로젝트 디렉토리로 이동하여 `npm run dev` 명령어 실행
- 리액트처럼 바로 실행되지 않기에 `http://localhost:3000`으로 접속 (`ctrl+해당 localhost` 클릭)

### Chocolatey 설치

1. chocolatey 페이지에서 chocolatey 설치
2. powershell에 복붙 `https://chocolatey.org/install#individual`
3. powershell에서 GIT도 다운 `https://community.chocolatey.org/packages?q=git`

#### + PLUS

- pages/ 의 index.js 파일을 복사해서, about.js로 이름ㅇ르 바꾸면, `http://localhost:3000/about` 으로 접속 가능

- `ctrl+해당 localhost` 클릭 하면 바로 들어갈 수 있음.
- `ctrl+c` 누르면 워킹디렉토리에서 빠져나올 수 있음.

- 바벨이나 웹팩의 설정도 커스터마이징 가능
- 바벨 : 자바스크립트 트랜스컴파일, 최신 자바스크립트 코드를 하위 호환성을 보장하는 스크립트 코드로 변환하는 일을 담당.
- 하위 호환성이 보장되면 어떤 js코드도 실행할 수 있음.
- 바벨 사용 시 브라우저나 Node.js 등에서 지원하지 않는 기능을 사용가능.

## 8월 28일 강의

### npm vs yarn

- yarn 설치: `$ npm i -g yarn`
- yarn 확인: `$ yarn -v`
- yarn 삭제: `$ npm uni -g yarn`

### Pages Router vs App Router

- React로 개발하다 처음 Next를 사용하면 제일 먼저 놀라는 기능.
- Next.js **13.4**에서부터 **App Router**가 **stable**하게 지원하기 시작.

### [ Pages Router ]

- **pages 디렉토리**가 **root**이고, **index.js**가 **index page**가 됨.
- about.js는 /about, team.js는 /team 경로로 라우팅
- **클라이언트 중심**의 라우팅입니다.

### [ App Router ] => 강의 진행

- **app 디렉토리**가 **root**이고, **page.js**가 **index page**가 됨.
- /about/page.js는 /about, /login/page.js는 /page 경로로 라우팅.
- **서버 중심**의 라우팅입니다.
- 번들 사이즈가 작음.

### Next.js 13 vs 14

- Pages Router -> App Router
- Date Fetching: 13까지는 getServerSideProps, getStaticProps 메소드를 이용해 구현했으나,
  14에서는 SSG(정적 사이트 생성), SSR(서버 측 렌더링) 및 ISR(증분적 정적 재생성)에서 **하나의 API**만을 사용해 구현할 수 있게됨.
- **이미지 최적화**: 13까지는 **도구**를 사용했으나, 14부터는 **자체적**으로 지원하기 시작
- **보안 강화**: XSS 공격에 대한 보호 기능이 강화되고, 보안 관련 헤더 설정을 더욱 쉽게 만듦.

### Ch01. Next.js 알아보기

- Next.js는 리액트를 위해 만든 오픈소스 **자바스크립트 웹 프레임워트**
- 리액트에는 없는 **다양한 기능 제공**
  - 서버 사이드 렌더링(SSR: Server Side Rendering)
  - 정적 사이트 생성(SSG: Static Site Generation)
  - 증분 정적 재생성(ISR: Incremental Static Regeneration)

```html
SSG(정적 페이지 생성) 미리 만들어 놓은 페이지를 서비스 하기에 속도는 빠르나, 한
번 생성 후엔 수정이 불가능. 이러한 단점을 보완하고자 나온 것이 ISR(증분 정적
재생성). 이미 생성된 페이지를 일정 시간이 지난 후에 다시 생성.(최신 데이터로
업데이트)
```

#### [CH01의 주요 내용]

- Next.js.소개 / 다른 프레임워크와의 비교 / 리액트와의 차이점
- 기본 구조 타입 스크립트를 사용하는 방법
- 바벨과 웹팩 설정 커스터 마이징 ( Next.js 14는 Webpack에서 Tubopack으로 바뀜)

### 1.1 준비하기

- Node.js와 npm을 설치하거나, codesandbox.io 혹은 repl.it 등의 사이트를 이용.
  <br>
  **잠시 확인을 위한 것이면 사이트 이용도 괜찮으나, 그렇지 않다면 local에 환경설정하는 것이 BEST**

### 1.2 Next.js란?

Angular, React, Vue와 같은 프레임워크가 등장하며 웹 개발 분야는 급속도로 변화함.

- 리액트는 메타(페이스북)의 조던 발케가 만들어, 2013년 오픈소스를 발표.

#### [ Next.js가 제공하는 새로운 기능들 ]

- **코드 분할(Splitting):** 페이지를 로딩 할 때 번들을 여러 조각으로 나누어 필요한 부분만 전송.
  <br><br>
- 파일 기반 라우팅 (React에서는 React-Router-Dom사용)
  <br><br>
- 경로 기반 **프리페칭(Prefetching):** 사용자가 다음에 이동할 수 있는 페이지를 미리 가져오는 기술.
  <br><br>
- **서버 사이드 렌더링(SSR):** 페이지 요청이 올때 마다 사전 렌더링. (페이지 요청 시 Fetching 요소 적용하여 렌더링)
  <br><br>
- **정적 사이트 생성(SSG):** 빌드하는 동안 페이지를 사전 생성. (Fetching 요소 적용하려면 재 빌드 해야함.)
  <br><br>
- **증분 정적 콘텐츠 생성(ISR)** 배포 후에도 재 배포 없이 계속 없데이트 (일정 시간마다 SSG를 재렌더링)
  <br><br>
- 타입스크립트 기본 지원
  <br><br>
- **자동 폴리필(Polyfill)적용:** 이전 브라우저에서 최신 기능을 제공하는 데 필요한 코드를 제공.
  <br><br>
- **이미지 최적화:** Next/image 컴포넌트로 제공하는 이미지 최적화 기술 ( laxy loading-지연, 이미지 사이즈 최적화-webp 변환, placeholder-영역 확보)
  <br><br>
- 웹 애플리케이션의 국제화 지원: **다국어 지원** (local에 맞는 URL로 라우팅)
  <br><br>
- Next.js는 현재 넷플릭스, 트위치, 틱톡, 나이키, 우버, 엘라스틱 등 사이트에서 사용 중임.

### 1.3 Next.js와 비슷한 프레임워크

#### [ Gatsby ]

- 정적 웹 사이트를 만들 수 있는 프레임워크
- 정적 사이트 생성만 지원
- 클라이언트 사이드 렌더링만 지원
- 동적으로 변하는 복잡한 웹 사이트 제작 불가

#### [ Razzle ]

- 서버 사이드 랜더링이 가능한 자바스크립트 애플리케이션 개발 가능
- CRA와 유사하게 프로젝트를 구성할 수 있다는 장점 (create-razzle-app)
- React, Preact, Reason-React, Angular 및 Vue와 함께 사용O

#### [ Nuxt.js ]

- Vue를 사용한 웹 애플리케이션 개발에서 리액트의 Next.js에 해당하는 프레임워크
- Nuxt.js나 Next.js 모두 같은 목표를 갖는 프레임워크지만 Nuxt.js는 더 많은 설정 필요
- 만약 Vue 개발자가 서버 사이드 렌더링이 필요하다면 Nuxt.js도 추천함.

#### [ Angular Universal]

- 정적 사이트 생성과 서버 사이드 렌더링 지원
- Nuxt나 Next와는 달리 대기업 Google에서 만듦.
- Angular로 개발하는 경우 Angular Universal을 사용하는 것이 대부분.
