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
<center><img src="https://user-images.githubusercontent.com/47339929/112755509-f098e200-901b-11eb-9589-cac86bb203ca.png" ></center>
- 형태소 입력 화면 페이지

<br><hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112755525-fd1d3a80-901b-11eb-9d19-15d90b414f2b.png"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112755533-027a8500-901c-11eb-9966-a0eacde17ec6.png"></center>
<center><img src="https://user-images.githubusercontent.com/47339929/112755541-07d7cf80-901c-11eb-93c8-d47a6936d3e8.png"></center>
- 인터페이스 입력 및 검색결과 확인 페이지


### 인터페이스 입력 값에 대한 간단한 설명 <br>
<b>질의 형태소</b> : 검색 대상이 되는 기준 형태소. 예: '먹다' 주변의 문맥을 검색하려는 경우 '먹'만 입력하면 됨.<br>
<b>질의 형태소 품사</b> : 질의 형태소의 품사. 하나만 선택.<br>
<b>문맥 형태소 종류</b> : 질의 형태소 주변에 등장한 형태소(문맥 형태소)들의 품사. 여러 개 선택 가능.<br>
<b>추출 문맥 사이즈</b> : 추출할 문맥 형태소의 개수<br>
<b>추출 문맥 종류</b> : 1차 문맥은 질의 형태소와 동일한 문장에서 등장한 형태소. 2차 문맥은 1차 문맥과 동일한 문장에서 등장한 형태소. 2차 문맥 추출은 시간이 많이 걸릴 수 있으니 꼭 필요한 경우에만 실행하시길 바람. <br>

문화요소 후보가 되는 문맥 형태소는 1차 문맥과 2차 문맥으로 구분된다.<br>
<b>1차문맥</b>은 질의형태소와 동일한 문장에서 직접적으로 같이 출현한 형태소를 말한다.<br>
<b>2차문맥</b>이란 질의 형태소와 직접적으로 같이 출현하지 않았더라도 공기한 형태소가 질의 형태소의 2차문맥이된다.<br>
다시말하면, 1차문맥과 동일한 문장에서 공기한 형태소가 질의 형태소의 2차문맥이된다.<br>

<hr>

### 검색결과<hr>
<center><img src="https://user-images.githubusercontent.com/47339929/112755560-17efaf00-901c-11eb-84cc-175cd2307367.png"></center>
<hr>

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



#### Q. 문제 발생
Apache Tomcat 취약점(Ghostcat) 조치
#### A. 해결방안
방안 1 )  버전별로 제공되는 웹페이지를 찹고하여 최신 버전으로 업데이트한다.
방안 2 )  AJP 설정 중 secretRequired와 secret속성을 통하여 인증제한 설정.
방안 3 )  AJP 프로토콜 포트를 차단해 버린다.

본 프로젝트에서는 3번의 방식을 사용하였음.


#### Q. 문제 발생
JAVA에서는 DB연동이 되는데 JSP에서는 연동이 안되는 문제
#### A. 해결방안
같은 코드를 가지고 자바에서는 JDBC가 잘 연동이 되는데 JSP에서 연동을 할때 문제 난다면 톰켓 문제이다.
쉽게 말하면 톰켓이 JDBC를 찾지 못하는 것이다.

우선적으로 자바가 깔린 폴더를 가면 jre와 jdk가 있다.
여기서 jdk 안에 jre가 또 있는데 톰켓의 경우에는 jdk안에 jre로 가지않고 바로 jre로 간다.

jre > lib > ext 라는 폴더가 있는데 해당 디렉토리 안에다 jdbc를 넣어줘야 jsp에서 톰켓이 jdbc를 인식한다.


## 2020.06.12.

#### 1. 숫자 값들의 경우 가운데 정렬 하지않고 대소관계가 잘 파악될수 있도록 정렬
( ex. 소수점은 소수점 기준으로 정렬, 숫자는 왼쪽정렬, 문자는 오른쪽 정렬)

#### 2. 각 컬럼을 기준으로 오름차순 내림차순 가능하도록 구현

