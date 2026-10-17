# 음악 추천 시스템 — KKBox Music Recommendation

## Overview

WSDM KKBox Music Recommendation Challenge 데이터를 활용해 사용자가 특정 곡을 다시 들을 가능성(`target`)을 예측한 프로젝트

- Task: Binary classification / implicit recommendation
- Metric: AUC
- Final model: CatBoost

## Preprocessing

- `song_id`, `msno` 기준 데이터 통합
- `song_length`, `age`: median imputation
- `language`: missing value를 별도 값으로 처리
- 범주형 결측치: `unknown`
- 비현실적 age 범위 보정
- 다중 장르에서 대표 장르 추출
- 날짜형 변수 변환

## Feature Engineering

- `user_count`: 사용자별 청취 횟수
- `song_count`: 곡별 청취 횟수
- `membership_days`: 가입 기간
- `user_genre_preference`: 특정 장르 청취 비중
- `user_genre_diversity`: 고유 장르 수
- `artist_entropy`: 전체 청취 대비 고유 아티스트 비율
- `daily_listen_cnt`: 가입 기간 대비 일평균 청취량
- `isrc_country`, `isrc_year`
- `source_intent`: Passive / Active / Exploratory 유입 성격

## Model Comparison

| Model | Public AUC | Private AUC |
|---|---:|---:|
| Random Forest | 0.6390 | 0.6366 |
| XGBoost | 0.6636 | 0.6669 |
| LightGBM | 0.6702 | 0.6743 |
| **CatBoost** | **0.6897** | **0.6911** |

## My Contribution

- `user_count`, `song_count`, `membership_days` 등 파생변수 아이디어
- 장르 선호도·다양성, artist concentration, source context 등 사용자 행동 feature 설계
- **Random Forest 단일 모델** 실험 및 leaderboard 검증
- 최종 발표의 feature engineering 파트 정리

## Limitations

- 데이터 규모 때문에 일부 모델링에서 층화추출 사용
- multi-genre 정보를 대표 장르 하나로 단순화
- 사용자 행동의 시간 순서를 충분히 활용하지 못함

## Tech Stack

`Python` `pandas` `scikit-learn` `CatBoost` `XGBoost` `LightGBM`

## Notebook

- [`kkbox_music_recommendation.ipynb`](./kkbox_music_recommendation.ipynb) — 최종 프로젝트 모델링 코드 정리본
