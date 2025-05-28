# Credit-card-customer-segmentation-AI
데이콘 해커톤- 신용카드 고객 세그먼트 분류 AI


## Feature Importance분석.ipynb

1. 키워드 기반 Feature Importance 분석
: '이용', '금액', '연체' 특정 키워드와 "R3M", "R6M" 등 특정 시간이 포함된 피처들의 분류 성능 및 중요도 분석
keywords = ["이용", "금액", "연체"] #여기서 kewords 설정
time_filters = ["R3M", "R6M"]  # 여기서 기간 설정, []로 두면 기간 조건 X


2. 전체 피처 중 상위 30개씩 Feature Importance 분석
: 전체 피처를 기준으로 LightGBM의 feature importance 상위 30개를 추출하여 분석
show_next_30_features(model_all, all_columns)  # 실행 시 다음 상위 30개 추출

