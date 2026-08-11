# Odysseus's Bow - 통합 개발 기록 (PROJECT.md)

## 📌 1. 프로젝트 개요
- **앱 명칭**: **Odysseus's Bow**
- **라이브 웹 주소**: [https://parkjae.github.io/odysseus-bow/](https://parkjae.github.io/odysseus-bow/)
- **주요 목적**:
  - `index.html`: 활시위를 거는 **"STRING A BOW"** 단계와, 활시위를 튕겨 연주하는 **"PLUCK A BOW"** 단계를 연결한 인터랙티브 웹 애플리케이션.

---

## 🎼 2. 오디오 인터랙션 및 시퀀스 사양

### 2.1 오디오 세션 및 디바이스 호환성 (iOS Mute Override)
- **하이브리드 iOS AudioSession 승격**:
  - 최신 iOS 17+ API (`navigator.audioSession.type = 'playback'`)와 하위 호환 HTML5 무음 Audio Hack (`SILENT_WAV_BASE64`)을 동시 적용.
  - 아이폰의 하드웨어 무음 스위치가 켜진 상태에서도 미디어 재생 카테고리로 승격되어 사운드가 스피커로 출력됨.

### 2.2 음량(Volume) 및 피치(Pitch) 설정 사양
- **`bow_1.mp3` & `bow_2.mp3`**:
  - 활시위를 걸 때 발생하는 배경음의 음량을 **50% (`0.5`)** 수준으로 은은하게 축소 조절.
- **`pluck.mp3` (FOREPLAY 시퀀스)**:
  - 1차 Pluck: **원본 피치 (`1.0`)**, 100% 음량 (`1.0`)
  - 2차 Pluck: **반음 하향 (`Math.pow(2, -1/12)`)**, 100% 음량 (`1.0`), 1차 음 재생 1초(`1000ms`) 후 연속 연주.
- **`pluck.mp3` (Scene 2 메인 연주)**:
  - 변수명: **`MAIN_SEMITONES_DOWN_RATE`** (`Math.pow(2, -3/12)` = 단3도/3반음 하향)
  - 음량: **150% (`1.5`)**로 타격감 및 울림 증폭.

### 2.3 시퀀스 단계별 구조
1. **"STRING A BOW" (Scene 1)**:
   - 하단 90% 지점(`height * 0.9`)의 링(Ring)을 상단 20% 지점(`height * 0.2`) 하얀 점(Target)까지 끌어 올려 활시위를 검.
   - **20% (1/5 지점)**: `bow_1.mp3` (50% 볼륨)
   - **60% (3/5 지점)**: `bow_2.mp3` (50% 볼륨, `onended` 정밀 이벤트 연동)
2. **"FOREPLAY" (시퀀스 전환 서곡 연주)**:
   - `bow_2.mp3` 재생 완료(`onended`) 정밀 타이밍에 `pluck.mp3`를 **[1차: 원본 피치(1.0) ➔ (1초 후) 2차: 반음 다운]** 순서로 연주 후 Scene 2로 자동 전환.
3. **"PLUCK A BOW" (Scene 2)**:
   - 완결과 함께 **고급스러운 노란색(`#E5B409`) 황금 활시위**로 전환되어 자유 연주 (단3도 하향, 150% 볼륨).
4. **Reload 기능**:
   - Scene 2 우측 하단 버튼으로 언제든 초기 **"STRING A BOW"** 단계로 복귀 가능.

---

## 🛠️ 3. 색상 및 테마 디자인 사양
- **Scene 1 (STRING A BOW)**: 미니멀 순백색 (`#FFFFFF`, Glow: White)
- **Scene 2 (PLUCK A BOW)**: 신화적 황금색 (**`#E5B409`**, Glow: Golden Yellow, Particles: `#E5B409`)
- **Sine Spline Physics Engine**: 2단계에서 화면 전역 손길에 반응하는 부드러운 스플라인 탄성 엔진.

---

## 📁 4. 프로젝트 파일 구성 및 크레딧
- `index.html`: **단일 통합 메인 애플리케이션 (`Odysseus's Bow`)**
- `pluck.mp3`, `bow_1.mp3`, `bow_2.mp3`: 사운드 리소스 파일 (Sound effects created via [ElevenLabs](https://elevenlabs.io/))
- `PROJECT.md`: 통합 개발 기록 문서
- `README.md`: 사용자 안내 가이드 문서
