# dacon 금융문자 분석 대회
### 기간
2019-

### 실행환경
코랩

### 사용 라이브러리
numpy
pandas
sklearn
keras_preprocessing
collections
imblearn
gensim

### 전처리
본 데이터는 개인 정보가 XXX로 치환되어 있다. 높은 빈도수로 등장하지만 예측에는 방해되기 때문에 특수문자와 함께 제거한다.                                                                                                                            
### 클래스 불균형 맞추기
본 데이터는 스미싱 문자가 전체 문자에서 6% 정도밖에 되지 않는다. 그래서 Undersampling을 이용하여 전체의 20% 가 되도록 샘플링을 적용했다.



