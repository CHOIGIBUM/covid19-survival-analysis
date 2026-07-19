<div align="center">

# COVID-19 생존율 분석

<p>
  <strong>한국어</strong> · <a href="./README.en.md">English</a>
</p>

**비만과 기저질환에 따른 생존분포를 비교하고,  
공변량을 함께 고려해 사망위험과의 관련성을 분석한 프로젝트**

![Event](https://img.shields.io/badge/2024-COMPASS%20Hackathon-147C8A)
![Data](https://img.shields.io/badge/Data-Synthetic%20Clinical%20Data-5A8F99)
![Analysis](https://img.shields.io/badge/Analysis-Kaplan--Meier%20%7C%20Cox-0C4F5A)
![Award](https://img.shields.io/badge/Award-Encouragement%20Award-C5962A)

<br/>

<img
  src="./assets/overview/covid19-survival-analysis.png"
  width="100%"
  alt="COVID-19 생존율 분석 프로젝트 개요"
/>

<sub>
프로젝트의 분석 흐름을 요약한 개요 도식입니다. 실제 분석 결과는 아래 발표자료 기반 그래프에서 확인할 수 있습니다.
</sub>

<br/><br/>

<a href="./materials/2024-compass-hackathon-poster.pdf">
  <img src="https://img.shields.io/badge/포스터-보기-147C8A?style=for-the-badge" alt="포스터 보기" />
</a>
<a href="./materials/2024-compass-hackathon-presentation.pdf">
  <img src="https://img.shields.io/badge/발표자료-보기-147C8A?style=for-the-badge" alt="발표자료 보기" />
</a>
<a href="./materials/2024-compass-hackathon-award.pdf">
  <img src="https://img.shields.io/badge/상장-보기-C5962A?style=for-the-badge" alt="상장 보기" />
</a>
<a href="https://www.veritas-a.com/news/articleView.html?idxno=528804">
  <img src="https://img.shields.io/badge/행사%20보도-보기-5E6E73?style=for-the-badge" alt="행사 보도 보기" />
</a>

</div>

---

## 🧭 연구 개요

COVID-19 감염 환자에서 비만과 기저질환이 생존분포와 어떤 관련을 보이는지 분석했습니다. 고혈압, 만성 신장질환, 만성 부비동염과 대사증후군 X를 중심으로 집단별 생존곡선을 비교하고, 연령·성별·인종·비만 여부와 기저질환을 함께 고려했을 때 어떤 변수가 사망위험과 관련되는지 살펴보았습니다.

단변량 생존분석에서는 집단 간 생존분포의 차이를 확인했으며, 이후 Cox 비례위험모형을 적용해 여러 변수를 함께 고려한 뒤에도 관련성이 유지되는지를 분석했습니다.

<p align="center">
  <img
    src="./assets/study/research-background.png"
    width="100%"
    alt="COVID-19 생존율 분석의 연구 배경과 목표"
  />
</p>

---

## ❓ 연구 질문

1. 비만 여부로 환자군을 층화했을 때, 각 층에서 기저질환 유무에 따른 생존분포는 다르게 나타나는가?
2. 연령, 성별, 인종, 비만 여부와 여러 기저질환을 함께 고려한 뒤에도 사망위험과 관련되는 변수가 남는가?

---

## 👥 데이터와 코호트

분석에는 해커톤 당시 COMPASS 플랫폼을 통해 제공된 합성 임상데이터를 사용했습니다. COVID-19 감염 여부와 생존·사망 상태가 기록되어 있고, 주요 인구통계학적 변수와 비만 및 기저질환 정보를 확인할 수 있는 환자를 분석 대상으로 구성했습니다.

주요 변수는 다음과 같습니다.

- **인구통계학적 정보:** 연령, 성별, 인종
- **비만:** BMI 30 이상 여부
- **기저질환:** 고혈압, 만성 신장질환, 만성 부비동염, 대사증후군 X
- **결과 변수:** 생존 또는 사망 상태

<p align="center">
  <img
    src="./assets/study/cohort-definition.png"
    width="100%"
    alt="COVID-19 생존율 분석의 코호트 정의"
  />
</p>

---

## 🧪 분석 방법

먼저 비만 여부에 따라 환자군을 층화한 뒤, 각 층에서 해당 기저질환의 유무에 따른 Kaplan–Meier 생존곡선을 비교했습니다. 이 분석을 통해 집단별 생존분포가 서로 다른지를 확인했습니다.

Kaplan–Meier 곡선에서 관찰된 차이가 다른 변수들을 함께 고려한 뒤에도 유지되는지를 확인하기 위해 Cox 비례위험모형을 적용했습니다. 모형에는 연령, 성별, 인종, 비만 여부와 네 가지 기저질환을 함께 포함했습니다.

```text
COVID-19 감염 환자
        ↓
비만 여부로 환자군 층화
        ↓
각 층에서 기저질환 유무별
Kaplan–Meier 생존곡선 비교
        ↓
연령·성별·인종·비만·기저질환을 포함한
Cox 비례위험모형 적용
```

---

## 📊 분석 결과

### Kaplan–Meier 생존분석

네 기저질환 분석에서 생존곡선 차이에 대한 log-rank 검정 결과가 모두 통계적으로 유의하게 나타났습니다. 아래 이미지는 당시 발표자료에 제시한 Kaplan–Meier 생존곡선입니다.

<table>
  <tr>
    <td width="50%" align="center">
      <img
        src="./assets/results/km-chronic-kidney-disease.png"
        width="100%"
        alt="만성 신장질환 Kaplan–Meier 생존분석 결과"
      />
      <br/>
      <sub>만성 신장질환</sub>
    </td>
    <td width="50%" align="center">
      <img
        src="./assets/results/km-chronic-sinusitis.png"
        width="100%"
        alt="만성 부비동염 Kaplan–Meier 생존분석 결과"
      />
      <br/>
      <sub>만성 부비동염</sub>
    </td>
  </tr>
  <tr>
    <td width="50%" align="center">
      <img
        src="./assets/results/km-hypertension.png"
        width="100%"
        alt="고혈압 Kaplan–Meier 생존분석 결과"
      />
      <br/>
      <sub>고혈압</sub>
    </td>
    <td width="50%" align="center">
      <img
        src="./assets/results/km-metabolic-syndrome-x.png"
        width="100%"
        alt="대사증후군 X Kaplan–Meier 생존분석 결과"
      />
      <br/>
      <sub>대사증후군 X</sub>
    </td>
  </tr>
</table>

<details>
<summary><strong>질환별 log-rank 검정 결과 보기</strong></summary>

| 기저질환 | p-value |
|:---|---:|
| 만성 신장질환 | 2.904986e-13 |
| 만성 부비동염 | 1.474284e-09 |
| 고혈압 | 2.411282e-37 |
| 대사증후군 X | 3.806251e-17 |

</details>

### Cox 비례위험모형

연령, 성별, 인종, 비만 여부와 네 기저질환을 함께 고려한 결과, **연령과 고혈압은 사망위험과 통계적으로 유의한 관련성을 보였습니다.** 반면 비만 여부는 다른 변수들을 함께 고려한 뒤에는 유의한 변수로 유지되지 않았습니다.

<p align="center">
  <img
    src="./assets/results/cox-model-summary.png"
    width="100%"
    alt="Cox 비례위험모형 결과"
  />
</p>

<details>
<summary><strong>주요 Cox 모형 결과 보기</strong></summary>

| 변수 | Hazard Ratio | 95% CI | p-value |
|:---|---:|---:|---:|
| 고혈압 | 5.481 | 3.089–9.725 | 6.06e-09 |
| 연령 1년 증가 | 1.066 | 1.053–1.079 | 4.58e-26 |
| 비만 여부 | 1.093 | 0.674–1.773 | 0.719 |

</details>

---

## 🔍 결과 해석

Kaplan–Meier 분석에서는 집단별 생존곡선의 차이가 뚜렷하게 나타났지만, 여러 변수를 함께 고려한 Cox 모형에서는 비만 여부의 유의성이 유지되지 않았습니다.

따라서 생존곡선에서 관찰된 집단 차이와, 연령이나 다른 기저질환을 함께 고려한 뒤에도 유지되는 관련성은 구분해서 해석할 필요가 있습니다. 이 분석에서는 단변량 결과를 그대로 결론으로 받아들이기보다 공변량을 함께 고려한 결과와 비교해 해석했습니다.

분석에는 합성 임상데이터를 사용했으며, 결과는 관찰된 통계적 관련성의 범위에서 정리했습니다.

---

## 📎 프로젝트 자료

| 자료 | 링크 | 내용 |
|:---|:---|:---|
| 포스터 | [2024 COMPASS 해커톤 포스터](./materials/2024-compass-hackathon-poster.pdf) | 연구 질문, 코호트, 분석 방법과 주요 결과 |
| 발표자료 | [2024 COMPASS 해커톤 발표자료](./materials/2024-compass-hackathon-presentation.pdf) | Kaplan–Meier 생존분석과 Cox 모형 결과 |
| 상장 | [장려상 상장](./materials/2024-compass-hackathon-award.pdf) | 팀 `Insight_'AI'_chemists` 장려상 |
| 행사 보도 | [베리타스알파 기사](https://www.veritas-a.com/news/articleView.html?idxno=528804) | 2024 COMPASS 해커톤 개최 및 운영 관련 기사 |

---

## 🤝 팀과 역할

| 이름 | 역할 |
|:---|:---|
| **최기범** | 연구 질문 및 분석 방향 설정, 질환군 선정과 코호트 구성, 통계분석, 결과 해석 및 발표 |
| **한만규** | 공동 프로젝트 수행 |

<div align="center">

**Team `Insight_'AI'_chemists` · 2024 COMPASS 해커톤 장려상**

</div>

---

## © 자료 이용 범위

이 저장소에는 별도의 오픈소스 또는 Creative Commons 라이선스를 적용하지 않습니다.

별도로 표시하지 않은 경우, **직접 작성한 README와 자체 제작한 개요 도식·분석 그림**은 학술 포트폴리오 및 검토 목적으로 공개합니다. 자료의 재사용, 수정 또는 재배포가 필요한 경우 사전에 문의해 주세요.

원본 데이터는 이 저장소에 포함하지 않으며, 데이터 이용 권한은 제공기관의 이용조건을 따릅니다. 공동 제작 자료, 상장, 기관 로고, 기사 및 기타 제3자 콘텐츠는 위 이용 범위에서 제외되며 각 권리자와 제공기관의 조건을 따릅니다.
