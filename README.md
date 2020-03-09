# dacon 금융문자 분석 대회
### 기간
2019.11.21 - 2020.01.12 23:59

### 실행환경
colab

### 사용 라이브러리
- numpy
- pandas
- sklearn
- keras_preprocessing
- collections
- imblearn
- gensim
- tensorflow

### 데이터 설명
- KB 금융그룹 및 KISA(한국인터넷진흥원)에서 제공받은 정상문자와 스미싱 문자
- 제공되는 데이터에는 개인정보 보호를 위해 개인정보로 간주될 수 있는 이름, 전화번호, 은행 이름, 지점명은 X 혹은 * 로 필터링 되어 제공된다.
- 스폰서의 요청으로 데이터 공유는 불가하다.

### 전처리
본 데이터는 개인 정보가 XXX로 치환되어 있다. 높은 빈도수로 등장하지만 예측에는 방해되기 때문에 특수문자와 함께 제거한다.                                                                                                                            
### 클래스 불균형 맞추기
본 데이터는 스미싱 문자가 전체 문자에서 6% 정도밖에 되지 않는다. 그래서 Undersampling을 이용하여 전체의 20% 가 되도록 샘플링을 적용했다.

### Tokenizing
문장을 분석하려면 먼저 형태소 단위로 문장을 쪼개야한다. 형태소 분석을 위해 Konlpy의 **Mecab** 형태소 분석기를 사용했다.

### 다단어 표현 추출
'리브앱' 같이 다단어 표현의 추출을 위해 gensim의 Phrases 라이브러리를 사용하여 bigram, trigram 단어를 추출했다.

### word2vec
모델의 임베딩층을 학습시키지 않고 word2vec로 학습시킨 단어의 분산표현을 사용했다.

### 모델
- 시퀀스 데이터를 다루기 때문에 RNN 계열인 LSTM을 사용하여 모델을 구축했다.
- 임베딩층에 word2vec로 미리 학습한 단어벡터를 사용하여 학습 속도를 높였다.
- 모델 과적합을 막기 위하여 dropout 층도 사용했다.
- optimizer : Adam
- loss function : categorical crossentropy
- metrics : accuracy, auc(본 대회의 평가 지표)
- 클래스의 불균형을 보정하기 위하여 class weight 도 설정해주었다.


