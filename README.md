# 사이비켜: 길거리 포교 판별·예방 서비스

> 충남대학교 어드벤처디자인(2026-2) 팀 프로젝트 · 팀 **삼각관계**
> 2026 CNU 창의SW/AI축전 주니어 창의작품경진대회 (아이디어 부문)
> 대학생이 길거리·캠퍼스 포교를 **알아보고, 벗어나고, 함께 알릴 수 있도록** 돕는 모바일 웹 서비스

| 웹 데모 (GitHub Pages) | Claude 웹앱 (공유 제보·AI 분석) | Figma 디자인 |
|---|---|---|
| [gosua0412.github.io/saibikyeo](https://gosua0412.github.io/saibikyeo/) | [사이비켜 웹앱 열기](https://claude.ai/artifact/4ThLhj1rkRgLMdKEndBmST) | [Figma 파일 열기](https://www.figma.com/design/otjMvIPtjZu7n0PMSG6wtG) |

<p>
  <img src="docs/screenshots/01_main.png" width="200">
  <img src="docs/screenshots/06_map.png" width="200">
  <img src="docs/screenshots/08_ai.png" width="200">
  <img src="docs/screenshots/09_fake_call_ring.png" width="200">
</p>

---

## 1. 프로젝트 개요

캠퍼스 주변에서는 설문조사, 심리테스트, 인터뷰 요청 등으로 위장한 포교가 자주 일어나요. 처음에는 포교인지 알아차리기 어렵고, 알아차려도 자리를 벗어나기 곤란한 경우가 많아요. 또 어디서 이런 일이 자주 일어나는지 정보가 흩어져 있어 미리 조심하기도 어려워요.

**사이비켜**는 이 문제를 세 가지 키워드로 해결해요.

| 키워드 | 의미 | 기능 |
|---|---|---|
| **판별** | 지금 상황이 포교인지 알아본다 | AI 의심도 판별, 포교 패턴 퀴즈 |
| **회피** | 위험한 순간에 자리를 벗어난다 | 가짜 전화, 위치 알림 |
| **공유** | 겪은 사람이 알리고 함께 조심한다 | 제보 지도, 관리자 승인, 커뮤니티 |

## 2. 디자인씽킹 과정

### 공감 (Empathize)
- 팀원별 외부인 2명 이상 인터뷰 및 맥락 질의
- **팀 자체 설문 (51명):** 76%가 낯선 사람의 접근이나 원치 않는 종교 권유를 겪었고, 64%가 상대의 의도를 알아차리기 어렵다고 답함
- 가장 어려운 점: ① 자연스럽게 벗어나기 ② 의도 알아차리기 ③ 관련 정보·장소를 미리 확인하기
- 서울과기대신문 조사(162명)에서도 83%가 포교를 겪거나 목격했고, 92.6%가 대처법을 전혀 모른다고 답함
- <!-- TODO: 인터뷰에서 나온 대표적인 발언이나 발견점을 추가해 주세요 -->

### 문제 정의 (Define)
- **페르소나:** 나순진 (20세, 여, 대학생)
- **POV:** 나순진은 사이비 포교에 당하지 않기를 원한다. 왜냐하면 시간을 허비하지 않고, 정신적인 부담을 느끼고 싶지 않기 때문이다.
- **HMW:** <!-- TODO: 팀에서 정한 HMW 질문을 적어 주세요 -->

### 아이디어 (Ideate)
- 브레인스토밍 → 친화도법 → 다중투표로 기능 선정
- 선정된 기능: 포교 패턴 교육, 상황 판별, 제보 기반 지도, 상황 탈출용 가짜 전화

### 프로토타입 (Prototype)
1. **Figma 와이어프레임:** 화면 구조와 이동 흐름 설계 (`메인 화면` → `정리된 초안` 페이지)
2. **패드 손그림 초안:** 팀원과 화면별 세부 구성 논의
3. **Figma 상세 디자인:** 색·문구·아이콘을 적용한 클릭형 프로토타입 (`상세 디자인` 페이지)
4. **웹앱:** 실제로 동작하는 모바일 웹 서비스 (`src/index.html`)

### 테스트 (Test)
- <!-- TODO: 사용자 테스트 대상, 방법(Think Aloud 등), 피드백과 수정 사항을 정리해 주세요 -->

## 3. 주요 기능

- [x] **제보하기:** 카카오T처럼 실제 지도를 움직여 정확한 위치를 고르고, 접근 수법·시간대·상황을 입력
- [x] **관리자 승인:** 제보는 관리자가 확인한 뒤에만 지도에 게시 (허위 제보·비방 방지)
- [x] **제보 지도:** 실제 지도(OpenStreetMap)에 제보를 묶음으로 표시, 내 위치 기준 반경 100/300/500m 안의 제보를 가까운 순으로 보여줌
- [x] **포교 의심도 판별 AI:** 상황 문장 + 확인 질문 4개로 상·중·하를 판별하고 판단 근거와 대처법, 비슷한 제보 사례를 보여줌. 근거가 부족하면 '판단 어려움'으로 처리하고 되물음 (`js/judge.js`, 판별 엔진 v2)
- [x] **포교 패턴 퀴즈:** 실제 접근 상황 6문제, 정답 해설과 점수
- [x] **가짜 전화:** 발신자·시간·벨소리/진동을 정해 예약하거나 바로 울리기, 통화 중 대사 안내
- [x] **위치 알림:** 걸어 다니다 제보가 있는 곳 근처에 가면 알림과 진동 (페이지를 열어 둔 동안)
- [x] **커뮤니티:** 익명으로 경험 공유·질문·정보 글쓰기, 공감과 댓글, 신고
- [x] **기타 정보:** 112, 학교 상담센터, 현대종교, 지역별 이단 상담소 연락처와 대처 가이드 글
- [x] **사이비 관련 소식:** 관리자가 등록한 기사 목록

## 4. 화면 구성

| 메인 | 메뉴 | 제보하기 | 위치 선택 |
|---|---|---|---|
| <img src="docs/screenshots/01_main.png" width="180"> | <img src="docs/screenshots/02_menu.png" width="180"> | <img src="docs/screenshots/03_report.png" width="180"> | <img src="docs/screenshots/04_location_pick.png" width="180"> |

| 제보 완료 | 제보 지도 | 퀴즈 | AI 판별 |
|---|---|---|---|
| <img src="docs/screenshots/05_report_done.png" width="180"> | <img src="docs/screenshots/06_map.png" width="180"> | <img src="docs/screenshots/07_quiz.png" width="180"> | <img src="docs/screenshots/08_ai.png" width="180"> |

| 가짜 전화 | 전화 수신 | 관리자 | 기타 정보 |
|---|---|---|---|
| <img src="docs/screenshots/09_fake_call.png" width="180"> | <img src="docs/screenshots/09_fake_call_ring.png" width="180"> | <img src="docs/screenshots/10_admin.png" width="180"> | <img src="docs/screenshots/11_info.png" width="180"> |

| AI 판별 입력 | 커뮤니티 | 글 보기 |
|---|---|---|
| <img src="docs/screenshots/14_ai_input.png" width="180"> | <img src="docs/screenshots/12_community.png" width="180"> | <img src="docs/screenshots/13_post.png" width="180"> |

## 5. 디자인 원칙

- **색:** 청록(메인, 안심) · 남색(판별 기능) · 주황(회피 기능) · 빨강(위험 표시에만 사용)
- 공포감을 주는 검정·빨강 조합과, 종교적 느낌을 줄 수 있는 보라색은 피함
- 모든 화면을 스마트폰 한 손 사용 기준으로 설계 (하단 탭, 가운데 제보 버튼)

## 6. 파일 구성

```
saibikyeo/
├── index.html              # 웹앱 전체 (HTML·CSS·JavaScript)
├── js/
│   └── judge.js            # 포교 의심도 판별 엔진 v2 (표현 패턴, 부정문 처리, 안심 신호)
└── docs/
    └── screenshots/        # README용 화면 캡처
```

## 7. 기술 구성 및 실행 방법

- **화면:** HTML, CSS, JavaScript (프레임워크 없음)
- **지도:** Leaflet + OpenStreetMap
- **판별:** 규칙 엔진 v2 (`js/judge.js`). Claude 웹앱에서는 AI 분석과 함께 사용
- **글꼴:** IBM Plex Sans KR

**GitHub Pages 버전**에서는 제보·커뮤니티 글이 각자 브라우저에만 저장돼요(데모용 예시 데이터 포함). 관리자 화면은 주소 끝에 `?admin=1`을 붙이면 열려요.
여러 사람이 제보를 공유하고 AI 분석을 쓰는 버전은 [Claude 웹앱](https://claude.ai/artifact/4ThLhj1rkRgLMdKEndBmST)이에요.

**직접 실행하기:** 저장소를 내려받아 `index.html`을 브라우저로 열면 돼요.

## 8. 한계와 향후 계획

- [ ] **누구나 제보·글쓰기가 공유되도록 Firebase로 이전:** 현재 GitHub Pages 버전은 기기별 저장, Claude 웹앱은 초대받은 사람만 저장 가능
- [ ] **주소 표시:** 선택한 위치를 실제 도로명 주소로 표시
- [ ] **백그라운드 위치 알림:** 앱을 닫아도 알림 받기 (앱 출시 필요)
- [ ] **상담소 정보 검증:** 공개 전에 연락처와 운영 정보를 다시 확인

## 9. 팀원 (팀 삼각관계)

<!-- TODO: 팀원 이름과 역할을 채워 주세요 -->

| 이름 | 역할 |
|---|---|
|  |  |
|  |  |
|  |  |
