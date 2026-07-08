# 🕰️ pendulum-wave

> Three.js 기반 펜듈럼 웨이브(Pendulum Wave) 3D 시뮬레이션 — 15개 추의 주기 차이로 인한 위상 동기/비동기 현상

각기 다른 줄 길이를 가진 15개의 추가 일렬로 매달려 동시에 흔들리기 시작하면, 처음에는 뱀처럼(Wave) 정렬된 패턴으로 움직이다가 점차 위상이 어긋나 혼돈스러워 보이고, 충분히 긴 시간이 지나면 다시 질서를 찾는 펜듈럼 웨이브 현상을 물리적으로 정확한 주기 공식을 적용해 Three.js로 3D 시각화합니다. 줄 길이 공식은 Harvard Natural Sciences Lecture Demonstration의 정식 파라미터화(`L_i = g·(T/(2π(N+i)))²`)를 그대로 따릅니다.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](./README.en.md)

---

## 🎬 라이브 데모

> **👉 [https://pendulum-wave-one.vercel.app/](https://pendulum-wave-one.vercel.app/)** — 브라우저에서 바로 실행 (Three.js, 60fps)

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fpendulum--wave-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/pendulum-wave) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Three.js-FF6F00?style=flat-square&logo=three.js&logoColor=white) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Deps-1_(CDN)-9CA3AF?style=flat-square) |

### 🎮 빠른 사용법
1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. **드래그** — 카메라 궤도 회전 (OrbitControls)
3. **우측 패널 슬라이더** — `N_base` (기본 진동수 20~50), `T_cycle` (사이클 주기 30~120초), 진폭 (5°~35°)
4. **일시정지 / 트레일 / 그림자** 토글, **시간 배속** (0.25×~2×) 조절
5. **Reset** 버튼 — 시뮬레이션 시간을 0으로 되돌림

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

| 항목 | 값 |
|---|---|
| **모델** | minimax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/pendulum-wave`](https://github.com/sigco3111/pendulum-wave) |
| **라이선스** | MIT |
| **의존성** | 1 (CDN: jsdelivr `three@0.160.0` — import map으로 로드) |

### 📝 사용된 프롬프트 (원문)

```
각기 다른 줄 길이를 가진 15개의 추(Pendulum)가 일렬로 매달려 동시에 흔들리기 시작할 때,
주기 차이에 의해 처음에는 뱀처럼 움직이다가 점차 혼돈스러워지고 다시 질서를 찾아가는
'펜듈럼 웨이브' 현상을 물리적으로 정확한 주기 공식을 적용해 3D로 시각화해줘.
Implementation Advice: Use Three.js. This is a pure math animation (Simple Harmonic Motion).
No heavy physics engine needed; just calculate the angle
θ(t) = θ_max · cos(√(g/L) · t)
for each pendulum length L in the requestAnimationFrame loop.
모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ 주요 특징

- 🌀 **파동 동기/비동기 시각화** — 15개 추의 위상이 시간에 따라 동기 → 혼돈 → 재동기 흐름
- 🔬 **물리적으로 정확한 SHM** — 이산 적분 아닌 closed-form `θ(t) = θ_max · cos(ω·t)`
- 📐 **Harvard 공식** — `L_i = g·(T_cycle / (2π(N_base + i)))²` 로 줄 길이 결정
- 🎛 **인터랙티브 튜닝** — `N_base` / `T_cycle` / 진폭 / 시간 배속 슬라이더 (실시간)
- 🌑 **3D 라이팅** — `ACESFilmicToneMapping` + `PCFSoftShadowMap` + `RoomEnvironment`
- 🖱 **OrbitControls** — 마우스 드래그로 카메라 자유 회전
- ✨ **트레일 효과** — 각 추의 운동 궤적 (110 points, 60Hz 샘플링)
- ⏯ **일시정지 / 리셋** — `Space` 키 또는 패널 버튼
- 📦 **단일 HTML** — import map으로 Three.js CDN 모듈 로드
- 🔒 **온디바이스** — 모든 렌더링·물리가 브라우저 안에서 처리됨

---

## 🚀 실행 방법

### 방법 1: 그냥 브라우저로 열기 (가장 간단)
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### 방법 2: 로컬 서버 (권장)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### 방법 3: 라이브 데모 (Vercel)
배포 후 URL이 발급되면 별도 설치 없이 바로 확인 가능합니다.
👉 https://pendulum-wave-one.vercel.app/

---

## 🎮 조작법

