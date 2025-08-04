
## 프로젝트 소개

**PBRT Bathroom Renderer**는 [PBRT v3](https://pbrt.org/)의 `bathroom.pbrt` 씬을 레퍼런스로 삼아,
**Vulkan의 RTX 기능**을 활용해 **GPU 기반 Path Tracing**으로 렌더링한 프로젝트입니다.

Vulkan Ray Tracing Extension을 직접 사용하여, **재질, 조명, 반사, 투과** 등을 **물리 기반 모델**로 구현했습니다.

---

## 주요 기능

* **PBRT v3 포맷 기반 씬 로딩**

  * `bathroom.pbrt` 구조에 맞춰 **재질, 텍스처, 지오메트리 파싱**
* **Vulkan RTX 기반 Path Tracing 엔진**

  * Ray Generation / Closest Hit / Miss 셰이더 구성
  * **다중 바운스 반사 경로 추적**
* **Microfacet BRDF 및 Fresnel 모델 구현**

  * GGX 분포, Smith G, Schlick Fresnel 기반
* **Next Event Estimation (NEE)**

  * Area Light 샘플링 및 **Multiple Importance Sampling(MIS)** 적용

---

## Rendering Results

| Reference (PBRT v3)                          | Vulkan RTX Path Tracing                  |
| -------------------------------------------- | ---------------------------------------- |
| ![Reference](/images/bathroom_reference.jpg) | ![Rendered](/images/bathroom_result.PNG) |

---

## 카메라 조작 및 SPP 누적 방식

* `W`, `A`, `S`, `D` 키로 **자유롭게 카메라 이동**
* **마우스 왼쪽 클릭 후 드래그**로 시점 회전
* `R` 키로 **레퍼런스 카메라 시점**으로 복귀
* **움직임이 감지되면 SPP (Samples Per Pixel)가 초기화**되고,
  **정지 상태에서는 프레임이 누적**되어 결과가 점점 정제됨

> **정지 상태로 오래 기다릴수록 더 깨끗한 이미지를 얻을 수 있습니다.**

![move](/images/move.gif)

---

## 더 알아보기

자세한 구현 과정과 렌더링 이론 정리는 블로그에서 확인할 수 있습니다:
[https://surkim.tistory.com/132](https://surkim.tistory.com/132)

---
