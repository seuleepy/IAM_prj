# PROJECT_PLAN.md

# 🐈 I AM — 나만 고양이 없어

---

## 1. 프로젝트 개요

### 프로젝트명
**나만 고양이 없어**

### 한 줄 정의
매력적인 고양이들을 힙한 인터랙티브 웹사이트로 소개하고, 한 키보드로 두 사람이 함께 즐기는 고양이 미니게임을 제공하는 웹 서비스

### 프로젝트 목표
- 큰 타이포그래피와 마우스 반응형 고양이로 강한 첫인상을 만든다.
- 실제 고양이 프로필과 사진을 재미있게 소개한다.
- 한 대의 컴퓨터와 한 개의 키보드로 두 사람이 바로 즐길 수 있는 게임을 구현한다.
- HTML, CSS, Vanilla JavaScript만 사용한다.
- 1일차에는 메인 SPA를 완성하고, 2일차에는 MPA와 게임으로 확장한다.
- PC와 모바일에서 소개 페이지가 자연스럽게 보이도록 구현한다.
- 키보드 게임은 PC 환경을 중심으로 제공하고, 모바일에는 PC 플레이 안내를 표시한다.

---

## 2. 핵심 콘셉트

### 메인 메시지

```text
나만
고양이
없어
```

서브 문구 예시:

```text
고양이는 없지만,
고양이 구경은 누구보다 진심입니다.
```

또는:

```text
남의 고양이로 채우는
나의 고양이 없는 삶.
```

### 디자인 방향
- Milo AI 개인 웹사이트처럼 레트로하고 실험적인 분위기
- 화면을 크게 채우는 타이포그래피
- 검은색 또는 매우 어두운 배경
- 형광 주황, 라임 등의 포인트 컬러
- 고양이 누끼 이미지와 스티커형 장식
- 겹쳐진 카드와 포스터 형태의 UI
- 마우스와 스크롤에 반응하는 인터랙션
- 고양이 밈과 인터넷 문화가 섞인 유쾌한 분위기

### 핵심 경험
1. 첫 화면에서 고양이가 마우스에 반응한다.
2. 스크롤하면 여러 고양이의 프로필을 구경할 수 있다.
3. 게임 페이지에서 두 사람이 한 키보드로 대결한다.

---

## 3. Vanilla JavaScript 구현 가능 여부

**구현 가능하다. 별도의 프레임워크나 게임 엔진이 필요하지 않다.**

사용할 핵심 기능은 다음과 같다.

- `keydown`, `keyup`: 두 플레이어의 키 입력 감지
- `Set`: 현재 누르고 있는 여러 키를 동시에 저장
- `requestAnimationFrame()`: 캐릭터 이동과 게임 화면 갱신
- `setInterval()` 또는 시간 누적 방식: 아이템 생성
- `getBoundingClientRect()`: 캐릭터와 아이템 충돌 판정
- DOM 요소와 CSS `transform`: 캐릭터와 아이템 이동
- `setTimeout()`: 카운트다운과 결과 연출
- `localStorage`: 최고 점수 저장 시 선택적으로 사용

게임 엔진 없이도 충분히 구현할 수 있으며, 이번 프로젝트에서는 Canvas보다 **HTML 요소를 절대 위치로 움직이는 DOM 방식**이 수정과 디자인 적용이 쉬워 더 적합하다.

---

## 4. 전체 페이지 구조

2일차 MPA 요구사항을 충족하기 위해 세 페이지로 구성한다.

### 1. `index.html`
메인 대문 및 프로젝트 소개

주요 구성:
1. 상단 고정 네비게이션
2. 마우스 반응형 고양이가 있는 히어로
3. 짧은 프로젝트 소개
4. 대표 고양이 미리보기
5. 고양이 구경 및 게임 이동 버튼
6. 푸터

### 2. `cats.html`
고양이 프로필 갤러리

주요 구성:
1. 고양이 프로필 카드 목록
2. 이름, 성격, 한 줄 대사
3. 인스타그램 링크
4. 이미지 상세 모달
5. 꾹꾹이 발바닥 인터랙션

### 3. `game.html`
한 키보드 2인용 고양이 게임

주요 구성:
1. 게임 방법 안내
2. 플레이어 키 안내
3. 3초 카운트다운
4. 30초 게임
5. 실시간 점수
6. 승자 발표
7. 다시 하기 버튼

---

## 5. 공통 네비게이션

