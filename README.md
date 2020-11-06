# You Don't Know Javascript

## 정체되지 않는 프론트엔드 개발자의 일하는 방식

1. 좋은 커밋 메세지 작성법
2. n npm // node version 관리
3. 좋거나 나쁘다 평가하지 않는다.
4. 무엇을 사용할지 고민인 된다면 많은 사람이 사용하는 것을 고르는 것도 자료찾기가 싶고 나름 괜찮은 방법이 될 수 있습니다.
5. 변수를 줄이고, 컴포넌트로 나눈다.
   - 하나의 컴포넌트는 하나의 기능만 한다.
6. 작성된 프로젝트를 망가트려 보려고 노력해본다. 사용자가 어떤 행위를 할지 모르기 때문에!

## 프레임보다 기본기

1. 정확한 용어
   - 영어 원문, 발음
2. 명확한 근거
   - 구체적은 근거를 한다
     - React vs Jquery
     - SSR..
     - 도입과 선택한 이유!
3. Web + HTML + CSS +JS
   - Web 브라우저
     - window:beforeunload
     - redirect - 서버에서 보내는 신호
     - AppCache - DNS -TCP (Network)
     - 💥 Process (domInteractive domComplete - readystatechange +
       domContentLoadedEvent - DOMContentLoaded 돔에 접근이 가능 + Load (window:load) - Image)
     - 브라우저 주요 구성 요소
       - 사용자 인터페이스
         - 웹 페이지를 제외 하는 나머지
           - 주소창, 뒤로가기 버튼, 북마크 등..
       - 브라우저 엔진
         - 사용자 인터페이스와 렌터링 엔진의 다리.
       - 렌터링 엔진
         - 실제로 화면을 표현을 하는 부분
         - HTML해석, JS 해석기, 통신
         - How Browser works... 자료 읽고 분석 10년 전, 모던 웹 브라우저 들여다보기
4. 렌터링 엔진의 동작과정 [점진적으로 보여준다. - 조금씩 자료를 보여주면서 사용자 경험을 높이고자 한다.] 한꺼번에 받아서!! 하는게 좋아!
   - HTML CSS JS파싱
     - 문서를 읽어 브라우저가 문법을 분석, 코드를 이해한다. DOM을 컨트롤 할 수 있기 때문에.
   - DOM CSSOM
     - 브라우저에서 사용할 수 있는 구조(객체)로 변환한다.
   - 🟢 렌터 트리 구축
     - DOM + CSSOM을 결합하여 화면에 그려낼 내용을작성한다. 즉, 어떤 엘리먼트에 어떤 스타일을 적용할 것인지 정해진다.
   - 🔴 렌터 트리 배치
     - Layout단계 각 요소의 크기와 위치를 계산한다.
   - 🟠 렌터 트리 그리기
     - Paint단계 요서를 실제 픽셀로 변환하여 그린다.
   - Composition 조합

### HTML

- 버전이 없는 Livin Standard로 변화
- 시대에 발맞추어 계속 변화함
- 의미를 가진 태그 대거 추가
  - section, header, footer, main, article, nav등
- 의미를 기술하기 위한 Microdata도 포한.
- canvas, video, figure, srcset
- WebSocket, WebWorker, StorageAPI, History
- 점진적 향상 vs 우아한 성능 저하

1. Semantically
   - HTML 엘리먼트와 속성, 속성값은 특정한 의미를 지니도록 정의되어있다.
2. Documents

### CSS

- 각 기능별 모듈만 존재
- css명세가 방대해 졌다.
- 레이아웃
  1. 기본 개념 두 가지
     - 크기 와 위치
  2. CSS Box Model
     - CSS레이아웃의 기본이 되는 원리
     - 엘리먼트의 크기를 정하는 표준
     - box-sizing 속성으로 크기 계산 방식 변경 가능
  3. flex box
     - display:flex
     - flex-direction, justify-content, align-items
     - 필연적인 중첩. 한 방향으로만
  4. grid Layout
  5. 논리적 프로퍼티와 값
     - line 글쓰기 방향
     - block 글쓰기 수직 방향
     - ex, margin-line-start, margin-line-end, margin-block-start, margin-block-end
- BEM, SMACSS
- 마진 병합
  1. 수직 인접한 두 마진이 더 끈 쪽으로 병합되는 현상.

### JS

1. ECMAScript

- ESM (import, from)

2. Lexical Environment

- 정의
  - 변수나 함수 등의 식별자(변수, 함수 이름)를 정의할 때 사용되는 명세
  - 중첩된 어휘적 환경에 기반해 동작
  - Environment Record와 outer 속성을 포함
- 관련 문법
  - 함수선언
  - 블럭문
  - try~catch문의 catch 절
- 종류
  - 전역 환경
  - 모듈 환경
  - 함수 환경

3. 실행 컨텍스트 Execution Context

- 정의
  - 자바스크립트 코드가 실행되는 환경
  - 모든 JS코드는 실행 컨텍스트 내부에서 실행된다.
- 종류
  - 전역 실행 컨텍스트
  - 함수 실행 컨텍스트 (함수 생성이 아닌 함수를 실행 할때 add() )

4. Lexical Scope

