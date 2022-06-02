# 간단 정리 (작성 중)

1. NODE JS 설치
2. 프로젝트 폴더 생성
3. 터미널 -> npx create-react-app [프로젝트명]

npm <-> npx 
create-react-app : boilerplate 생성을 도와주는 node-js의 라이브러리

App.js : 메인 페이지에 들어갈 HTML 작성, function 과 class 정의

## 간단한작동원리 ##

App.js <-> index.js <-> index.html

index.js 에서 App.js 에 정의된것들을 가져와 index.html에 랜더링


## 디렉토리 구조 및 파일 ##
1. node_modules 폴더: 라이브러리 모음
2. public 폴더: static 파일 보관
3. src 폴더: 소스코드 보관
4. package.json : 설치한 라이브러리 목록

## JSX 문법 ##

div class 사용 불가 -> div className 사용
데이터 바인딩을 쉽게 함
전통적인 JS 데이터 바인딩인 document.getElementById().innerHTML 을 쓸 필요가 없다
변수에 데이터를 담아 { 변수명, 함수 등 } 으로 데이터 바인딩
<img src='이미지경로' /> 도 쓸 수 있지만 이미지를 import 하여 <img src = { 이미지 } /> 으로 호출 가능하다.
이 외에도 src, id, href, className 등의 속성에도 적용 가능

JSX에서 style 속성을 넣을 땐 style='font-size  :16px'> 의 문법이 아닌,
style = { object 자료형으로 만든 스타일 } 같이 오브젝트 형식으로 삽입하여야 한다.

JSX는 camelCase 문법을 따른다

## useState 사용법 ##

1. { useState } 임포트
2. useState(데이터);

state는 변수 대신 쓰는 데이터 저장공간이며, useState()를 이용하여 만든다.  
관습적인 선언 방식은 [state 데이터, state 데이터 변경 함수] = useState(데이터); 가 된다.
문자, 숫자, array, object 등 모든 데이터를 담아둘 수 있다.  
변수에 선언하면 되지 않나 ? -> state에 데이터를 저장하는 이유는 Web이 App처럼 동작하게 만들기 위함이다.
state 의 가장 큰 특징은 변경될 경우 HTML 이 재랜더링 되기 때문이다. (정렬, 수정 등의 액션이 일어날때 새로고침이 없어도 됨)
자주 바뀌거나 중요한 데이터는 변수 말고 state 에 저장하는게 좋다.

## 문법 ##

이벤트 핸들러
onClick = { 클릭될 때 실행할 함수 }
onClick = { () => { 실행식 } }
