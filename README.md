# 간단 정리 (작성 중)

리액트 : 프론트엔드 프레임워크의 하나로서 HTML, CSS, JS 을 이용한 개발을 쉽게 만들어 줌
이와 비슷한 프레임워크로는, 
Vue, Angular, Svelte, Preact, SolidJS 등이 있으나, 생태계 구축이 가장 잘 되어있는 프레임워크라고 할 수 있다. 

1. NODE JS 설치 (node package manager 를 통해 쉽게 리액트 환경 구축 가능)
2. 프로젝트 폴더 생성
3. 터미널 -> npx create-react-app [프로젝트명]

* 오류 발생시
Windows : 허가되지 않은 스크립트 ~ 에러 -> 관리자 권한으로 실행된 프롬프트에서 Set-ExcutionPolicy Unrestricted 명령어를 실행하여 정책 변경
MacOs : Permission (권한) 에러 -> 터미널에서 sudo (관리자) 명령어로 재시도

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
4. package.json : 설치한 라이브러리 목록, 프로젝트 정보

## JSX 문법 ##

React.CreateElemnet() 등을 사용 안해도 된다.
document.querySelector().innerHTML = 변수; 등을 사용 안해도 된다.

div class 사용 불가 -> div className 사용 (기본적으로 JS 작성 공간이기 때문에 class를 쓰게되면 class 선언 문법과 겹치게됨.)
데이터 바인딩을 쉽게 함
전통적인 JS 데이터 바인딩인 document.getElementById().innerHTML 을 쓸 필요가 없다
변수에 데이터를 담아 { 변수명, 함수 등 } 으로 데이터 바인딩
&lt; img src='이미지경로' /&gt; 도 쓸 수 있지만 이미지를 import 하여 &lt;img src = { 이미지 } /&gt; 으로 호출 가능하다.
이 외에도 src, id, href, className 등의 속성에도 적용 가능

JSX에서 style 속성을 넣을 땐 style='font-size  :16px'> 의 문법이 아닌,
style = { object 자료형으로 만든 스타일 } 같이 오브젝트 형식으로 삽입하여야 한다.

JSX는 camelCase 문법을 따른다

1. class 넣을 땐 className
2. 변수 넣을땐 { 변수명 }
3. style 지정 시 style = { { 지정할 스타일 } } 

## useState 사용법 ##

1. { useState } 임포트
2. useState(데이터);

state는 변수 대신 쓰는 데이터 저장공간이며, useState()를 이용하여 만든다.    
관습적인 선언 방식은 [state 데이터, state 데이터 변경 함수] = useState(데이터); 가 된다.  
문자, 숫자, array, object 등 모든 데이터를 담아둘 수 있다.   

Q. 변수에 선언하면 되지 않나 ? -> state에 데이터를 저장하는 이유는 Web이 App처럼 동작하게 만들기 위함이다.     
state 의 가장 큰 특징은 변경될 경우 HTML 이 재랜더링 되기 때문이다. (정렬, 수정 등의 액션이 일어날때 새로고침이 없어도 됨)  
자주 바뀌거나 중요한 데이터는 변수 말고 state 에 저장하는게 좋다.  
ex) 홈페이지의 이름 등의 정적인 데이터는 굳이 useState를 사용하느니 변수 선언, 하드 코딩 등도 별 상관없다.  

state 값의 변경은 state 변경 함수를 써야한다. -> state변경함수(새로운state) 

## onClick 사용법 ##

이벤트 핸들러  
onClick = { 클릭될 때 실행할 함수 }  
onClick = { () => { 실행식 } } # 파이썬의 람다와 유사  

## state값 변경 ##

array, object 등을 다룰 땐 원본을 보존하는것이 좋음 -> 변수 하나를 선언하여 원본을 담음  
ex) let copy = 원본; x -> let copy [...원본] o

state 변경함수의 특징
기존state == 신규state 일 경우 리소스 관리를 위해 변경이 되지 않음

array, object의 특징
array, object를 담은 변수에는 그 데이터가 어디 존재하는지 메모리(RAM)상 위치(index)만 저장하게 됨

*Point*
변수1 & 변수2 이 RAM 을 가르키는 위치가 같게 되면, 변수1 == 변수2 를 비교해도 True가 된다. - console.log(copy == 글제목);
referance data type 이라는 특징