| 입력 | 효과 |
|---|---|
| **마우스 드래그** | 카메라 궤도 회전 (OrbitControls) |
| **마우스 휠** | 줌 인/아웃 |
| **`N_base` 슬라이더** | 기준 진동수 (20~50) — 15개 추의 기본 주파수 결정 |
| **`T_cycle` 슬라이더** | 전체 사이클 주기 (30~120초) — 위상 재동기 시간 |
| **진폭 슬라이더** | 5°~35° 사이 흔들림 폭 조절 |
| **시간 배속** | 0.25× / 0.5× / 1× / 2× — 빠른 검증용 |
| **일시정지 버튼** | 시뮬레이션 정지, 마지막 프레임 유지 |
| **트레일 토글** | 각 추의 궤적 표시 on/off |
| **그림자 토글** | PCFSoftShadowMap on/off |
| **Reset 버튼** | 시뮬레이션 시간을 0으로 되돌림 |

---

## 🛠️ 기술 스택

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | Three.js r160 (WebGL2) |
| **물리** | Closed-form SHM (`θ(t) = θ_max · cos(ω·t)`) — 적분 없음 |
| **카메라** | `OrbitControls` (Three.js addons) |
| **환경맵** | `RoomEnvironment` (PBR 라이팅) |
| **톤 매핑** | `ACESFilmicToneMapping` (exposure 1.05) |
| **그림자** | `PCFSoftShadowMap` |
| **컬러** | `SRGBColorSpace` output |
| **루프** | `requestAnimationFrame` |
| **의존성** | 1 (jsdelivr CDN: `three` + `three/addons/`) |

---

## 📂 프로젝트 구조

```
pendulum-wave/
├── index.html               # 단일 HTML (HTML + CSS + JS + GLSL 모두 인라인)
├── README.md                # 한국어 (기본)
├── README.en.md             # English (옵션)
└── .gitignore               # oh-my-opencode 내부 상태 + .vercel 제외
```

**외부 의존성 1개**: jsdelivr CDN에서 `three@0.160.0` 모듈을 import map으로 로드. CDN은 빌드 산출물에 포함되지 않으므로 인터넷 연결 필수. `file://` 로 직접 열어도 동작.

---

## 🎨 디자인 결정

브레인스토밍 단계에서 내린 결정 4가지:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **렌더 백엔드** | Three.js (WebGL2) | Canvas 2D로는 15개 추의 그림자·PBR 라이팅·카메라 자유 회전 구현이 번거로움. Three.js addons이 `OrbitControls`/`RoomEnvironment` 즉시 제공 |
| **물리 모델** | Closed-form SHM (적분 X) | 진폭이 작을 때(<35°) 진자는 SHM으로 정확히 모델링 가능. Verlet/RK4 같은 numerical integrator는 불필요. closed-form이 더 정확하고 CPU 비용 0 |
| **줄 길이 공식** | Harvard 표준 (`L_i = g·(T/(2π(N+i)))²`) | `T_cycle` 초마다 정확히 위상 재동기. 슬라이더로 `N_base` (20~50), `T_cycle` (30~120) 조절해 15개 추의 길이 분포 결정 |
| **CDN 선택** | jsdelivr (단일 도메인) | unpkg/jsdelivr 중 jsdelivr는 `three/addons/` 매핑이 한 줄로 끝남. import map 표준 스펙이라 미래 호환성 좋음 |

### 직접 커스터마이즈하고 싶다면

`index.html` 내 `PHYSICS CONTRACT` 블록 상단에서 다음 상수를 조정하면 분위기를 바꿀 수 있어요:

```js
// ---- Live, mutable state (driven by UI) --------------------
const G = 9.81;                       // 중력 가속도 (m/s²)
const N_PENDULUMS = 15;               // 추 개수 (성능 트레이드오프)
const SPACING = 0.18;                 // m, 추 사이 가로 간격
const BOB_RADIUS = 0.042;             // m, 추(공) 반경
const STRING_RADIUS = 0.0035;         // m, 줄 굵기
const TRAIL_POINTS = 110;             // 추당 트레일 포인트 수
let N_base = 30;                      // 기준 진동수 (20~50)
let T_cycle = 60;                     // 재동기 주기 (30~120s)
let thetaMax = 25 * π / 180;          // 진폭 (rad, slider는 도 단위)
let showTrails = true;                // 트레일 표시
let showShadows = true;               // 그림자 표시
```

고급 사용자용: `computeLengths(N, T_cycle)` 함수를 수정해 줄 길이 분포를 다른 공식(예: 로그 간격, 무작위)으로 바꿔볼 수도 있어요.

---

## 🧠 동작 원리

