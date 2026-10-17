# 작가 분류 — Author Classification

## Overview

문장 텍스트의 표현 방식과 문체적 특징을 이용해 **5명의 작가를 분류**한 multi-class text classification 프로젝트입니다.

- Train: 약 54.9K 문장
- Test: 약 19.6K 문장
- Target: 5개 author class
- Metric: Multi-class Log Loss

## Approach

단순 텍스트 벡터화뿐 아니라 작가별 문체 차이를 나타낼 수 있도록 수치형 특징을 직접 설계했습니다.

### Engineered Features
- 문자 수, 단어 수, 평균 단어 길이
- 문장 수, 문장당 단어 수
- 문장부호 비율
- 대문자·숫자 비율
- 명사·형용사·부사·관사 비율
- stopword / unique word 비율
- readability score
- sentiment score

### Text Representation
- 소문자화 및 정제
- TF-IDF
- CountVectorizer
- word / character n-gram 실험
- 수치형 파생변수와 sparse text features 결합

## Modeling

Logistic Regression, SGDClassifier, LightGBM, CatBoost, XGBoost, Random Forest 등을 비교하고, 여러 base model의 **클래스별 예측 확률을 meta-feature로 사용하는 stacking**도 실험했습니다.

프로젝트 회의 기록상 단일 모델 비교에서는 Logistic Regression과 LightGBM 계열이 상대적으로 낮은 Log Loss를 보였고, 후반에는 TF-IDF/Count 기반 예측 확률을 결합하는 stacking을 추가로 실험했습니다.

## My Contribution

- **언어적 특징 설계**
  - 명사/형용사/부사/관사 비율
  - readability score
  - sentiment score
  - 대문자 비율
- 텍스트 전처리 파트
- **TF-IDF 기반 stacking 실험**

## Tech Stack

`Python` `pandas` `NLTK` `TextBlob` `textstat` `scikit-learn` `XGBoost` `LightGBM` `CatBoost`

## Notebook

- [`author_classification.ipynb`](./author_classification.ipynb) — EDA, 문체 파생변수, TF-IDF/Count 기반 모델링 및 stacking 실험