```html
<nav class="site-nav">
  <a href="index.html" class="logo">NO CAT CLUB</a>

  <div class="nav-links">
    <a href="index.html">HOME</a>
    <a href="cats.html">CATS</a>
    <a href="game.html">GAME</a>
  </div>
</nav>
```

요구사항:
- 세 HTML 파일에 동일한 네비게이션 사용
- 현재 페이지 링크에 활성화 스타일 적용
- 화면 상단 고정
- 반투명 배경과 `backdrop-filter` 적용
- 모바일에서는 글자 크기와 간격 축소

---

# 6. 메인 페이지 계획

## 6.1 히어로 섹션

### 구성
- 화면 전체 높이 사용
- 거대한 `나만 고양이 없어` 제목
- 누끼 처리한 대표 고양이 이미지
- 고양이가 제목 일부를 가리도록 겹쳐 배치
- 발바닥, 별, 왕관, 경고문 등의 스티커
- 짧은 소개 문구
- `고양이 구경하기` 버튼
- `둘이서 게임하기` 버튼
- 스크롤 안내

### 마우스 반응형 고양이

```javascript
const hero = document.querySelector('.hero');
const heroCat = document.querySelector('.hero-cat');

hero.addEventListener('pointermove', (event) => {
  const rect = hero.getBoundingClientRect();

  const x =
    (event.clientX - rect.left) / rect.width - 0.5;
  const y =
    (event.clientY - rect.top) / rect.height - 0.5;

  heroCat.style.transform = `
    translate3d(${x * 45}px, ${y * 25}px, 0)
    rotate(${x * 5}deg)
  `;
});

hero.addEventListener('pointerleave', () => {
  heroCat.style.transform =
    'translate3d(0, 0, 0) rotate(0deg)';
});
```

### 모바일 대응
- 마우스 추적 대신 천천히 떠 있는 애니메이션 적용
- `prefers-reduced-motion` 설정에서는 움직임 최소화
- 제목과 고양이가 겹쳐 잘리지 않도록 세로 배치로 변경

---

## 6.2 대표 고양이 미리보기

메인 페이지에는 전체 목록 대신 3마리 정도만 보여준다.

표시 정보:
- 고양이 사진
- 이름
- 짧은 성격
- `ALL CATS` 버튼

전체 고양이 목록은 `cats.html`에서 제공한다.

---

# 7. 고양이 갤러리 계획

## 7.1 유지할 기존 기능
- `data.js` 기반 동적 렌더링
- 프로필 이미지 표시
- 인스타그램 링크
- 이미지 클릭 시 모달
- 꾹꾹이 버튼과 발바닥 효과

## 7.2 변경할 디자인
- 원형 프로필 중심의 일반 카드에서 스티커형 카드로 변경
- 카드마다 다른 포인트 컬러 적용
- 카드마다 미세한 회전 각도 적용
- hover 시 카드가 위로 올라오고 살짝 기울어지는 효과
- 이름, 성격, 한 줄 대사 표시

## 7.3 모달 개선
- 좌우 화살표 버튼
- 현재 이미지 번호
- 배경 클릭 시 닫기
- `Escape` 키로 닫기
- 모달이 열렸을 때 배경 스크롤 차단
- 고양이별 `images` 배열 사용

---

# 8. 2인용 게임 기획

## 게임명
**냥냥 간식 쟁탈전**

## 한 줄 설명
두 고양이가 제한 시간 동안 떨어지는 간식을 더 많이 먹기 위해 경쟁하는 한 키보드 2인용 게임

## 기본 규칙
- 게임 시간은 30초
- 플레이어 1과 플레이어 2가 화면 아래에서 좌우로 움직인다.
- 위에서 생선, 간식, 장난감이 떨어진다.
- 좋은 아이템을 먹으면 점수를 얻는다.
- 오이 또는 물방울 같은 방해 아이템을 먹으면 점수가 깎이거나 잠시 느려진다.
- 시간이 끝났을 때 점수가 높은 플레이어가 승리한다.

## 조작키

### 플레이어 1
- 왼쪽 이동: `A`
- 오른쪽 이동: `D`

### 플레이어 2
- 왼쪽 이동: `←`
- 오른쪽 이동: `→`

키보드 동시 입력을 위해 `keydown` 한 번으로 움직이는 방식이 아니라, 누른 키 상태를 계속 저장해야 한다.

