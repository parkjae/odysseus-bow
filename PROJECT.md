# Odysseus's Bow - 통합 개발 기록 (PROJECT.md)

## 📌 1. 프로젝트 개요
- **앱 명칭**: **Odysseus's Bow**
- **라이브 웹 주소**: [https://parkjae.github.io/odysseus-bow/](https://parkjae.github.io/odysseus-bow/)
- **주요 목적**:
  - `index.html`: 활시위를 거는 **"STRING A BOW"** 단계와, 활시위를 튕겨 연주하는 **"PLUCK A BOW"** 단계를 연결한 인터랙티브 웹 애플리케이션.

---

## 🎼 2. 오디오 인터랙션 및 UX 사양

### 2.1 디바이스 호환성 및 오디오 세션 (iOS Mute Override)
- **하이브리드 iOS AudioSession 승격**:
  - 최신 iOS 17+ API (`navigator.audioSession.type = 'playback'`)와 하위 호환 HTML5 무음 Audio Hack (`SILENT_WAV_BASE64`)을 동시 적용.
  - 아이폰의 하드웨어 무음 스위치가 켜진 상태에서도 미디어 재생 카테고리로 승격되어 사운드가 스피커로 출력됨.
- **사운드 언락 전 인터랙션 차단**:
  - 오디오 활성화 버튼을 누르기 전(`!isUnlocked`)까지는 캔버스 링 드래그 및 연주 조작이 완전 차단됨.

### 2.2 음량(Volume) 및 피치(Pitch) 사양
- **`bow_1.mp3` & `bow_2.mp3`**:
  - 활시위를 걸 때 발생하는 배경음의 음량을 **50% (`0.5`)** 수준으로 은은하게 축소 조절.
- **`pluck.mp3` (FOREPLAY 시퀀스)**:
  - 1차 Pluck: **원본 피치 (`1.0`)**, 100% 음량 (`1.0`)
  - 2차 Pluck: **반음 하향 (`Math.pow(2, -1/12)`)**, 100% 음량 (`1.0`), 1차 음 재생 1초(`1000ms`) 후 연속 연주.
- **`pluck.mp3` (Scene 2 메인 연주)**:
  - 변수명: **`MAIN_SEMITONES_DOWN_RATE`** (`Math.pow(2, -3/12)` = 단3도/3반음 하향)
  - **당긴 변위 비례 동적 가변 음량 (Dynamic Displacement Volume)**:
    - 최소 50% (`0.5`) ~ 최대 130% (`1.3`)
    - 당긴 거리에 비례하여 실시간으로 음량이 가변 계산됨.
  - **다중 화음(Polyphonic) 및 연속 연주 (Rapid Plucking)**:
    - 연속 튕기기 시 이전 소리 fade-out 블로킹 차단 구문을 전면 제거하여 소리 중첩(Overlapping Polyphony) 및 연달아 패스트 플러킹 허용.

### 2.3 단계별 `promptText` 가이드라인 디스플레이
- **사운드 언락 전**: `"화면을 터치하여 사운드 활성화"` (눈에 띄는 황금빛 글로우 스타일)
- **1단계 (`STRING A BOW` 진행 중)**: `"활 시위를 걸어보세요"` (은은한 순백색 미니멀 유리 질감 스타일 복귀)
- **목적지 도달 ~ FOREPLAY 시퀀스**: `"준비 완료"`
- **2단계 (`PLUCK A BOW` 연주 중)**: `"활 시위를 당겨보세요"`

---

## 🛠️ 3. UI/UX 및 물리 엔진 사양
- **상단 타이틀 미니멀리즘**:
  - `<h1>ODYSSEUS'S BOW</h1>` 및 `<div class="sub-caption">` 아래의 불필요한 보조 설명 문구를 제거하여 최상의 미니멀 디자인 구현.
- **리로드 버튼 이벤트 전파 완전 차단 (Event Isolation)**:
  - 우측 하단 리로드 버튼 조작 시 2단계 황금 현(String)이 오작동 반응하지 않도록 모든 터치/마우스 포인터 이벤트의 `e.stopPropagation()` 처리.
- **Scene 1 (STRING A BOW)**: 미니멀 순백색 (`#FFFFFF`, Glow: White)
- **Scene 2 (PLUCK A BOW)**: 신화적 황금색 (**`#E5B409`**, Glow: Golden Yellow, Particles: `#E5B409`)
- **Sine Spline Physics Engine**: 2단계에서 화면 전역 손길에 반응하는 부드러운 스플라인 탄성 엔진.

---

## 📁 4. 프로젝트 파일 구성 및 크레딧
- `index.html`: **단일 통합 메인 애플리케이션 (`Odysseus's Bow`)**
- `pluck.mp3`, `bow_1.mp3`, `bow_2.mp3`: 사운드 리소스 파일 (Sound effects created via [ElevenLabs](https://elevenlabs.io/))
- `PROJECT.md`: 통합 개발 기록 문서
- `README.md`: 사용자 안내 가이드 문서
