# 다국어 '문화요소추출시스템(CEMS)' 인터페이스 개발 


### 문화요소 추출 시스템이란?

개별 언어 속에서 문화요소를 발견하고 이를 통해 실제 학습자의 의사소통능력을 제고하며 언어교육의 수월성을 높일 수 있는 방안의 일환으로 다국어문화요소추출시스템이다.
우선 그 첫 번째 시도로서 본 프로젝트에서는 한·중·일 문화요소추출시스템의 개발을 통하여 다국어로의 확장 가능성을 가늠해보고 향후 다국어 문화요소추출시스템의 단계적인 구축을 위한 발판으로 삼으려고 하는 목표가 있다.

### 본 프로젝트에서 수행 한 내용
1. 인터페이스 구축 <br>
2. 시스템 검색 속도 개선<br>
3. 형태소간의 공기빈도 값 DB테이블 구축<br>
4. 형태소간의 공기빈도 값 검색 구현<br>


### 2021.12.05 (초기 인터페이스 구축)
<hr>
![image](https://user-images.githubusercontent.com/47339929/112755509-f098e200-901b-11eb-9589-cac86bb203ca.png)

- 형태소 입력 화면 페이지

<br><hr>
![image](https://user-images.githubusercontent.com/47339929/112755525-fd1d3a80-901b-11eb-9d19-15d90b414f2b.png)
- 인터페이스 입력 및 검색결과 확인 페이지


### 인터페이스 입력 값에 대한 간단한 설명 <br>
<b>질의 형태소</b> : 검색 대상이 되는 기준 형태소. 예: '먹다' 주변의 문맥을 검색하려는 경우 '먹'만 입력하면 됨.<br>
<b>질의 형태소 품사</b> : 질의 형태소의 품사. 하나만 선택.<br>
<b>문맥 형태소 종류</b> : 질의 형태소 주변에 등장한 형태소(문맥 형태소)들의 품사. 여러 개 선택 가능.<br>
<b>추출 문맥 사이즈</b> : 추출할 문맥 형태소의 개수<br>
<b>추출 문맥 종류</b> : 1차 문맥은 질의 형태소와 동일한 문장에서 등장한 형태소. 2차 문맥은 1차 문맥과 동일한 문장에서 등장한 형태소. 2차 문맥 추출은 시간이 많이 걸릴 수 있으니 꼭 필요한 경우에만 실행하시길 바람.<hr>
![image](https://user-images.githubusercontent.com/47339929/112755533-027a8500-901c-11eb-9966-a0eacde17ec6.png)<hr>
![image](https://user-images.githubusercontent.com/47339929/112755541-07d7cf80-901c-11eb-93c8-d47a6936d3e8.png)<hr>
### 검색결과<hr>
![image](https://user-images.githubusercontent.com/47339929/112755560-17efaf00-901c-11eb-84cc-175cd2307367.png)

### 저장결과<hr>
![image](https://user-images.githubusercontent.com/47339929/112755567-21791700-901c-11eb-97ad-099a43498114.png)



## 2020.04.16. 
#### 1. 하나의 페이지에서 검색하고 볼수 있도록 페이지 축소
#### 2. 저장 파일 이름 수정 (test.txt로 입력했을 경우 test.txt.txt로 저장되는 현상)
#### 3. 도움말 내용수정 및 추가 
<b>질의 형태소</b> : 검색 대상이 되는 기준 형태소. 예: '먹다' 주변의 문맥을 검색하려는 경우 '먹'만 입력하면 됨.<br>
<b>질의 형태소 품사</b> : 질의 형태소의 품사. 하나만 선택.<br>
<b>문맥 형태소 종류</b> : 질의 형태소 주변에 등장한 형태소(문맥 형태소)들의 품사. 여러 개 선택 가능.<br>
<b>추출 문맥 사이즈</b> : 추출할 문맥 형태소의 개수<br>
<b>추출 문맥 종류</b> : 1차 문맥은 질의 형태소와 동일한 문장에서 등장한 형태소. 2차 문맥은 1차 문맥과 동일한 문장에서 등장한 형태소. 2차 문맥 추출은 시간이 많이 걸릴 수 있으니 꼭 필요한 경우에만 실행하시길 바람.<br>


## 2020.06.12.

#### 1. 숫자 값들의 경우 가운데 정렬 하지않고 대소관계가 잘 파악될수 있도록 정렬
( ex. 소수점은 소수점 기준으로 정렬, 숫자는 왼쪽정렬, 문자는 오른쪽 정렬)

#### 2. 각 컬럼을 기준으로 오름차순 내림차순 가능하도록 구현


## 2020.07.16. 
#### 1. 테이블 검색 기능
-각 테이블 오른쪽 상단을 통하여 검색할수 있도록 하였습니다.

#### 2. 특정행 값만 저장할수 있도록 체크박스 생성
-  용례문장 테이블에서 체크박스를 선택하고 저장을 누를경우 선택된 행의 값만 가지고 저장을 할 수 있도록 하였습니다. 만약 체크박스를 선택하지 않고 저장할 경우 이전에 보셨던 출력과 동일하게 출력이 됩니다.

#### 3. 사용자가 체크한 체크박스를 초기화 할 수 있는 누른 체크박스의 개수 표시를 추가
- 버튼을 누르게 되면 체크박스에 체크들이 모두 초기화가 됩니다.

#### 4. 프로젝트 문서화
- 작성내용 
서버계정, 접속방법, 입력 인터페이스 설명, 웹페이지 관계도, 파일설명, 오류 발생부분 및 해결방안.


## 2020.09.03.
#### 1. 소스레벨 연동<br>
 Before  : jar 파일을 사용하여 연동<br>
 After   : 첨부한 소스파일을 사용하여 소스 코드 레벨에서 연동되도록 수정.  
 
#### 2. 리팩토링 과정<br>
검색기능을 하는 소스코드와 비슷한 기능을 하는 변수들의 이름을 같도록 변경

#### 3. java.lang.IllegalStateException: getOutputStream() has already been called for this respons 에러 처리 <br>
검색 결과를 저장하는 과정에서 에러가 발생하는 것을 확인
JSP에서는 Servlet으로 변환시 내부적으로 out객체가 자동으로 생성되기 때문에 따로 out객체를 만들면 충돌이 일어나서 발생하는 이슈로 파악.
<br>
#### 해결방안
outputstream을 생성하기전에 JSP자체의 out객체를 비워주고 사용하도록 하여 에러처리

## 2021.09.15.
### 1. 속도 개선 방안 

<center><img src="https://user-images.githubusercontent.com/47339929/112755859-8aad5a00-901d-11eb-9fbe-513a8c0ac86b.png" width="1200" height="500"></center>
- 각 동작방식에 대해서 시간을 분석 하고, 가장 시간이 많이 소요되는 부분에서 속도를 하나하나 개선해 나감.<hr>
#### 1.1 멀티쓰레드 사용<br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757312-3d80b680-9024-11eb-80bd-45afc7743825.png" width="1200" height="500"></center>

문화요소를 추출하는 과정에서 한개의 요소당 <b>0.01초</b>가 소요되었고, <br>
만약 추출해야되는 문화요소 개수가 2000개라고 한다면 추출하는데에서 걸리는 시간만 <b> 20초이상</b>의 시간을 잡아먹는 상황이였습니다 <br>
이 파트에서 멀티쓰레드를 사용하여 300단위 당 쓰레드1개를 생성하여 각 쓰레드마다 300개씩 처리하도록 하여 시스템 속도를 향상시켰습니다.<hr>
#### 1.2 트리거 사용 <br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757351-79b41700-9024-11eb-8fcd-020748313e02.png" width="1200" height="500"></center>
sql쿼리문을 분석하던 중 테이블의 크기가 매우큰데 전체 튜플을 카운트하는 쿼리문이 있었습니다.<br>
해당 테이블은 1천만개가 넘는 데이터를 가지고있었기 때문에 매우 비효율적으로 동작을하고 있는 것으로 파악하였고
#### 별도의 테이블개수를 저장하는 테이블을 만들고 트리거를 사용하여 지속적으로 업데이트 되도록 구성하였습니다.
<br><hr>
#### 1.3 멀티쓰레드 사용<hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757359-83d61580-9024-11eb-8901-50934c76f0f2.png" width="1200" height="500"></center>
서로 영향을 받지않는 문화요소 후보 가중치계산 부분과 용례문장 생성 부분을 병렬처리하여 속도를 개선


## 속도개선 전과 이후 비교

<br><hr>
## 2020.01.04

#### 1. 순위 가운데 정렬
#### 2. 표 접기 기능 추가
#### 3. 표의 전체적인 길이 확장
- 표에서 더 많은 데이터가 보입니다.
#### 4. "문화요소 체크" 열이나 "용례문장를 선택할수 있는 체크박스" 열이 정렬되지 않도록 변경
- 테이블 자체에 상단바 클릭시 정렬이 되도록 구현을 하였기 때문에, "문화요소 체크" 열도 예외없이 정렬기능이 되어 에러가 발생하는 상황이 있었습니다. 이 문제를 해결하기위해 특정열은 정렬이 안되도록 수정하였습니다.
#### 5. 각 열을 구분하기 위한 세로선을 추가
![image](https://user-images.githubusercontent.com/47339929/112757720-f267a300-9025-11eb-954a-8ada3cd6ab0d.png)

## 2020.02.10
##### 1. 문화요소 체크를 하게되면 클릭한 형태소가 등장한 용례 문장 테이블이 출력
##### 2. 기존의 초기화 버튼을 없애고 표상단의 전체선택 버튼으로 수정
 ![image](https://user-images.githubusercontent.com/47339929/112757812-46728780-9026-11eb-9a30-e7936d591799.png)
##### 3. 표접을때 보여지는 텍스트를 "형태소"와 "추출 개수"가 보여지도록 수정
![image](https://user-images.githubusercontent.com/47339929/112757884-86d20580-9026-11eb-91c9-b164edfc4463.png)
##### 4. 검색 이후 표가 접은 상태가 기본 상태가 아닌 펼쳐져 있는 상태로 수정

##### 5. 테이블 상단에 정렬 라이브러리를 커스텀해서 오름차순 내림차순의 표시 방향을 바꾸었습니다.



