# Ewha Statistics Analysis Association (ESAA)

이화여자대학교 통계분석학회 **ESAA** 활동 중 수행한 스터디, 과제, 미니프로젝트와 팀 프로젝트를 정리한 저장소입니다.

학습 기록 전체를 보관하되, 주요 프로젝트는 문제 정의 → 데이터 처리 → 피처 설계 → 모델링 → 검증 흐름이 보이도록 별도 README로 정리했습니다.

## Featured Projects

| Project | Task | Main Methods | Result |
|---|---|---|---|
| [유통데이터 활용 경진대회](./OB/프로젝트/유통데이터%20활용%20경진대회) | 2025년 1–3월 매입·매출 수요 예측 | Lag/Rolling features, external indicators, RF/XGBoost/LightGBM | 2021–2023 학습 → 2024 holdout 검증 |
| [작가 분류](./OB/프로젝트/작가%20분류) | 문체 기반 5-class text classification | Linguistic features, TF-IDF/CountVectorizer, stacking | Multi-class Log Loss |
| [음악 추천 시스템](./OB/프로젝트/음악%20추천%20시스템) | KKBox 재청취 여부 예측 | User/Song features, RF/XGBoost/LightGBM/CatBoost | Public AUC 0.6897 / Private AUC 0.6911 |
| [사이버 공격 유형 예측](./YB/방학프로젝트) | 네트워크 트래픽 기반 공격 유형 분류 | Classification | Private Score 0.91887 (4th) |

## Repository Structure

### YB
- `YB/스터디` — 학회 스터디 코드
- `YB/과제` — 주차별 과제
- `YB/연습문제` — NumPy·pandas·ML 연습문제
- `YB/수상작 리뷰` — 데이터 분석 경진대회 수상작 리뷰
- `YB/미니프로젝트` — 시각화·분류·회귀 미니프로젝트
- `YB/방학프로젝트` — 사이버 공격 유형 예측 해커톤

### OB
- `OB/과제` — 학회 과제
- `OB/연습 문제` — ML·추천시스템·시계열 연습문제
- `OB/수상작 리뷰` — 경진대회 수상작 리뷰
- `OB/프로젝트` — 팀 프로젝트

## Notes
- 교재 필사·스터디·과제와 프로젝트를 구분해 저장합니다.
- 프로젝트 폴더에는 가능한 경우 별도 README를 두어 문제 정의, 분석 방법, 결과, 개인 기여를 기록합니다.
- 일부 원본 데이터는 대회/프로젝트 제공 자료이므로 공개 가능한 코드와 분석 과정 중심으로 정리합니다.
