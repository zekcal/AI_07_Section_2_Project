# Classifying_Music_Genres_By_Mood
<img src="https://user-images.githubusercontent.com/89769294/176891270-5fa75ed3-6ffb-48ce-8e71-bf1040bf5f9d.png" width="50" height="50">

* ipynb 파일의 용량 문제로 인해 파일 내용이 화면에 보이지 않습니다. [이 곳](https://nbviewer.org/github/zekcal/AI_07_Section_2_Project/blob/main/AI_07_%EA%B9%80%EB%B0%B1%EA%B1%B4_Section2.ipynb)을 통해 확인해주시면 감사하겠습니다.

#### 1. 프로젝트 개요 : 곡의 분위기로 음악 분류하기
만약 **음악을 들을 수 없는 상황**이라면,
  1. 곡의 분위기를 수치화한 기록이 있다면 이를 통해 **장르를 분류해 구분**할 수 있을 것이다.
  2. 이를 활용해 듣고 싶은 분위기를 지정하면 노래를 추천해주는 서비스를 만들 수 있을 것이다.  
  
라는 가설을 세우고 프로젝트를 진행함
- 데이터는 [Kaggle에서 발견한 데이터](https://www.kaggle.com/datasets/saurabhshahane/music-dataset-1950-to-2019)를 활용함
- 'artist_name',	'track_name',	'release_date',	'genre',	'lyrics',	'len',	'dating',	'violence',	'world/life, 	...	, 'valence',	'energy',	'topic',	'age'로 구성, 트랙에 대한 정보와, 수치화된 음악의 특징 등이 기록되어 있음

#### 2. 프로젝트 진행 과정
![image](https://user-images.githubusercontent.com/89769294/176928049-a6c3214d-2fcf-4757-aa50-2d14f527ccbd.png)
데이터 확인 및 전처리 - 다양한 머신 러닝 모델을 활용한 학습 - 결과 확인
- **데이터 확인 및 전처리**
  - 파일 확인, 결측치, 문자열을 범주형 데이터로 변경, 너무 높은 상관관계 열 통합 등

- **다양한 머신 러닝 모델을 활용한 학습**
  - 기준 모델(분류 문제이므로 최빈값) 설정 후 Decision Tree, Random Forest, Logistic Regression, XGBoost Classifier, LightGBM을 활용해 f1 스코어를 비교함
  - 높은 점수인 **XGBoost Classifier, LightGBM에 대하여 RandomizedSearchCV를 활용한 하이퍼 파라미터 튜닝**을 진행

- **결과 확인**
  - 기준 모델의 f1 스코어가 0.0987, 최종 선택된 LightGBM의 하이퍼 파라미터 튜닝된 모델의 f1 스코어가 0.3955로 약 4배 이상 높음을 확인
  - 다양한 특징 가운데 'daneability'가 곡 분위기를 확인하는데 가장 큰 영향을 보임을 확인

#### 3. 결론
![image](https://user-images.githubusercontent.com/89769294/176928875-7af2abae-2de5-41b9-b1b9-0a6ddac1e7c7.png)
  1. 곡의 분위기를 수치화한 기록이 있다면 이를 통해 장르를 분류해 구분할 수 있을 것이다.  
  → **높은 정확도로 가능함**
  2. 이를 활용해 듣고 싶은 분위기를 지정하면 노래를 추천해주는 서비스를 만들 수 있을 것이다.  
  → **웹 디자인이 들어간다면 이 모델을 활용해 빠르게 만들 수 있을 것임**
  
#### 4. 파일 구성
**AI_07_김백건_Section2.ipynb** : 프로젝트 진행 내용이 기록된 파일

#### 5. 프로젝트 진행 기간
21.11.08 ~ 22.11.12

#### 6. 프로젝트 과정에서 느낀 것
- **성취감**
    - 다양한 모델을 활용해 프로젝트 결과의 설득력을 높인 것에 대한 성취감을 느낌

- **데이터의 측정 방식에 대한 의구심**  
    - 어떤 방식으로 원본 데이터에서 특징적인 분위기를 수치화했는지에 대한 정보를 찾을 수 없었음
    - 이로 인해 모델을 활용해 예측할 때 데이터에 없는 노래를 집어넣어보고 싶었으나 수치화를 시킬 수 없어 임의로 점수를 입력한 점이 아쉬움
      - raw data에 대한 이해가 필수적이며 이를 위해 실제 업무에서 도메인의 대한 이해가 중요함을 깨닫게 됨

- **결과의 낮은 수치**
    - 모델 입장에서 타겟인 장르가 7개라 많고 기준 모델보다 4배의 성과를 이룬 것은 사실이지만, f1 스코어가 0.3955로 절대적인 수치 측면에서 높지 않은 점이 아쉬움.
