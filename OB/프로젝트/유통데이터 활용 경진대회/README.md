# 유통데이터 활용 경진대회 — Demand Forecasting

## Overview

2021–2024년 유통센터의 매입·매출 데이터를 기반으로 **2025년 1–3월 매입량과 판매량을 예측**한 프로젝트

- 대상: A/B 물류센터의 지정 상품군
- 평가 지표: RMSE, MAE
- 검증: 2021–2023 학습 → 2024 holdout 검증 → 2021–2024 전체 학습 후 2025년 예측

## Data Processing

- 매출 데이터에서 `반품` 제외
- 매입 데이터에서 `반출` 제외
- 날짜 변수 정리 및 월 단위 집계
- 상품군별 데이터 분리
- 범주형 변수 인코딩

## Feature Engineering

### Time & historical demand
- year / month / quarter / holiday
- 1개월 lag, 12개월 lag
- 최근 3개월 평균·최대·최소

### Price
- 개당 단가
- 최근 가격 변동성

### External variables
상품군에 따라 다음 외부 변수를 결합

- 기온·강수량
- 소비자물가지수(CPI)
- 소비자심리지수(CCSI)
- 네이버/구글 검색 트렌드
- 연관 상품군의 과거 수요

## B센터 봉지라면 — Model Validation

### Sales

| Model | RMSE | MAE |
|---|---:|---:|
| XGBoost | 70.0847 | 24.0124 |
| LightGBM | 68.7911 | 24.1548 |
| **Random Forest** | **68.3543** | **23.5165** |

판매량은 Random Forest를 최종 모델로 선택

### Purchase

| Model | RMSE | MAE |
|---|---:|---:|
| XGBoost | 343.0760 | 139.4871 |
| **LightGBM** | **315.1238** | 135.2210 |
| Random Forest | 325.8443 | **133.1050** |

RMSE 기준으로 매입량은 LightGBM을 최종 모델로 선택

## 2025 Q1 Forecast — B센터 봉지라면

| Month | Predicted Sales | Predicted Purchase |
|---|---:|---:|
| 2025-01 | 2,975.58 | 19,682.77 |
| 2025-02 | 2,929.70 | 20,115.42 |
| 2025-03 | 2,792.36 | 20,039.84 |

## My Contribution

- 매출·매입 데이터 **공통 영문 변수명 체계 정리**
- 시계열 예측용 공통 파생변수 설계
  - lag features
  - 3개월 rolling statistics
  - 가격·가격 변동성
  - 분기·휴일 변수
- **B물류센터 봉지라면** 매출·매입 분석 및 모델링
- 라면 CPI, 온라인 검색 트렌드, 용기라면 과거 수요 등 외부·연관 변수 결합

## Files

- `OB_프로젝트_B_봉지라면.ipynb` — B센터 봉지라면 전처리, 피처 생성, 모델 비교 및 2025 Q1 예측

## Tech Stack

`Python` `pandas` `NumPy` `scikit-learn` `XGBoost` `LightGBM`
