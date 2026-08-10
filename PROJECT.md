# Odysseus's Bow - 통합 개발 기록 (PROJECT.md)

## 📌 1. 프로젝트 개요
- **앱 명칭**: **Odysseus's Bow**
- **라이브 웹 주소**: [https://parkjae.github.io/odysseus-bow/](https://parkjae.github.io/odysseus-bow/)
- **주요 목적**:
  - `index.html`: 활시위를 거는 **"STRING A BOW"** 단계와, 활시위를 튕겨 연주하는 **"PLUCK A BOW"** 단계를 연결한 인터랙티브 웹 애플리케이션.
  - **시퀀스 구조**:
    1. **"STRING A BOW" (Scene 1)**: 하단 90% 지점(`height * 0.9`)의 링(Ring)을 상단 20% 지점(`height * 0.2`) 하얀 점(Target)까지 끌어 올려 활시위를 검 (가이드: *"활 시위를 걸어보세요"*, **1/5 지점(20%)**: `bow_1.mp3`, **3/5 지점(60%)**: `bow_2.mp3` 재생). 목적지 도달 시 링이 멈추고 사운드 완결 후 `Scene 2`로 자동 전환.
    2. **"PLUCK A BOW" (Scene 2)**: 활시위를 거는 데 성공하면 완결과 함께 **고급스러운 노란색(`#E5B409`) 황금 활시위**로 전환되어 `pluck.mp3` 연주 (가이드: *"활 시위를 당겨 보세요"*).
    3. **Reload 기능**: Scene 2 우측 하단 새로고침 버튼으로 언제든 초기 **"STRING A BOW"** 단계로 복귀 가능.

---

## 🛠️ 2. 색상 및 테마 디자인 사양

### 2.1 Color Palette & Physics
- **Scene 1 (STRING A BOW)**: 미니멀 순백색 (`#FFFFFF`, Glow: White)
- **Scene 2 (PLUCK A BOW)**: 신화적 황금색 (**`#E5B409`**, Glow: Golden Yellow, Particles: `#E5B409`)
- **Sine Spline Physics Engine**: 2단계에서 화면 전역 손길에 반응하는 부드러운 스플라인 탄성 엔진 구현.

---

## 📁 3. 프로젝트 파일 구성 및 크레딧

- `index.html`: **단일 통합 메인 애플리케이션 (`Odysseus's Bow`)**
- `pluck.mp3`, `bow_1.mp3`, `bow_2.mp3`: 사운드 리소스 파일 (Sound effects created via [ElevenLabs](https://elevenlabs.io/))
- `PROJECT.md`: 기술 및 개발 기록 문서
- `README.md`: 사용자 가이드 문서 (GitHub Pages 라이브 주소 및 ElevenLabs 크레딧 탑재)