#### Q. 문제 발생
연구원 프로젝트를 진행하는 도중에 java 파일의 결과물의 데이터를 넘기기위해서 get 방식이 아닌 post방식을 통하여 데이터를 전송하도록 설계.

post방식의 크기제한은 없다고 알고있었기 때문에 문제 없이 작동할 것 이라고 생각을 했었는데
일정량 이상 데이터크기가 넘어가니 parameter가 넘어가지 않는 현상이 발생.

#### A. 해결방안
현상은 피라미터 개수가 설정 해놓은 개수보다 초과되었기 때문에 발생을 하게 되었습니다.
톰캣에서 설정해 놓을 속성은! maxPostSize와 maxParameterCount입니다.
" Tomcat은 기본적으로 Post로 넘어갈 수 있는 Parameter 최대 Size가 2097152 (2 megabytes), 최대 Parameter갯수는 10000개입니다.(Tomcat 7.0기준) "
get방식에는 제한이있다는 사실을 알고있었는데 post방식에도 제한이 있다는 사실을 처음알게되었습니다.

maxPostSize 와 maxParameterCount 속성을 변경하기위해서는
Tomcat의 server.xml에서 Connector Tag 부분에서 변경해주시면됩니다.

<Connector connectionTimeOut="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443" 
URIEncoding="euc-kr" maxPostSize="-1" maxParameterCount="-1" />

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

## 2020.01.04

#### 1. 순위 가운데 정렬
#### 2. 표 접기 기능 추가
#### 3. 표의 전체적인 길이 확장
- 표에서 더 많은 데이터가 보입니다.
#### 4. "문화요소 체크" 열이나 "용례문장를 선택할수 있는 체크박스" 열이 정렬되지 않도록 변경
- 테이블 자체에 상단바 클릭시 정렬이 되도록 구현을 하였기 때문에, "문화요소 체크" 열도 예외없이 정렬기능이 되어 에러가 발생하는 상황이 있었습니다. 이 문제를 해결하기위해 특정열은 정렬이 안되도록 수정
#### 5. 각 열을 구분하기 위한 세로선을 추가
![image](https://user-images.githubusercontent.com/47339929/112757720-f267a300-9025-11eb-954a-8ada3cd6ab0d.png)

## 2020.02.10
##### 1. 1차문맥 부분에서 특정 형태소를 클릭 하게되면 해당 형태소가 등장한 용례 문장 테이블이 등장하도록 수정
![image](https://user-images.githubusercontent.com/47339929/114395924-e9ef9a80-9bd7-11eb-9c4b-bfc86bd37db1.png)

##### 2. 기존의 초기화 버튼을 없애고 표상단의 전체선택 버튼으로 수정
 ![image](https://user-images.githubusercontent.com/47339929/112757812-46728780-9026-11eb-9a30-e7936d591799.png)
##### 3. 표접을때 보여지는 텍스트를 "형태소"와 "추출 개수"가 보여지도록 수정
![image](https://user-images.githubusercontent.com/47339929/112757884-86d20580-9026-11eb-91c9-b164edfc4463.png)
##### 4. 검색 이후 표가 접은 상태가 기본 상태가 아닌 펼쳐져 있는 상태로 수정

##### 5. 테이블 상단에 정렬 라이브러리를 커스텀해서 오름차순 내림차순의 표시 방향 수정


## 2020.04.12

##### 1. 한국어 형태소 간의 관계(빈도수) 출력해주기위한 새로운 DB테이블 구축
##### 2. 한국어 형태소 간의 관계(빈도수)를 출력해주기 위한 인터페이스 및 로직 구성
![image](https://user-images.githubusercontent.com/47339929/114395717-ab59e000-9bd7-11eb-8a93-4fdd0e297f18.png)


![image](https://user-images.githubusercontent.com/47339929/114395630-954c1f80-9bd7-11eb-8895-72b7823b160b.png)
형태소를 기준으로 하여 가장 빈도수가 높은 것들 부터 순차적으로 출력 하도록 하였음.

