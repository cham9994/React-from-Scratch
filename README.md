# 컴포넌트

- 여러 컴포넌트들을 만들어 연결함
- App.js가 최상단 루트 컴포넌트이고 그 밑에 트리구조로 여러 컴포넌트들을 만들 수 있음
- 결국 index.js가 렌더링 하는 것은 App.js
- 컴포넌트를 만들때는 첫 시작 글자를 대문자로 작성
- 컴포넌트는 결국 html을 반환하는 js 함수! 함수 형식으로 작성됨
- 컴포넌트 안 html 요소를 작성할 때 jsx의 코드 조각마다 반드시 루트 요소가 필요
  ⇒ 즉 jsx에서는 하나의 루트요소만 있어야함!

# JSX 소개

> `$ npx create-react-app react-complete-guide`

⇒ 리액트 프로젝트 시작, 관련 파일 자동으로 만들어지고 리액트 개발자 서버가 실행됨

> ` $ npm start` ⇒ 개발 서버 오픈

> `$ npm crtl + c` ⇒ 개발 서버 오픈 취소

- index.js 파일 - ReactDom을 import 해옴 라이브러리를 불러오는 과정임
- ReactDom의 내장 메서드로 render를 사용하여 App 컴포넌트를 렌더링
- public 폴더에 index.html이 존재
- App은 컴포넌트, index.js에서는 App 컴포넌트를 렌더링
- App 컴포넌트 안에는 함수 형태의 코드가 존재하고 export 할 수 있음
- App은 무언가를 반환함 → 바로 html 파일
- App은 JSX 구문으로 되어 있음
- JSX는 JS 안에있는 html을 말함.
- 개발 서버를 오픈하고 개발자 도구 안 static/js 폴더 안을 보면 여러 JS 파일이 있음
- 이곳에는 여러 코드가 있는데 리액트 라이브러리 소스 코드를 비롯한 리액트 패키지 코드임
- 이 파일들이 JSX 구문을 작성하면 브라우저에서 읽을 수 있는 코드로 변환해줌

# 리액트 기초 및 작동방식

- 컴포넌트는 기본적으로 사용자에 의해 정의된 커스텀된 HTML 요소
- 선언적 접근 방식 → 리액트는 목표 상태(state)를 정의하고 화면에 보이는 것을 업데이트 하는 DOM 지시사항들을 생성하고 실행하는 역할
- return 안 html 구조 모습이 목표 상태, 즉 결국 그 html 코드를 반환하는 것
- 일반 자바스크립트로 DOM을 만드는 것은 명령형 접근 방식
- 리액트는 목표로 하는 html 요소의 최종 상태를 정의하고 이 요소들을 화면에 불러오기 위한 지시사항들을 뒷단에 생성함 ⇒ 이것이 컴포넌트를 쓰는 이유

## 컴포넌트 활용

- 컴포넌트의 return문 뒤 html 요소를 작성할 때 소괄호로 묶어주어 하나의 문장이라고 의미를 전달할 수 있다.
- CSS를 컴포넌트 파일으 import 하면서 리액트가 렌더링 할 때 CSS파일도 같이 컴파일 할 수 있도록 해야한다.
- JSX 요소의 클래스 이름을 정할 때는 className으로 해야한다. class는 JS의 예약어이기 때문에
- html 요소의 중간에 중괄호를 넣으면 자바스크립트 코드를 그 안에서 실행할 수 있다.(동적인 데이터 출력)
- props를 통해 컴포넌트 간 데이터 전송이 가능하다.
- 그냥 props를 전달할 경우 여러 데이터를 props 하나로 전송이 가능하다.(여기서 props =>모든 속성을 받는 객체가 됨)

> Router 부분 먼저 듣기

# Router

- SPA(Single Page Application)구현해줌
- 페이지가 바뀔 때 마다 새로운 html을 다운 받는 것이 아니라,
- 클라이언트에서 컴포넌트간 경로를 설정하여 속도를 개선할 수 있다.

## Router v6

- 라우터6에서는 exact를 쓰지 않음 -> 경로가 완전히 일치할 경우에만 동작
- 에스터리스크(\*)를 붙인다면 5버전 처럼 사용 가능(url내 관련 모든 페이지 보여줌)
- ㄷㄹ

# section 12: How React Works

## 리액트의 백그라운드 작업 - 리액트가 실제 작동하는 방식

- JS 라이브러리
- 리액트의 핵심은 컴포넌트 -> 내장기능: props 통신, state 관리, 컴포넌트 전체 데이터인 context 등을 바탕으로 Real DOM 렌더링

### 컴포넌트와 Real DOM 간의 통신

- 리액트는 컴포넌트를 관리하고 결국 가상 DOM을 사용하는 것
- 가상 DOM은 최종 렌더링 전 컴포넌트 트리를 결정함
- 가상 DOM: 리액트가 컴포넌트 트리를 통해 구성한 가상 스냅샷
- 가상 DOM과 일치하도록 실제 DOM을 조작!
- state나 props, context, 컴포넌트가 변경되면 컴포넌트가 재실행되는데 이를 재평가라 한다.
- 재평가는 DOM을 다시 렌더링하는 것은 아니다!
- 리액트는 가상 DOM과 실제 DOM의 차이를 비교하여 필요한 부분만 변경, 재평가한다.
  => 최종 스냅샷과 현재의 스냅샷을 실제 DOM에 전달하는 구조!
- 새로운 요소를 추가하면 차이를 인식하고 새로운 값만 리액트 DOM에 전달하고 리액트 DOM은 실제 DOM을 업데이트
  => 리액트 DOM은 전체 DOM을 재렌더링 하지않는다!