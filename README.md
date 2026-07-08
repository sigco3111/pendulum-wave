# 🕰️ pendulum-wave

> Three.js 기반 펜듈럼 웨이브(Pendulum Wave) 3D 시뮬레이션 — 15개 추의 주기 차이로 인한 위상 동기/비동기 현상

각기 다른 줄 길이를 가진 15개의 추가 일렬로 매달려 동시에 흔들리기 시작하면, 처음에는 뱀처럼(Wave) 정렬된 패턴으로 움직이다가 점차 위상이 어긋나 혼돈스러워 보이고, 충분히 긴 시간이 지나면 다시 질서를 찾는 펜듈럼 웨이브 현상을 물리적으로 정확한 주기 공식을 적용해 3D로 시각화합니다.

---

## 🤖 생성 정보

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**됩니다.

| 항목 | 값 |
|---|---|
| **모델** | minimax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/pendulum-wave`](https://github.com/sigco3111/pendulum-wave) |
| **상태** | 🚧 bootstrap 단계 — README 초기화 완료, 본 코드는 OpenCode CLI에서 생성 예정 |

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

## 🧠 배경 지식

펜듈럼 웨이브는经典的 Harvard Natural Sciences Lecture Demonstration 으로 잘 알려진 현상입니다. 15개 추의 줄 길이 $L_i$가 다음 조건을 만족하도록 설계되면, $T$초 주기로 정확히 같은 위상으로 돌아옵니다:

$$L_i = g \left(\frac{T}{2\pi (N + i)}\right)^2 \quad (i = 0, 1, \dots, 14)$$

여기서:
- $g$ ≈ 9.81 m/s² (중력 가속도)
- $N$ = 기준 진동수 (보통 20~50)
- $T$ = 전체 사이클 주기 (보통 30~60초)

이때 각 추의 각도는 단순 조화 운동(SHM)으로 정확히 계산됩니다:

$$\theta_i(t) = \theta_{\max} \cos\left(\sqrt{\frac{g}{L_i}} \cdot t\right)$$

저장소에는 위 공식을 그대로 구현한 Three.js 시뮬레이션이 단일 HTML 파일로 포함될 예정입니다.

---

## 🚀 실행 방법 (예정)

코드가 추가된 후:

```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

또는 로컬 서버:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 **minimax-M3** 모델과 **OpenCode CLI** 환경에서 생성됩니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.