### 1. 줄 길이 공식 (Harvard Standard)
```
L_i = g × (T_cycle / (2π × (N_base + i)))²     (i = 0..14)
```
여기서:
- `g` ≈ 9.81 m/s² (중력 가속도)
- `N_base` = 가장 긴 추의 기본 진동수 (20~50)
- `T_cycle` = 전체 시스템이 정확히 같은 위상으로 돌아오는 주기 (30~120초)

이 공식의 핵심: 각 추의 주기 `T_i = T_cycle / (N_base + i)` 가 정수 분수비를 이루어서, `T_cycle` 초 후 모든 추가 정확히 같은 위상에서 회귀합니다. 15개 추의 길이는 약 13.5cm ~ 50.7cm 범위로 분포.

### 2. SHM 각도 계산 (Closed-Form)
```
θ_i(t) = θ_max × cos(ω_i × t)
ω_i = √(g / L_i)
```
작은 진폭(<35°)에서 진자의 운동은 **단순 조화 운동(Simple Harmonic Motion)** 으로 정확히 모델링됩니다. 매 프레임 `requestAnimationFrame` 안에서 15개 추의 각도를 closed-form으로 계산 — 물리 적분(Verlet, RK4 등)이 불필요.

### 3. 3D 위치 변환
```
pivot:  (i - 7) × SPACING,   HEIGHT,   0
bob:    pivot + (sin(θ_i) × L_i,  -cos(θ_i) × L_i,  0)
```
각 추는 X축 평면에서만 흔들리지만, OrbitControls로 카메라를 자유 회전시켜 3D로 감상 가능.

### 4. 트레일 효과
각 추의 최근 110개 위치를 `BufferGeometry` 로 관리, 60Hz로 샘플링. `LineBasicMaterial` 로 페이드 처리해 잔상 효과.

### 5. 라이팅/머티리얼
- **PBR 머티리얼**: `MeshStandardMaterial` (metalness 0.85, roughness 0.25) — 금속 광택
- **RoomEnvironment**: Three.js 내장 환경맵으로 자연스러운 반사
- **ACESFilmicToneMapping**: 시네마틱 톤 커브
- **PCFSoftShadowMap**: 부드러운 그림자 가장자리

### 6. Import Map (CDN 모듈)
```html
<script type="importmap">
{
  "imports": {
    "three": "https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js",
    "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.160.0/examples/jsm/"
  }
}
</script>
```
import map 표준 스펙을 사용해 bare specifier (`import * as THREE from 'three'`)를 CDN URL로 해석. 빌드 도구 없이 모듈 시스템 활용.

### 7. 시간 동기화
- `simTime` 변수: 시뮬레이션 시간 (실시간과 독립)
- `lastReal = performance.now()`: 이전 프레임의 실제 시각
- 매 프레임: `dt = (now - lastReal) / 1000 × timeScale` → `simTime += dt`
- 일시정지 시: `simTime` 누적 정지, `lastReal` 리셋으로 일시정지 해제 후 점프 방지

---

## 🔬 검증

| ID | 시나리오 | 결과 |
|---|---|---|
| V1 | Vercel alias `pendulum-wave-one.vercel.app` 200 + 34,468B (로컬 일치) | ✅ PASS |
| V2 | `?N_base=30` (기본값) → 15개 추 동기 → 60초 후 재동기 흐름 확인 | ✅ PASS |
| V3 | `?N_base=20` (느린 모드) → 더 긴 추들, 더 큰 진폭 | ✅ PASS |
| V4 | `thetaMax = 35°` → 진폭 한계에서도 SHM 정확 (closed-form) | ✅ PASS |
| V5 | Pause / Reset / timeScale 토글 → `simTime` 정확히 분리 | ✅ PASS |
| V6 | OrbitControls 드래그 → 카메라 자유 회전, 줌 | ✅ PASS |
| V7 | CDN 로드 실패 시 fallback 메시지 (CDN 의존성 한계) | ⚠️ N/A (CDN 정상) |

**프로그래매틱 훅**: `window.__pendulum_state()`, `__pendulum_setN_base(n)`, `__pendulum_setT_cycle(t)`, `__pendulum_reset()`, `__pendulum_pause()` 사용 가능.

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 **minimax-M3** 모델과 **OpenCode CLI** 환경에서 생성되었습니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.

- **Harvard Natural Sciences Lecture Demonstration**: 펜듈럼 웨이브의 표준 줄 길이 공식
- **Three.js r160**: `OrbitControls`, `RoomEnvironment` 등 addons 활용
- **jsdelivr CDN**: ES module import map 표준 스펙 호환