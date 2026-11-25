<!-- portfolio-cover-v1 -->
# STC — Skin Tension Constraint

**삼각형 면적 기반 피부 인장 제약 | GPU-based soft tissue simulation**

![C++17](https://img.shields.io/badge/C%2B%2B17-25292e?style=flat-square) ![CUDA](https://img.shields.io/badge/CUDA-25292e?style=flat-square) ![PBD](https://img.shields.io/badge/PBD-25292e?style=flat-square) ![Qt 6](https://img.shields.io/badge/Qt%206-25292e?style=flat-square) ![OpenGL](https://img.shields.io/badge/OpenGL-25292e?style=flat-square)

2025 · 석사 연구 · 제1저자 논문

[**Portfolio ↗**](https://soz1p.github.io/jeon-sojin-portfolio/#projects)

기존 PBD의 거리·부피 제약만으로 충분히 표현하기 어려운 절개 주변 피부 인장 반응을 삼각형 면적 기반 제약으로 근사합니다.

<p align="center"><img src="images/stc-figure5.jpg" alt="STC — Skin Tension Constraint — project preview" width="460"></p>
<p align="center"><sub>2025년 게재 논문 Figure 5 · STC 미적용 / 적용 비교 (기존 연구 결과)</sub></p>

## Highlights

| 제1저자 | 3개 CT 데이터셋 | +3.23–7.66% |
| :---: | :---: | :---: |
| 2025 학술지 논문 | 적용 전후 비교 | 병렬 리샘플링 시간 증가율 |

**Pipeline:** CT density → Surface detection → STC projection → Volume visualization

위 수치는 2025년 게재 논문의 측정값입니다. 

## My Contributions

피부 표면 탐지와 면적 기반 인장 제약의 설계·구현, CUDA PBD 파이프라인 통합 및 비교 실험. 공동 연구이며 기반 시스템 전체의 단독 개발을 의미하지 않습니다.

## Research

**STC: A Skin Tension Constraint Model for Position-Based Dynamics**  
전소진 · 서지완 · 계희원  
한국컴퓨터그래픽스학회 논문지 31(4), 21–31, 2025.

[Paper PDF](papers/stc-2025.pdf) · [KCI · Published paper](https://www.kci.go.kr/kciportal/landing/article.kci?arti_id=ART003238324)  
DOI: 10.15701/kcgs.2025.31.4.21

## Approach

- CT 밀도와 전달 함수를 이용해 공기 정점을 분류하고 피부 표면 삼각형을 탐지합니다.
- 삼각형의 기준 면적과 현재 면적의 차이를 기반으로 피부 인장 반응을 표현합니다.
- 기존 CUDA 제약 그룹 실행 구조에 통합하여 적용 전후의 절개 형상과 병렬 리샘플링 시간을 비교합니다.

## Results

| PBD resolution | STC OFF (ms) | STC ON (ms) | Increase |
| --- | ---: | ---: | ---: |
| 129×129×76 | 74.06 | 79.73 | 7.66% |
| 129×129×138 | 126.52 | 131.89 | 4.24% |
| 129×129×289 | 257.75 | 266.08 | 3.23% |

2025년 게재 논문 Table 4. NVIDIA GeForce RTX 3090, 연속 10프레임 평균. 전체 시스템 FPS의 변화율을 의미하지 않습니다.

## Source Availability

연구실 및 공동 연구의 소스코드는 공개하지 않습니다. 이 페이지는 연구 소개와 공개된 논문 정보를 제공하는 포트폴리오입니다.

## Discussion

절개 형상의 정성 비교를 통해 면적 기반 제약의 적용 가능성을 확인했습니다. 조직의 실측 물성과의 일치, 임상적 정확도 및 다양한 절개 조건에 대한 일반화는 별도 검증 과제입니다.

## Paper License

논문: 전소진 · 서지완 · 계희원 (2025), 한국컴퓨터그래픽스학회 논문지 31(4), 21–31. KCI에 명시된 [CC BY-NC 3.0](https://creativecommons.org/licenses/by-nc/3.0/) 조건에 따라 원문 PDF를 변경 없이 제공합니다. 비교 이미지는 해당 논문 Figure 5입니다. 이 조건은 연구실 소스코드의 공개 허가를 의미하지 않습니다.
