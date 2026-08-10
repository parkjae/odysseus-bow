# 🏹 Odysseus's Bow

> **Odysseus's Bow**는 활시위를 거는 **"STRING A BOW"** 시퀀스와, 활시위를 튕겨 연주하는 **"PLUCK A BOW"** 시퀀스로 구성된 단일 통합 웹 인터랙티브 애플리케이션(`index.html`)입니다.

---

## ✨ 웹앱 시퀀스 안내

### 1단계: 🏹 STRING A BOW (활시위 걸기)
- **개념**: 화면 하단 90% 지점(`height * 0.9`)에 위치한 하얀 링(Ring)을 마우스나 손가락으로 잡고 **상단 20% 지점(`height * 0.2`)의 하얀 점(Target Dot)**까지 끌어 올려 활시위를 겁니다.
- **안내 문구**: *"활 시위를 걸어보세요"*
- **사운드 트리거**:
  - **1/5 지점 (20%)** 통과 시: `bow_1.mp3` 사운드 재생 🎵
  - **3/5 지점 (60%)** 통과 시: `bow_2.mp3` 사운드 재생 🎶
- **목적지 완결 & 자동 전환**:
  - 링이 상단 목적지에 딱 멈춘 후 사운드 재생이 완결되면 자동으로 아름다운 황금 활시위 단계로 전환됩니다.

### 2단계: 🎻 PLUCK A BOW (황금 활시위 연주)
- **개념**: 활시위 걸기에 성공하면 화면이 부드럽게 전환되며 **고급스러운 노란 황금빛 현(String, `#E5B409`)**이 나타납니다.
- **전역 터치 조작 (Fullscreen Drag)**: 화면 전체 어디든 손가락이나 마우스로 잡고 좌우로 움직여 당겼다 놓으면 아름다운 황금 이펙트 입자와 함께 `pluck.mp3` 소리가 연주됩니다.
- **안내 문구**: *"활 시위를 당겨 보세요"*
- **사운드**: `pluck.mp3` 사운드 연주.
- **🔄 Reload (다시 활시위 걸기로 돌아가기)**:
  - 우측 하단의 **새로고침(Reload) 버튼**을 누르면 언제든 초기 **"STRING A BOW"** 단계로 되돌아갑니다.

---

## 🌐 웹 라이브 실행 주소

별도의 설치나 서버 실행 없이 아래 **GitHub Pages 라이브 주소**로 접속하시면 PC 및 모바일 스마트폰에서 즉시 플레이할 수 있습니다:

👉 **[https://parkjae.github.io/odysseus-bow/](https://parkjae.github.io/odysseus-bow/)**

---

## 🎵 Credits & Acknowledgments
- Sound effects created via [ElevenLabs](https://elevenlabs.io/)