```javascript
const pressedKeys = new Set();

window.addEventListener('keydown', (event) => {
  pressedKeys.add(event.key.toLowerCase());
});

window.addEventListener('keyup', (event) => {
  pressedKeys.delete(event.key.toLowerCase());
});
```

게임 루프에서 매 프레임 키 상태를 확인한다.

```javascript
function updatePlayers() {
  if (pressedKeys.has('a')) {
    player1.x -= player1.speed;
  }

  if (pressedKeys.has('d')) {
    player1.x += player1.speed;
  }

  if (pressedKeys.has('arrowleft')) {
    player2.x -= player2.speed;
  }

  if (pressedKeys.has('arrowright')) {
    player2.x += player2.speed;
  }
}
```

## 아이템 종류

### 좋은 아이템
- 생선: `+1점`
- 츄르: `+3점`
- 털실공: `+2점`

### 방해 아이템
- 오이: `-2점`
- 물방울: 2초 동안 이동 속도 감소

처음 구현할 때는 생선과 오이 두 종류만 만든다. 기본 기능이 완성된 뒤 아이템을 추가한다.

---

## 8.1 게임 진행 순서

### 시작 전
1. 두 플레이어의 조작키 표시
2. `게임 시작` 버튼
3. 3, 2, 1 카운트다운
4. 게임 시작

### 게임 중
1. 아이템이 일정 간격으로 생성됨
2. 아이템이 위에서 아래로 이동
3. 두 플레이어가 좌우로 이동
4. 충돌하면 점수 반영
5. 화면 상단에 남은 시간과 점수 표시

### 게임 종료
1. 모든 움직임 정지
2. 플레이어별 최종 점수 표시
3. 승자 또는 무승부 발표
4. `다시 하기` 버튼 표시
5. 선택적으로 최고 점수 저장

---

## 8.2 게임 화면 구조

```html
<section class="game-page">
  <div class="game-info">
    <div>PLAYER 1: <span id="score-p1">0</span></div>
    <div>TIME: <span id="timer">30</span></div>
    <div>PLAYER 2: <span id="score-p2">0</span></div>
  </div>

  <div id="game-board" class="game-board">
    <div id="player-1" class="player player-1"></div>
    <div id="player-2" class="player player-2"></div>
  </div>
</section>
```

게임 보드는 `position: relative`, 플레이어와 아이템은 `position: absolute`를 사용한다.

---

## 8.3 게임 상태 데이터

```javascript
const gameState = {
  isRunning: false,
  timeLeft: 30,
  animationId: null,
  lastItemTime: 0
};

const player1 = {
  x: 100,
  y: 0,
  speed: 5,
  score: 0
};

const player2 = {
  x: 500,
  y: 0,
  speed: 5,
  score: 0
};

const items = [];
```

---

## 8.4 게임 루프

```javascript
function gameLoop(timestamp) {
  if (!gameState.isRunning) return;

  updatePlayers();
  createItems(timestamp);
  updateItems();
  checkCollisions();
  renderGame();

  gameState.animationId =
    requestAnimationFrame(gameLoop);
}
```

역할:
- `updatePlayers()`: 눌린 키에 따라 플레이어 위치 변경
- `createItems()`: 일정 시간마다 아이템 생성
- `updateItems()`: 아이템을 아래로 이동
- `checkCollisions()`: 플레이어와 아이템 충돌 확인
- `renderGame()`: DOM에 위치와 점수 반영

---

## 8.5 충돌 판정

초기 구현은 `getBoundingClientRect()`를 사용한다.

```javascript
function isColliding(elementA, elementB) {
  const a = elementA.getBoundingClientRect();
  const b = elementB.getBoundingClientRect();

  return !(
    a.right < b.left ||
    a.left > b.right ||
    a.bottom < b.top ||
    a.top > b.bottom
  );
}
```

아이템과 플레이어가 충돌하면:
1. 점수 변경
2. 아이템 배열에서 제거
3. DOM에서도 제거
4. 짧은 효과 표시

---

## 8.6 한 키보드 사용 시 주의점

일부 키보드는 특정 키를 동시에 많이 누르면 입력을 놓치는 `키 고스팅` 현상이 있을 수 있다.

대응:
- 기본 조작은 `A/D`와 방향키 사용
- 점프나 추가 액션 키는 초기 버전에서 제외
- 실제 사용할 교육장 키보드에서 동시 입력 테스트
- 방향키 스크롤 방지를 위해 게임 중 `event.preventDefault()` 적용

