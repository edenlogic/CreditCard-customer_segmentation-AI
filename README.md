# Credit-card-customer-segmentation-AI
데이콘 해커톤- 신용카드 고객 세그먼트 분류 AI


## Feature Importance분석.ipynb

1. 키워드 기반 Feature Importance 분석
: '이용', '금액', '연체' 특정 키워드와 "R3M", "R6M" 등 특정 시간이 포함된 피처들의 분류 성능 및 중요도 분석

- keywords = ["이용", "금액", "연체"] #여기서 kewords 설정
- time_filters = ["R3M", "R6M"]  # 여기서 기간 설정, []로 두면 기간 조건 X


3. 전체 피처 중 상위 30개씩 Feature Importance 분석
: 전체 피처를 기준으로 LightGBM의 feature importance 상위 30개를 추출하여 분석

- show_next_30_features(model_all, all_columns)  # 실행 시 다음 상위 30개 추출


## 신용카드_세그먼트_분류_1차제출

1. 데이터 구성
- 입력 데이터: card_train.csv, card_test.csv

- 추천 피처: 총 50여 개 변수로 구성된 recommended_columns 기준 사용

2. 전처리
- Object 타입 컬럼에 대해 Label Encoding 및 Frequency Encoding 적용

- 결측치 및 inf 값은 적절히 처리 (평균 또는 0 대체)

- 파생 변수 생성: 카드 이용률, 포인트 사용률, 연체 비율 등 총 8개 파생 변수 추가

3. 데이터 불균형 처리
- SMOTE 및 RandomOverSampler를 결합하여 불균형 보정

- 클래스별 타깃 수량을 수작업 지정 (e.g., 클래스 2 → 40000, 클래스 0 → 35000 등)

4. 모델 학습
- 앙상블 구조로 XGBoost, LightGBM, CatBoost 모델을 사용하여 soft voting 수행

- 모델 하이퍼파라미터는 수동으로 튜닝 (e.g., n_estimators=300, max_depth=5 등)

#### 평가 결과 (Validation)

- Soft Voting 기준
  F1 Score (macro): 0.9372
  F1 Score (weighted): 0.9311

- Cross Validation 평균 (3-Fold 기준)
  XGB: 0.9349
  LGB: 0.9449
  CAT: 0.9187

#### 최종 제출 결과
- 제출 파일: card_test_submission.csv
- 리더보드 점수: 0.869840733634568
