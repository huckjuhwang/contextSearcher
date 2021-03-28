# 다국어 '문화요소추출시스템(CEMS)' 인터페이스 개발 


문화요소 추출 시스템이란?

개별 언어 속에서 문화요소를 발견하고 이를 통해 실제 학습자의 의사소통능력을 제고하며 언어교육의 수월성을 높일 수 있는 방안의 일환으로 다국어문화요소추출시스템이다.
우선 그 첫 번째 시도로서 본 프로젝트에서는 한·중·일 문화요소추출시스템의 개발을 통하여 다국어로의 확장 가능성을 가늠해보고 향후 다국어 문화요소추출시스템의 단계적인 구축을 위한 발판으로 삼으려고 하는 목표가 있다.

- 수행한 내용
인터페이스, 속도개선, DB테이블 구축


### 2021.12.05 (목)
----
***
___
![image](https://user-images.githubusercontent.com/47339929/112755509-f098e200-901b-11eb-9589-cac86bb203ca.png)
<br>
![image](https://user-images.githubusercontent.com/47339929/112755525-fd1d3a80-901b-11eb-9d19-15d90b414f2b.png)
![image](https://user-images.githubusercontent.com/47339929/112755533-027a8500-901c-11eb-9966-a0eacde17ec6.png)
![image](https://user-images.githubusercontent.com/47339929/112755541-07d7cf80-901c-11eb-93c8-d47a6936d3e8.png)


검색결과

![image](https://user-images.githubusercontent.com/47339929/112755560-17efaf00-901c-11eb-84cc-175cd2307367.png)

저장결과

![image](https://user-images.githubusercontent.com/47339929/112755567-21791700-901c-11eb-97ad-099a43498114.png)


2021.09.15(화)
속도개선
![image](https://user-images.githubusercontent.com/47339929/112755859-8aad5a00-901d-11eb-9fbe-513a8c0ac86b.png)




1. 1차문맥을 선택했을 때 관련된 용례 문장이 출력되도록 하였습니다.
 * x를 선택하더라도 출력이 됩니다.
![image](https://user-images.githubusercontent.com/47339929/112755390-6fd9e600-901b-11eb-98da-aadd0a6a3691.png)
2. 검색 이후 표가 접은 상태가 기본 상태가 아닌 펼쳐져 있는 상태로 수정하였습니다

3. 테이블 상단에 정렬 라이브러리를 커스텀해서 오름차순 내림차순의 표시 방향을 바꾸었습니다.

 

4. 표 접을때 보여지는 텍스트 명을 용례와 개수가 보여지도록 변경하였습니다.



 

 

5. 기존의 초기화 버튼을 없애고 표상단의 전체 선택 버튼으로 변경하였습니다.



 



6. 저장을 할 때 띄어쓰기가 안되는 현상을 해결하였습니다.
