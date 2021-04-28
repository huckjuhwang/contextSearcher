## 다국어 문화요소추출시스템(CEMS)
개별 언어 속에서 문화요소를 발견하고 이를 통해 실제 학습자의 의사소통능력을 제고하며 언어교육의 수월성을 높일 수 있는 방안의 일환으로 다국어문화요소추출시스템이다.

## 본 프로젝트에서 수행 한 내용
- 프로젝트 명 : 문화요소 추출 시스템
- 개발기간 : 2020.04.01 ~ 2021.05.30
- 화면설계. 퍼블리싱. 백엔드. 테스트. 배포. 유지보수 및 프로젝트 문서화
- 개발 인원 : 1명 
- 관리자 : 1명 

## 연구원 프로젝트
처음부터 배포까지 작은 성과를 냈던 프로젝트 입니다.
현재 이 프로젝트는 일부 언어학자 분들을 대상으로 운영되고 있습니다.
보안상 간략하게 내용을 담았습니다.

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
[1. 검색 속도개선을 위한 구조 분석 및 속도 개선 결과](#검색-속도개선을-위한-구조-분석-및-속도-개선-결과)
[2.코딩을 잘하고 싶어요](#coding을-잘하고-싶어요)

## 개발을 하고 싶어요
## Coding을 잘하고 싶어요




## 검색 속도개선을 위한 구조 분석 및 속도 개선 결과

#### Q. 문제 발생
Apache Tomcat 취약점(Ghostcat) 조치
#### A. 해결방안
방안 1 )  버전별로 제공되는 웹페이지를 찹고하여 최신 버전으로 업데이트한다.<br>
방안 2 )  AJP 설정 중 secretRequired와 secret속성을 통하여 인증제한 설정.<br>
방안 3 )  AJP 프로토콜 포트를 차단해 버린다.<br>
<br>
본 프로젝트에서는 3번의 방식을 사용하였음.

<hr>

#### Q. 문제 발생
JAVA에서는 DB연동이 되는데 JSP에서는 연동이 안되는 문제
#### A. 해결방안
같은 코드를 가지고 자바에서는 JDBC가 잘 연동이 되는데 JSP에서 연동을 할때 문제 난다면 톰켓 문제이다.
쉽게 말하면 톰켓이 JDBC를 찾지 못하는 것이다.

우선적으로 자바가 깔린 폴더를 가면 jre와 jdk가 있다.
여기서 jdk 안에 jre가 또 있는데 톰켓의 경우에는 jdk안에 jre로 가지않고 바로 jre로 간다.

jre > lib > ext 라는 폴더가 있는데 해당 디렉토리 안에다 jdbc를 넣어줘야 jsp에서 톰켓이 jdbc를 인식한다.


#### Q. 문제 발생
연구원 프로젝트를 진행하는 도중에 java 파일의 결과물의 데이터를 넘기기위해서 get 방식이 아닌 post방식을 통하여 데이터를 전송하도록 설계.

post방식의 크기제한은 없다고 알고있었기 때문에 문제 없이 작동할 것 이라고 생각을 했었는데
일정량 이상 데이터크기가 넘어가니 parameter가 넘어가지 않는 현상이 발생.

#### A. 해결방안
현상은 피라미터 개수가 설정 해놓은 개수보다 초과되었기 때문에 발생을 하게 되었습니다.<br>
톰캣에서 설정해 놓을 속성은! maxPostSize와 maxParameterCount입니다.<br>
" Tomcat은 기본적으로 Post로 넘어갈 수 있는 Parameter 최대 Size가 2097152 (2 megabytes), 최대 Parameter갯수는 10000개입니다.(Tomcat 7.0기준) "<br>
get방식에는 제한이있다는 사실을 알고있었는데 post방식에도 제한이 있다는 사실을 처음알게되었습니다.<br><br>

maxPostSize 와 maxParameterCount 속성을 변경하기위해서는 Tomcat의 server.xml에서 Connector Tag 부분에서 변경.<br>



#### 4. 프로젝트 문서화
- 작성내용 
서버계정, 접속방법, 입력 인터페이스 설명, 웹페이지 관계도, 파일설명, 오류 발생부분 및 해결방안.


#### Q. 문제 발생
java.lang.IllegalStateException: getOutputStream() has already been called for this respons 에러 발생
#### A. 해결방안

하지만 유지보수로 인해서 부득이 하게 해당 메소드를 사용해야 하므로 <br>
out.clear(); //out--> jsp자체 객체
out=pageContext.pushBody(); //out--> jsp자체 객체
OutputStream out = response.getOutputStream();
 outputstream을 생성하기 전에 jsp자체의 out객체를 비워주고 사용함.

## 2021.09.15.
### 1. 속도 개선 방안 
<center><img src="https://user-images.githubusercontent.com/47339929/112755859-8aad5a00-901d-11eb-9fbe-513a8c0ac86b.png" width="650" height="290"></center>
- 각 동작방식에 대해서 시간을 분석 하고, 가장 시간이 많이 소요되는 부분에서 속도를 하나하나 개선해 나감.<hr>

#### 방안1. 같은 동작을하는 부분을 나눠서 멀티쓰레드 사용<br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757312-3d80b680-9024-11eb-80bd-45afc7743825.png" width="650" height="290"></center>

문화요소를 추출하는 과정에서 한개의 요소당 <b>0.01초</b>가 소요되었고, <br>
만약 추출해야되는 문화요소 개수가 2000개라고 한다면 추출하는데에서 걸리는 시간만 <b> 20초이상</b>의 시간을 잡아먹는 상황인것을 파악 <br>
이 파트에서 멀티쓰레드를 사용하여 300단위 당 쓰레드1개를 생성하여 각 쓰레드마다 300개씩 처리하도록 하여 시스템 속도를 향상.<hr>
#### 방안2. 비효율적으로 동작하는 sql을 트리거 사용하여 관리 <br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757351-79b41700-9024-11eb-8fcd-020748313e02.png" width="650" height="290"></center>
sql쿼리문을 분석하던 중 테이블의 크기(1000만개)가 매우큰데 전체 튜플을 카운트하는 쿼리문이 존재했습니다.<br>
해당 테이블은 1천만개가 넘는 데이터를 가지고있었기 때문에 매우 비효율적으로 동작을하고 있는 것으로 파악.
해결. 별도의 테이블개수를 저장하는 테이블을 만들고 트리거를 사용하여 지속적으로 업데이트 되도록 구성하였습니다.
<br><hr>

#### 방안3. 별도의 동작을 하는 각 기능들을 병렬처리 <hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112757359-83d61580-9024-11eb-8901-50934c76f0f2.png" width="650" height="290"></center>
서로 영향을 받지않는 문화요소 후보 가중치계산 부분과 용례문장 생성 부분을 병렬처리하여 속도를 개선


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

