# Classifying_Music_Genres_By_Mood
* ipynb 파일의 용량 문제로 인해 파일 내용이 화면에 보이지 않습니다. [이 곳](https://nbviewer.org/github/zekcal/AI_07_Section_2_Project/blob/main/AI_07_%EA%B9%80%EB%B0%B1%EA%B1%B4_Section2.ipynb)을 통해 확인해주시면 감사하겠습니다.
#### 1. 프로젝트 개요 : 곡의 분위기로 음악 분류하기
만약 음악을 들을 수 없는 상황에서 곡을 분류해야 하는 상황이 벌어진다고 가정 → 이 문제를 해결할 수 있는 곡의 분위기를 수치화한 점수를 토대로 곡의 장르를 예측하는 머신 러닝 모델을 구현하는 프로젝트
이를 위해 [Kaggle에서 발견한 데이터](https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019)를 활용
- 데이터는 'artist_name',	'track_name',	'release_date',	'genre',	'lyrics',	'len',	'dating',	'violence',	'world/life, 	...	, 'valence',	'energy',	'topic',	'age'로 구성. 트랙에 대한 정보와, 수치화된 음악의 특징 등이 기록되어 있음

#### 2. 프로젝트 진행 과정
데이터 확인 및 전처리 - 다양한 머신 러닝 모델을 활용한 학습 - 결과 확인
- 데이터 확인 및 전처리
  - 파일 확인, 결측치, 문자열을 범주형 데이터로 변경, 너무 높은 상관관계 열 통합 등
- 다양한 머신 러닝 모델을 활용한 학습
  - 기준 모델(분류 문제이므로 최빈값) 설정 후 Decision Tree, Random Forest, Logistic Regression, XGBoost Classifier, LightGBM을 활용해 f1 스코어를 비교함
  - 높은 점수인 XGBoost Classifier, LightGBM에 대하여 RandomizedSearchCV를 활용한 하이퍼 파라미터 튜닝을 진행
- 결과 확인
  - 기준 모델의 f1 스코어가 0.0987, 최종 선택된 LightGBM의 하이퍼 파라미터 튜닝된 모델의 f1 스코어가 0.3955로 약 4배 이상 높음을 확인
  - 다양한 특징 가운데 'daneability'가 곡 분위기를 확인하는데 가장 큰 영향을 보임을 확인

#### 3. 결론
음악을 듣지 않고도 곡의 분위기를 통해 음악 장르를 구분할 수 있음

#### 4. 파일 구성
AI_07_김백건_Section2.ipynb : 프로젝트 진행 내용이 기록된 파일

#### 5. 프로젝트 진행 기간
21.11.08 ~ 22.11.12

#### 6. 프로젝트 과정에서 느낀 것
- 성취감
    - 다양한 모델을 활용해 프로젝트 결과의 설득력을 높인 것에 대한 성취감을 느낌
- 데이터의 측정 방식에 대한 의구심  
    - 어떤 방식으로 원본 데이터에서 특징적인 분위기를 수치화했는지에 대한 정보를 찾을 수 없었음
    - 이로 인해 모델을 활용해 예측할 때 데이터에 없는 노래를 집어넣어보고 싶었으나 수치화를 시킬 수 없어 임의로 점수를 입력한 점이 아쉬움
- 결과의 낮은 수치
    - 모델 입장에서 타겟인 장르가 7개라 많고 기준 모델보다 4배의 성과를 이룬 것은 사실이지만, f1 스코어가 0.3955로 절대적인 수치 측면에서 높지 않은 점이 아쉬움.