- 같은 범위 혹은 그 보다 안쪽의 코드에서 바깥 영역에는 접근할 수 있지만 그역은 성립하지 않는다.

5. 클로저

- 처음 만들어 질 때의 어휘적 범위를 그대로 유지한 함수. 어휘적 범위 바깥에서 해당 범위에 접근할 수 있다.

```js
function hello() {
  const h = "hello";
  return function () {
    console.log(h);
  };
}
const say = hello();
say();
```

> 함수는 자신이 선언될 때 그 어휘적 환경(Lexical Environment)을 Environment라는 변수에 저장하고 있다가 함수가 실행 될 때(실행 컨텍스트를 만들 떄) 다시 outer에다가 넣어 둔다. 그렇기 때문에 자신이 선언될 때 속해있던 실행 컨텍스트를 참조할 수 있게 된다.

## 지속 가능한 코드작성과 성능 향상법

- 간결하고 명확하게 코드의 의도를 확실하게
- 바보도 컴퓨터가 이해하는 코드를 작성할 수 있다.
- 의존성이 적은 코드를 작성해야 한다.
- 디버깅과 코드의 복잡도
- 테스트를 실패할 환경을 만들어서 테스트를 해봐야 한다.
- 70% 되면 좋은 코드라고 할 수 있다.
- TDD(Test Driven development)
  - 테스트를 작성한다. = 실패할 테스트 말고는 작성하지 않으며, 테스트 작성없이는 프로덕션 코드를 작성 하지 않는다.
  - 테스트를 통과시킨다. = 테스트를 통과하는 코드 말고는 작성 하지 않는다.
  - 리팩토링을 한다. = 중복이 보이거나 하면 중복을 줄이고 기능을 개선한다.
- BDD(Behavior Driven Development)

### 리팩터링.

1. 겉보기 동작은 그대로 인상태로, 테스트는 고치지 않은 상태로
2. 처음에는 실행, 비슷한일 진행, 비슷한 작업 3번 하면 리팩터링을 해야할 때이다.
3. Happy Path... 아니된다.
4. 순수 함수로 작성한다 (똑같은 입력값에는 항상 같은 값을 리턴한다.)
5. 중괄호 짧아도 사용한다.
6. Switch문을 쓸거면 Object리터럴을 사용한다.
7. 배열과 객체를 이뮤터블하도록 사용한다. - 새로운 객체를 만들어
8. 템플릿 문자열을 사용해서 문자열을 작성한다.

## 성능관리

- Kent Beck
  - 속도가 빨라지면 사용자 경험이 올라간다.
  - 비용절감.
  - 면접 문제로도 나온다.

1. Make it work
2. Make it right
3. Make it Fast - 프론트엔드 개발에서 성능 최적화는 다른 작업보다 우선 순위가 떨어짐.....

### 코드 바깥의 성능

### 1. 시간 : 초기 구동시간(파일 다운로드, 컨텐츠 렌더링, 인터랙션 가능) + 계산시간 + 반응시간

- 파일 다운로드: 최신 브라우저는 도메인당 최대 6개 까지 접속한다. HTTP1.1
  - 다른 도메인을 사용해서 이미지나 이런거 받아온다.
  - HTTP2.0 부터는 접속
  - 이미지 포맷을 최신으로 사용WebP & Amep
  - <picture><source>+<img></picture> 점진적 향상
  - 웹 폰트 최적화 or WOFF3(70% 정도용량)
  - link: dns-prefetch, preconneting, prefetch(파일을 미리 받아 온다.- 진짜로 필요한 경우만)
- 계산시간 + 반응시간:
  - 점진적으로 나오는게 빠르다고 인정한다.
  - 필수 컨텐츠가 아니라면 비동기 로딩을 고려 해본다(광고, 댓글, 헤더,푸터)
  - 이미지/ 아이프레임/ 스크립트 등은 필요한 때까지는 일기 않는 게으른 로딩 기법을 고려해보자. <img loading="lazy"> 브라우저가 근처에 왔을때 로딩하는 네이티브로 지원한다.
- 시간이 많이 걸린다면 플레이스 홀더 등으로 대체

#### 계산시간

- main thread
- single thread
- 워커 스레드Worker 쓰레드
  - UI를 조작할 수 없다.
  - 워커 스레드 전용으로 분리된 파일이 필요하다.
- 느긋한 계산
- 메모이제이션 💥
  - 계산 결과를 기억해두고 반복 사용하는 기법. 루프 재귀 호출 등 최적화

#### 반응시간

- 지나치게 느린 애니메이션 및 응답 속도는 사용자 경험을 저해한다.
- 가능한! css로 애니메이션을 하면 알아서 한다. transform: translate or scale or rotate / opacity
- javascript(시각적 변화) -> style -> layout -> paint -> composition <br/>
  | ---------- main thread -----------------------| |--컴포지터 스레드 --|

- requestAnimationFram, Web Animation API 활용
- three.js, velocity.js 라이브러리
- will-change 속성을 통해 브라우저가 최적화 할 속성 명시 - 최적
- DOM 접근과 업데이트는 까능한 적게. 한 번에 몰아서 처리.
  - 엘리먼트 추가는 Document Fragment를 사용하면 좋아요 한 방에!

### 2. 리소스 : 자원 소모 (CPU 점유율, Network, Storage..)
