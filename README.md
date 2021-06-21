

## 다국어 문화요소추출시스템(CEMS)
개별 언어 속에서 문화요소를 발견하고 이를 통해 실제 학습자의 의사소통능력을 제고하며 언어교육의 수월성을 높일 수 있는 방안의 일환으로 다국어문화요소추출시스템이다.

## 연구원 프로젝트
프로젝트 시작 부터 배포되기 까지 모든과정을 겪어보고, 데이터 개수가 1000만개가 넘는 테이블을 관리, 검색, 생성하여 성과를 냈던 프로젝트 입니다. <br>
현재 이 프로젝트는 일부 언어학자 분들을 대상으로 운영되고 유지보수  있습니다.<br>
보안상 소스코드는 포함하지 않았습니다.
<br>

- 프로젝트 명 : 문화요소 추출 시스템
- 개발기간 : 2020.04.01 ~ 2021.05.30
- 기여한 내용 : <br>
<b>1) 화면설계</b><br>
<b>2) 퍼블리싱</b><br>
<b>3) 검색속도 개선(하단에 설명 기재)</b><br>
-> 전체시스템의 모듈 작동시간 분석 및 상황에 맞는 트리거, 멀티쓰레드를 사용해 보았음 적절한 방식을 찾게되어 최소 80퍼 이상의 성능향상의 결과를 이루었습니다. <br>
<b>4) 추가적인 정보를 얻기 위한 통계 테이블 생성 </b><br>
-> 단어 사이의 빈도수를 미리 계산하여 테이블을 생성하였으며 이로인해 DB검색 성능을 향상 시켰습니다.<br>
통계 Table에 insert해야하는 데이터가 적어도 1천만건 이상의 튜플들로 이루어 져있었기 때문에 preparedStatement에서 제공하는 addBacth() 메소드를 사용을 해볼 수있었습니다. <br>
메소리상에 쿼리들을 올려놓고 한번에 쿼리를 실행하는 방식으로 DB에 N번을 접근하지 않고 한번에 일정량의 쿼리를 실행시켜 효율성을 증대시켰습니다.<br>

<b>5) 프로젝트 문서화</b><br>
-> 인수인계를 하기위한 문서를 만들었습니다. 인수인계서 목차는 다음과 같습니다.

```
1. 개발환경 설정	
1.1. 환경변수 설정	
1-2. 이클립스 설정 	
1-3. Dynamic Web Project 생성	
1-4. java RunTime 설정	
1-5. Tomcat 추가	
1-6. 서버 실행 및 실행결과 확인	

2. 서버	
2-1. 서버 계정	
2-2. 접속 방법	
2-3. 서버 환경 구성 및 JAR파일 위치	
2-3-1 서버 환경	
2-3-2 JAR파일 위치	
2-4. 프로그램 수정 후 적용 방법	
2-4-1 수정 된 코드 적용 방법	
2-4-2 Tomcat서버 재시작 방법	

3. 프로그램 설명	
3-1. 입력 인터페이스	
3-2. 웹페이지 관계도 및 파일 설명	
3-3. 자바 프로그램 실행	
3-4. 출력 형태 	

4. 연구원 과제 진행 시 발생한 에러 사항 및 해결방안	
```

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

## 이슈
[1. 검색 속도개선을 위한 구조 분석](#검색-속도개선을-위한-구조-분석)<br>
[2. 속도개선 결과 ](#속도개선-전과-이후-비교)<br>
[3.[Tomcat] Apache Tomcat 취약점(Ghostcat) 조치방안](https://blog.naver.com/skygurwn96/221885327776)<br>
[4.[DataBase] 대용량 데이터(파일) DB Insert 시키기](https://blog.naver.com/skygurwn96/222294234818)<br>


<br><br><br><br>

https://user-images.githubusercontent.com/47339929/121848079-7cb9cc00-cd24-11eb-90ba-670fb6f65cfb.mp4

<br><br><br><br>


### 검색 결과

![image](https://user-images.githubusercontent.com/47339929/119082339-cfaba680-ba38-11eb-8cf3-292c424ed2c2.png)


### 저장 결과
- 빈도수 상위 랭킹 N개 * N개 사이의 공기빈도 출력
![image](https://user-images.githubusercontent.com/47339929/121847056-f3ee6080-cd22-11eb-904d-d24d654cd87d.png)

- 입력한 형태소와 같이 등장한 다른 형태소 와의 공기빈도 출력
![image](https://user-images.githubusercontent.com/47339929/121847104-05376d00-cd23-11eb-8fc3-482a5f3a7595.png)

- 입력한 형태소와 어떤 형태소와 같이 등장하는지와 용례문장 데이터 출력


![image](https://user-images.githubusercontent.com/47339929/121847458-8ee73a80-cd23-11eb-834b-2f67119ef845.png)



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