```javascript
window.addEventListener('keydown', (event) => {
  const gameKeys = [
    'a',
    'd',
    'ArrowLeft',
    'ArrowRight'
  ];

  if (gameState.isRunning &&
      gameKeys.includes(event.key)) {
    event.preventDefault();
  }
});
```

---

# 9. `data.js` 수정 계획

기존 고양이 목록과 이미지 경로 함수는 유지한다.

토너먼트용 `wins`, `matches`는 삭제하거나 사용하지 않는다.

```javascript
const cats = [
  {
    id: 1,
    name: "럭키",
    englishName: "LUCKY",
    personality: "인간을 부리는 전략가",
    message: "사료는 정각에 준비하도록.",
    dirName: "lucky",
    instaLink:
      "https://www.instagram.com/cat.lucky.zip/",
    accentColor: "#ff5c35",
    images: [
      "profile.jpg",
      "0.jpg",
      "1.jpg"
    ]
  }
];
```

추가할 필드:
- `englishName`
- `personality`
- `message`
- `accentColor`
- `images`

게임에서 사용할 플레이어 이미지는 `cats` 데이터 중 두 마리를 선택하거나 별도의 게임용 이미지를 사용한다.

---

# 10. 파일 구조

```text
project/
├─ index.html
├─ cats.html
├─ game.html
├─ data.js
├─ style.css
├─ main.js
├─ cats.js
├─ game.js
└─ assets/
   ├─ images/
   │  ├─ hero/
   │  │  └─ hero-cat.png
   │  ├─ game/
   │  │  ├─ player1.png
   │  │  ├─ player2.png
   │  │  ├─ fish.png
   │  │  └─ cucumber.png
   │  ├─ lucky/
   │  ├─ nyang2/
   │  └─ ...
   └─ icons/
```

### 파일 역할
- `style.css`: 세 페이지 공통 스타일
- `main.js`: 히어로와 메인 페이지 인터랙션
- `cats.js`: 고양이 목록 렌더링과 모달
- `game.js`: 게임 상태, 입력, 이동, 충돌, 점수
- `data.js`: 고양이 프로필 데이터

---

# 11. 현재 코드에서 유지·수정할 부분

## 유지
- `data.js` 데이터 분리 구조
- `getCatImageUrl()` 함수
- 고양이 목록 동적 렌더링
- 이미지 모달 아이디어
- 꾹꾹이 발바닥 인터랙션
- 로딩 고양이 애니메이션 아이디어

## 수정
- 프로젝트 제목을 `나만 고양이 없어`로 변경
- 중복된 `id="cat-list"` 제거
- 빠진 `fadeUp` 애니메이션 추가
- 하단 네비게이션을 상단 링크 네비게이션으로 변경
- 토너먼트와 랭킹 관련 UI 및 데이터 제거
- 메인 목록을 `cats.html`로 이동
- 이미지 배열을 `data.js`에서 관리
- 인라인 스타일을 `style.css`로 이동

---

# 12. 작업 우선순위

## 1단계: 기존 코드 정리
- [ ] 현재 파일 백업
- [ ] 중복 `cat-list` 제거
- [ ] 기존 하단 네비게이션 제거
- [ ] 토너먼트·랭킹 문구 제거
- [ ] `fadeUp` 애니메이션 추가
- [ ] 인라인 스타일 정리

## 2단계: 프로젝트명과 구조 변경
- [ ] 제목을 `나만 고양이 없어`로 변경
- [ ] `index.html`, `cats.html`, `game.html` 구조 확정
- [ ] 공통 상단 네비게이션 작성
- [ ] 페이지 간 링크 테스트

## 3단계: 메인 히어로 완성
- [ ] 누끼 고양이 이미지 준비
- [ ] 큰 한글 타이포그래피 배치
- [ ] 마우스 추적 효과
- [ ] 스티커 장식
- [ ] 두 CTA 버튼
- [ ] 모바일 반응형

## 4단계: 고양이 갤러리 이동
- [ ] 기존 렌더링 코드를 `cats.js`로 이동
- [ ] `data.js` 정보 확장
- [ ] 카드 디자인 변경
- [ ] 모달 개선
- [ ] 인스타그램 링크 테스트

## 5단계: 게임 최소 기능 구현
- [ ] 게임 보드 만들기
- [ ] 플레이어 두 마리 배치
- [ ] `A/D`, 방향키 이동
- [ ] 화면 밖 이동 제한
- [ ] 생선 아이템 생성
- [ ] 충돌 시 점수 증가
- [ ] 30초 타이머
- [ ] 승자 표시
- [ ] 다시 하기

