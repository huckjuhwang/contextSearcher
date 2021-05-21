## 다국어 문화요소추출시스템(CEMS)
개별 언어 속에서 문화요소를 발견하고 이를 통해 실제 학습자의 의사소통능력을 제고하며 언어교육의 수월성을 높일 수 있는 방안의 일환으로 다국어문화요소추출시스템이다.

## 연구원 프로젝트
프로젝트 시작 부터 배포되기 까지 모든과정을 겪어보고, 데이터 개수가 1000만개가 넘는 테이블을 관리, 검색, 생성하여 성과를 냈던 프로젝트 입니다. <br>
현재 이 프로젝트는 일부 언어학자 분들을 대상으로 운영되고 유지보수  있습니다.<br>
보안상 간략하게 내용을 담았습니다.<br>

- 프로젝트 명 : 문화요소 추출 시스템
- 개발기간 : 2020.04.01 ~ 2021.05.30
- 화면설계. 퍼블리싱. 백엔드. 테스트. 배포. 유지보수 및 프로젝트 문서화
- 개발 인원 : 1명 
- 관리자 : 1명 

## 기술스택

### Client
- HTML
- Javascript
- JQuery
- CSS

### Server
- JAVA
- JSP
- MYSQL

## 개발 포인트
[1. 검색 속도개선을 위한 구조 분석](#검색-속도개선을-위한-구조-분석)<br>
[2. 속도개선 결과 ](#속도개선-전과-이후-비교)


<br><br><br><br>



https://user-images.githubusercontent.com/47339929/119083535-18fcf580-ba3b-11eb-91bf-743dab392635.mp4


<br><br><br><br>









검색 결과

![image](https://user-images.githubusercontent.com/47339929/119082339-cfaba680-ba38-11eb-8cf3-292c424ed2c2.png)




## 검색 속도개선을 위한 구조 분석
### 1. 속도 개선 방안 
<center><img src="https://user-images.githubusercontent.com/47339929/112755859-8aad5a00-901d-11eb-9fbe-513a8c0ac86b.png" width="650" height="290"></center>

- 각 프로젝트 모듈마다 검색 시간을 분석하였습니다. 
- 이후 가장 시간이 많이 소요되는 부분 부터 속도 개선을 진행 하였습니다. <hr>

#### 속도 개선 방안 1. N번 반복하는 부분을 나눠서 멀티쓰레드 사용<br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757312-3d80b680-9024-11eb-80bd-45afc7743825.png" width="650" height="290"></center>

- 형태소 관련 데이터를 추출하는 과정에서 한개의 요소 당 대략 <b>0.005초</b>가 소요.
- 만약 추출해야되는 문화요소 개수가 2000개 라고 한다면 추출하는데에서 걸리는 시간만 <b> 15초이상</b>의 시간을 잡아먹는 상황인것을 파악.
- 멀티쓰레드를 사용하여 500개 단위 당 Thread 1개를 생성하여 같은 작업을 처리 시스템 속도를 향상.( Thread MAX 개수 지정 ) <hr>


#### 속도 개선 방안 2. 비효율적으로 동작하는 sql을 트리거 사용 <br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757351-79b41700-9024-11eb-8fcd-020748313e02.png" width="650" height="290"></center>

- SQL 쿼리문 분석 중 테이블의 튜플의 개수를( 1000만개 이상 ) 카운트하는 쿼리문이 존재.
- 때문에 매우 비효율적으로 동작을하고 있는 것으로 파악.
- 별도의 테이블개수를 저장하는 테이블을 만들고 트리거를 사용하여 테이블 갱신 시에 지속적으로 업데이트 되도록 구성.
<br><hr>

#### 방안3. 별도의 동작을 하는 각 기능들을 병렬처리 <hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757359-83d61580-9024-11eb-8901-50934c76f0f2.png" width="650" height="290"></center>

- 서로 영향을 받지않는 문화요소 후보 가중치계산 부분과 용례문장 생성 부분을 병렬처리하여 속도를 개선.


## 속도개선 전과 이후 비교

### 한국어

### 중국어
<center><img src="https://user-images.githubusercontent.com/47339929/112798475-e6bcc080-90a7-11eb-85b4-e6bd00b229c3.png" width="650" height="290"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112798509-f1775580-90a7-11eb-94a7-0a9ab4f9af86.png" width="650" height="290"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112798532-f805cd00-90a7-11eb-8af0-312484682bef.png" width="650" height="290"></center>
<hr>

### 일본어
<center><img src="https://user-images.githubusercontent.com/47339929/112798982-b32e6600-90a8-11eb-8712-abee41b11f07.png" width="650" height="290"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112799015-c0e3eb80-90a8-11eb-8311-7578be55d011.png" width="650" height="290"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112799045-c93c2680-90a8-11eb-8918-541793067cb4.png" width="650" height="290"></center>
<hr><br>
