<div align="center">

# COVID-19 생존율 분석

**비만 및 기저질환과 생존 결과의 관련성 검토**

![Status](https://img.shields.io/badge/status-documentation%20archive-147C8A)
![Data](https://img.shields.io/badge/data-synthetic%20clinical%20data-5A8F99)
![Methods](https://img.shields.io/badge/methods-Kaplan--Meier%20%7C%20Cox-0C4F5A)
![Award](https://img.shields.io/badge/award-Encouragement%20Award-C5962A)

<br/>

<img src="./assets/overview/covid19-survival-analysis.png" width="100%" alt="COVID-19 생존율 분석 프로젝트 개요" />

<br/><br/>

<a href="./materials/2024-compass-hackathon-poster.pdf">
  <img src="https://img.shields.io/badge/Poster-View-147C8A?style=for-the-badge" alt="포스터 보기" />
</a>
<a href="./materials/2024-compass-hackathon-presentation.pdf">
  <img src="https://img.shields.io/badge/Presentation-View-147C8A?style=for-the-badge" alt="발표자료 보기" />
</a>
<a href="./materials/2024-compass-hackathon-award.pdf">
  <img src="https://img.shields.io/badge/Award-View-C5962A?style=for-the-badge" alt="상장 보기" />
</a>
<a href="https://www.veritas-a.com/news/articleView.html?idxno=528804">
  <img src="https://img.shields.io/badge/News-Event%20Coverage-5E6E73?style=for-the-badge" alt="행사 기사 보기" />
</a>

</div>

> [!NOTE]
> 이 저장소는 2024년 「COMPASS Platform 활용 임상-유전체 데이터분석 해커톤」에서 수행한 프로젝트를 정리한 **문서형 아카이브**입니다. 원본 데이터와 당시 분석 코드는 현재 보유하고 있지 않으며, 연구 설계와 결과는 당시 제작한 포스터와 발표자료를 기준으로 정리했습니다.

> [!IMPORTANT]
> 아래 결과는 합성 임상데이터에서 관찰된 통계적 관련성입니다. 인과관계나 실제 환자집단의 임상적 효과를 의미하지 않으며, 진단·치료 또는 위험평가의 근거로 사용할 수 없습니다.

---

## 🧭 프로젝트 개요

본 프로젝트는 COMPASS 플랫폼에서 제공된 합성 임상데이터를 이용해, COVID-19 감염 환자에서 **비만 여부와 기저질환이 생존 결과와 어떤 관련을 보이는지** 살펴본 2인 팀 프로젝트입니다.

각 기저질환에 대해 비만 여부로 환자군을 층화한 뒤, 각 층에서 해당 기저질환 유무에 따른 Kaplan–Meier 생존곡선을 비교했습니다. 이후 연령·성별·인종·비만 여부와 기저질환을 함께 고려한 Cox 비례위험모형을 적용했습니다.

| 항목 | 내용 |
|:---|:---|
| 원 프로젝트명 | COVID-19 감염 환자 생존율에 대한 비만 및 기저질환의 위험 요인 분석 |
| 행사 | 2024 COMPASS Platform 활용 임상-유전체 데이터분석 해커톤 |
| 팀 | `Insight_'AI'_chemists` — 최기범, 한만규 |
| 수행 형태 | 2인 팀 프로젝트 |
| 본인 역할 | 연구 질문·분석 방향 설정, 코호트 구성, 통계분석, 결과 해석 및 발표 |
| 수상 | 장려상 |
| 수행일 | 2024년 11월 9일 |
| 저장소 성격 | 당시 산출물을 바탕으로 정리한 문서형 아카이브 |

---

## 🎯 연구 질문

1. 비만 여부로 층화했을 때, 각 기저질환 유무에 따라 생존곡선이 달라지는가?
2. 연령·성별·인종·비만 여부와 기저질환을 함께 고려한 뒤에도 사망위험과 관련된 변수가 남는가?

---

## 🧪 분석 설계

```text
COVID-19 감염 환자 선정
          ↓
  비만 여부로 환자군 층화
          ↓
각 층에서 기저질환 유무별
Kaplan–Meier 생존곡선 비교
          ↓
Cox 비례위험모형을 이용한 보정 분석
```

### 분석에 사용한 정보

| 구분 | 변수 |
|:---|:---|
| 인구통계 | 연령, 성별, 인종 |
| 비만 | BMI 30 이상 여부 |
| 기저질환 | 만성 신장질환, 만성 부비동염, 고혈압, 대사증후군 X |
| 결과 | 생존·사망 상태 |

### Kaplan–Meier 생존분석

네 기저질환 각각에 대해 환자군을 비만 여부로 먼저 나누고, 각 비만 층에서 해당 기저질환 유무에 따른 Kaplan–Meier 생존곡선을 비교했습니다. 당시 자료에는 각 분석의 log-rank p-value가 보고되어 있습니다. 다만 원본 코드가 없어 p-value가 어떤 집단 대비를 기준으로 산출되었는지는 현재 다시 확인할 수 없습니다.

### Cox 비례위험모형

연령, 성별, 인종, 비만 여부와 네 기저질환을 함께 포함한 다변량 Cox 비례위험모형을 적용했습니다. 이 단계에서는 단변량 비교에서 관찰된 차이가 다른 변수들을 함께 고려한 이후에도 유지되는지를 확인했습니다.

---

## 📊 당시 보고된 결과

### 핵심 결과

| 분석 | 당시 자료에 보고된 내용 |
|:---|:---|
| Kaplan–Meier 비교 | 비만 여부로 층화한 네 기저질환 분석 모두에서 생존곡선 차이가 통계적으로 유의하게 보고됨 |
| Cox 비례위험모형 | 연령과 고혈압이 사망위험과 유의한 관련성을 보임 |
| 비만 여부 | 다른 변수들을 함께 고려한 뒤에는 유의한 변수로 유지되지 않음 |

### Kaplan–Meier 비교 결과

| 기저질환 코호트 | 보고된 p-value |
|:---|---:|
| 만성 신장질환 | `2.904986e-13` |
| 만성 부비동염 | `1.474284e-09` |
| 고혈압 | `2.411282e-37` |
| 대사증후군 X | `3.806251e-17` |

### Cox 모형에서 보고된 주요 변수

| 변수 | Hazard Ratio | 95% CI | p-value |
|:---|---:|---:|---:|
| 고혈압 | `5.481112` | `3.089143–9.725217` | `6.057148e-09` |
| 연령 — 1년 증가 | `1.065921` | `1.053366–1.078627` | `4.582507e-26` |
| 비만 여부 | `1.092836` | `0.673530–1.773182` | `0.7192203` |

> 위 수치는 당시 포스터와 발표자료에 기재된 결과입니다. 원본 데이터와 분석 코드가 남아 있지 않아 이 저장소에서 독립적으로 재현하거나 모형 가정을 다시 검토하지는 못했습니다.

<details>
<summary><strong>발표자료에서 추출한 결과 이미지 보기</strong></summary>

<br/>

#### 만성 신장질환

![만성 신장질환 Kaplan–Meier 결과](./assets/results/km-chronic-kidney-disease.png)

#### 만성 부비동염

![만성 부비동염 Kaplan–Meier 결과](./assets/results/km-chronic-sinusitis.png)

#### 고혈압

![고혈압 Kaplan–Meier 결과](./assets/results/km-hypertension.png)

#### 대사증후군 X

![대사증후군 X Kaplan–Meier 결과](./assets/results/km-metabolic-syndrome-x.png)

#### Cox 비례위험모형 요약

![Cox 비례위험모형 결과](./assets/results/cox-model-summary.png)

</details>

---

## 🔎 결과 해석

Kaplan–Meier 분석에서는 비만 여부로 층화한 각 기저질환 분석에서 생존곡선 차이가 보고되었습니다. 그러나 곡선의 분리만으로 비만이나 특정 기저질환의 독립적인 관련성을 판단하기는 어렵습니다.

다변량 모형에서는 연령과 고혈압이 사망위험과 유의한 관련성을 보였고, 비만 여부는 다른 변수들을 함께 고려한 뒤에는 유의한 변수로 남지 않았습니다. 따라서 이 프로젝트에서는 **단변량으로 관찰된 집단 차이와 공변량 보정 이후에도 유지되는 관련성을 구분해 해석**했습니다.

---

## ⚠️ 해석 범위와 한계

- Kaplan–Meier 곡선의 차이는 집단 간 생존분포 차이를 보여주지만, 특정 요인의 독립적인 효과나 인과관계를 의미하지 않습니다.
- Cox 모형의 추정치는 코호트 정의, 변수 코딩, 결측치 처리와 비례위험 가정에 영향을 받을 수 있습니다.
- 현재 원본 데이터와 분석 코드가 없어 정확한 전처리 과정과 모형 진단 절차를 재검토할 수 없습니다.
- 분석은 합성 임상데이터를 기반으로 하므로 실제 환자집단에 결과를 그대로 일반화할 수 없습니다.
- 본 저장소는 당시 프로젝트를 보존·설명하기 위한 아카이브이며, 재현 가능한 분석 패키지가 아닙니다.

---

## 📂 공개 자료와 범위

이 저장소에는 다음 자료만 포함합니다.

- 프로젝트 분석 구조를 설명하는 인포그래픽
- 당시 발표자료에서 추출한 집계 결과 이미지
- 개인정보를 정리한 공개용 포스터
- 개인정보를 정리한 공개용 발표자료
- 공개용 상장 사본

다음 자료는 포함하지 않습니다.

- 원본 또는 가공된 행 단위 데이터
- 전처리·분석 코드와 실행 가능한 노트북
- COMPASS 내부 화면이나 데이터 내보내기 파일
- 환자 또는 표본 단위 식별정보

---

## 🏆 수상 및 관련 자료

| 자료 | 링크 |
|:---|:---|
| 포스터 | [2024 COMPASS 해커톤 포스터](./materials/2024-compass-hackathon-poster.pdf) |
| 발표자료 | [2024 COMPASS 해커톤 발표자료](./materials/2024-compass-hackathon-presentation.pdf) |
| 상장 | [2024 COMPASS 해커톤 장려상](./materials/2024-compass-hackathon-award.pdf) |
| 행사 보도 | [베리타스알파 — 강원지역혁신플랫폼 대학교육혁신본부, '2024 COMPASS 해커톤' 성료](https://www.veritas-a.com/news/articleView.html?idxno=528804) |

> 외부 기사는 해커톤의 개최 사실과 운영 방식을 소개한 자료입니다. 본 팀의 프로젝트 내용이나 장려상 수상을 직접 보도한 기사는 아닙니다.

---

## 👥 참여자

본 프로젝트는 **최기범과 한만규가 함께 수행한 2인 팀 프로젝트**입니다.

- **최기범** — 연구 질문 및 분석 방향 설정, 코호트 구성, 통계분석, 결과 해석, 발표
- **한만규** — 공동 프로젝트 수행

본 저장소는 최기범이 당시 포스터·발표자료와 상장을 바탕으로 정리했습니다.