## 6단계: 게임 재미 추가
- [ ] 오이 방해 아이템
- [ ] 획득 애니메이션
- [ ] 점수 팝업
- [ ] 시작 카운트다운
- [ ] 효과음 또는 음소거 버튼
- [ ] 플레이어 캐릭터 선택

## 7단계: 최종 테스트
- [ ] 세 페이지 링크 이동
- [ ] 콘솔 오류 없음
- [ ] 이미지 경로 오류 없음
- [ ] 두 플레이어 동시 입력
- [ ] 게임 재시작
- [ ] PC 화면 테스트
- [ ] 모바일 소개 페이지 테스트

---

# 13. 2일 작업 계획

## 1일차 — 메인 SPA 완성

### 오전
1. 현재 프로젝트 백업
2. 제목과 네비게이션 변경
3. 코드 오류 정리
4. `data.js` 확장
5. 히어로용 이미지 준비

### 오후
1. 히어로 레이아웃 구현
2. 마우스 반응형 고양이 구현
3. 고양이 프로필 섹션 재디자인
4. 모달과 꾹꾹이 기능 개선
5. 모바일 반응형 적용
6. SPA 기능 테스트

### 완료 기준
- 첫 화면에서 `나만 고양이 없어` 콘셉트가 명확하다.
- 고양이가 마우스에 반응한다.
- 고양이 목록과 모달이 작동한다.
- PC와 모바일에서 화면이 깨지지 않는다.

---

## 2일차 — MPA와 2인용 게임

### 오전
1. `cats.html` 생성
2. `game.html` 생성
3. 공통 네비게이션 삽입
4. 기존 프로필 목록을 `cats.html`로 이동
5. 플레이어 키보드 이동 구현

### 오후
1. 아이템 생성과 낙하 구현
2. 충돌 및 점수 구현
3. 타이머와 종료 조건 구현
4. 결과 화면과 재시작 구현
5. 디자인과 효과 추가
6. 동시 키 입력 및 전체 페이지 테스트
7. Git 커밋 정리

### 완료 기준
- 세 페이지가 서로 연결된다.
- 두 플레이어가 한 키보드로 동시에 움직인다.
- 아이템을 먹으면 점수가 반영된다.
- 제한 시간이 끝나면 승자를 표시한다.
- 다시 시작할 수 있다.

---

# 14. MVP와 추가 기능

## 반드시 완성할 MVP
- `나만 고양이 없어` 히어로
- 마우스 반응형 고양이
- 고양이 프로필 갤러리
- 이미지 모달
- 3페이지 MPA
- 두 플레이어 좌우 이동
- 생선 아이템 생성
- 충돌 및 점수
- 30초 타이머
- 승자 발표
- 다시 하기

## 시간이 남을 때 추가
- 오이 방해 아이템
- 츄르 보너스 아이템
- 캐릭터 선택
- 효과음 및 음소거
- 최고 점수 저장
- 아이템 획득 팝업
- 화면 흔들림 효과
- 커스텀 커서
- 랜덤 고양이 말풍선
- 이스터에그

---

# 15. Git 커밋 계획

```text
chore: backup initial cat project
fix: clean duplicate elements and animations
refactor: rename project and update navigation
feat: build interactive hero section
feat: move cat gallery to cats page
feat: improve cat cards and modal
feat: create two player game board
feat: add keyboard movement controls
feat: add falling items and collision
feat: add timer scoring and game result
style: improve responsive layouts
fix: test simultaneous keyboard input
docs: update project plan
```

---

# 16. 지금 바로 해야 할 일

1. 프로젝트 제목과 네비게이션 문구 변경
2. `tournament.html`, `dashboard.html` 계획 폐기
3. `cats.html`, `game.html` 파일 생성
4. 히어로용 누끼 고양이 이미지 준비
5. 새 `index.html` 히어로 구현
6. 기존 고양이 목록을 `cats.html`로 분리
7. `game.html`에 빈 게임 보드 제작
8. 두 플레이어의 좌우 이동부터 구현
9. 생선 하나를 떨어뜨리고 충돌 테스트
10. 점수와 타이머를 연결한 뒤 디자인 추가

**게임 구현은 디자인보다 먼저 최소 기능부터 만든다.  
두 캐릭터가 움직이고 생선 하나를 먹어 점수가 오르면 핵심 기술은 이미 완성된 것이다.**