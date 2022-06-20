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
<br>
<br>
## 간단한작동원리 ##

App.js <-> index.js <-> index.html

index.js 에서 App.js 에 정의된것들을 가져와 index.html에 랜더링
<br>
<br>
## 디렉토리 구조 및 파일 ##
1. node_modules 폴더: 라이브러리 모음
2. public 폴더: static 파일 보관
3. src 폴더: 소스코드 보관
4. package.json : 설치한 라이브러리 목록, 프로젝트 정보
<br>
<br>
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

<br>
참고자료 : https://ko.reactjs.org/docs/jsx-in-depth.html#gatsby-focus-wrapper
<br>  
<br>
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
<br>
<br>
## onClick 사용법 ##

이벤트 핸들러  
onClick = { 클릭될 때 실행할 함수 }  
onClick = { () => { 실행식 } } # 파이썬의 람다와 유사  
<br>
## state값 변경 ##  

array, object 등을 다룰 땐 원본을 보존하는것이 좋음 -> 변수 하나를 선언하여 원본을 담음   
ex) let copy = 원본; x -> let copy [...원본] o  (JS의 문법인 전개 연산자, 파이썬의 언패킹과 유사)

state 변경함수의 특징  
기존state == 신규state 일 경우 리소스 관리를 위해 변경이 되지 않음  

array, object의 특징  
array, object를 담은 변수에는 그 데이터가 어디 존재하는지 메모리(RAM)상 위치(index)만 저장하게 됨 (포인터 개념)  
ex) arr1 = [1,2,3] -> arr2 = arr1 -> arr1 의 값 변경 -> arr2 도 같이 변경된다

*Point*  
변수1 & 변수2 이 RAM 을 가르키는 위치가 같게 되면, 변수1 == 변수2 를 비교해도 True가 된다. - console.log(copy == 글제목);  
referance data type 이라는 특징   
반드시 state 값의 변경은 state 변경 함수를 통해 변경 !  
state는 state를 사용하는 컴포넌트들 중 '최상위 컴포넌트'에 위치한다.

<br>
<br>
## 컴포넌트 문법 ##  

컴포넌트 생성  
1. function 생성  
2. return () 안에 표현하고자 하는 html 삽입  
3. <함수명></함수명> 으로 호출  
4. return 내에는 html 문법을 병렬기입하면 error 발생  
5. 병렬기입을 하고 싶다면 리액트의 fragments 문법을 사용한다.   
ex) &lt;&gt; &lt;/&gt; 의 빈태그 이용 (참고자료 : https://ko.reactjs.org/docs/fragments.html)  

또 다른 생성방법으론 변수를 전역 선언하여 생성  
ex) const 컴포넌트명 = () => { return ( 실행식 ) } # 주로 const로 만들게 된다 (수정 및 재선언이 불가능 하므로)

<br>
컴포넌트의 생성 시기  
1. 반복적인 HTML의 등장
2. 큰 페이지 (페이지의 전환)
3. 자주 변경되는 UI

컴포넌트의 특징  
1. 당연하게도 지역변수를 가져와 쓸 수 없다 (App()에 정의되어 있는 state 등을 끌어올 수 없음, 전역변수는 가능, 스코프의 개념 이해 필요)

<br>
<br>

## 동적인 UI 만들기 3steps ##

1. html, css 를 사용하여 디자인  
2. UI 의 현재 상태를 state로 저장  
3. state에 따른 UI의 노출 구상  

if 문을 html 상에 작성할 수 없어 삼항연산자(ternary operator)를 이용하여 조건문 구현  
ex) { 조건식 ? True 일 경우 output : Flase 일 경우 output }

Modal 구현

<br>
<br>

## 반복문의 구현 ##

map 사용하기  
[배열].map(function(파라미터){  
  실행식
})  
<br>
map 의 특징  
1. array의 자료 갯수만큼 함수안의 코드 실행
2. 함수의 파라미터는 array안에 있던 데이터
3. return 문 을 쓸 경우 array에 넘겨주게 됨  
4. 두번째 파라미터는 반복문이 돌때마다 0부터 1씩 증가하는 정수

마찬가지로 for 문을 작성할 수 없으므로 map 함수나 for 문을 함수로 만들어 호출

<br/>
<br/>

## props 문법 ##

부모 컴포넌트에서 자식 컴포넌트에게 state 상속이 가능하다.  -> 아래에서 위로, 옆으로는 불가능  
<br>
사용법  
1. <자식컴포넌트 props_name={ state 명 }/>
2. props 파라미터 등록 후 props.props_name 을 통해 호출  
3. 관습적으로 props 의 선언은 넘겨줄 state 명과 동일화 한다.  
4. props 에게 적용되는 문법은 파라미터 문법과 동일하다.

<br/>
<br/>

## input 태그 다루기 ##  

항상 닫는 태그가 존재 해야 한다.  
&lt;input type='원하는 타입'/&gt;  
외에 select, textarea 등 기존 html 에서의 태그들도 다 쓸 수 있음  
<br/>
이벤트 핸들러
1. onChange, onInput 등등 연계해서 사용할 수 있는 핸들러들은 매우 많음. (약 30개)

state 의 변경함수는 늦게 처리된다 → 비동기처리  

## 이벤트 버블링 방지 ##
  
하위요소에 있는 이벤트가 상위요소로 퍼지는 현상   
```html
<span onClick={ (e)=>{ e.stopPropagation(); 실행식 }}>
```  
<br/>
<br/>

## 과거 리액트 문법에 대하여 ##    
  
1. component 를 만들 때
```React
class 이름 extends React.Component {
  constructor() {
    super()
    this.state = { name : 'Test', age : 20 } // state 등도 constructor 함수 안에 정의
  }

  render(){
    return (
      <div> Test </div>
      <p> { this.state.name } </p>
    )
  }
}
```
class : 변수, 함수를 정의   
extends : React.Component 를 상속   
constructor : class의 변수, 초기값을 정의

<br>
<br>
<br>
# 이어서 정리  
<br>
<br>
## 리액트 부트스트랩 ## 
js에서도 그렇듯 레이아웃을 쉽게 짤 수 있도록 도와주는 라이브러리  
  
링크 : https://react-bootstrap.github.io/getting-started/introduction
  
## img 삽입 시 ##
1. css 파일에 background-image로 정의 
2. js 에 import 문법 정의 (import 이름 from 경로)  
  
이미지는 src, public 모두 저장 가능하며, src에서는 상대경로 public에서는 절대경로를 사용한다.


## 리액트 배포시 ##
발행 전 html, js, css 파일을 압축하게 됨 (bundling)
하지만 public 폴더에 있던건 원본 상태로 압축되지 않게 됨

<br/>
  
## import / export 문법 ##  
함수, 컴포넌트 등도 export 가능  
여러개를 export 할 땐 중괄호 안에 묶어야함

<br/>
## 싱글 페이지 어플리케이션 ## 
리액트 미사용 시 페이지 분할  
1. html 파일 생성 및 작성
2. 클라이언트가 해당 경로 페이지 요청 시 1. 에서 작성 된 html 파일 렌더링

리액트 사용 시 페이지 분할  
1. 기본적으로 싱글 페이지 어플리케이션 (index.html 하나만 존재)
2. 컴포넌트를 생성 및 작성
3. 클라이언트가 해당 경로 요청 시 컴포넌트를 렌더링
4. 이를 도와주는 라이브러리 react-router-dom 을 사용 

## 리액트 라우팅 ## 

설치 : npm install react-router-dom@6 // 6버전 설치  
<br/>
index.html
```React
root.render(
  <React.StrictMode>
    <BrowserRouter>
    <App />
    </BrowserRouter>
  </React.StrictMode>
);
```
<br/>


App.js
```React
  return (
    <div className="App">
      <Routes>
        <Route path='/detail' />
        <Route />
      </Routes>
      .
      .
      .
```
<br/>
<br/>

## 리액트 라우팅의 Nested Routes ##  

```React
      <Route path='/about' element={<About/>}>
        <Route path='member' element={<div><About/></div>}/>
        <Route path='location' element={<div><About/></div>}/>  
      </Route>
      
function About() {
 return (
  <div>
    <h4>About</h4>
    <Outlet></Outlet> // 아웃렛 설정을 해야 엘레먼트 출력
  </div>
 ) 
}
      
```

<br/>
## 훅 함수 ##  
1. useNavigate() : 페이지 이동을 도와 줌
매개 변수에 1, -1이 들어 올 경우 다음, 이전 페이지 로딩 (스택)

<br/>
<br/>
## URL 파라미터 문법 ##

리액트 라우트는 매우 다양한 편의성을 제공
```
<Route path='/detail/:id' element={<Detail data={state}/>}/>
```
useParams() 함수를 사용  
<br/>
/detail/:id/test/:asdf 등 연장 사용 가능

<br/>
## styled-components 라이브러리 ##

js 안에서 css 제어 가능  
npm 으로 라이브러리 설치 후 사용

```React
import styled from 'styled-components'

let YellowBtn = styled.button`
    background : yellow;
    color : black
    padding : 10px;
`
let Box = styled.div`
    background : ${ props => props.bg };
    color : ${ props => props.bg == 'blue' ? 'white' : 'black' };
    paddind : 20px
`

return (
  <Box bg = 'yllow'/>
)

```
이렇게 만든 변수는 컴포넌트 식으로 사용가능  
props 도 적용 가능 (삼항연산 등 간단한 프로그래밍도 가능)  

장점
1. css 파일 굳이 안열어도 됨  
2. 스타일이 다른 js파일을 오염시키지 않음 (이름.module.css 식으로 css파일을 작명하면 종속시킬 수 있음)
3. 페이지 로딩 시간 단축 됨
  
단점  
1. JS파일이 길어짐 (컴포넌트, 스타일 등 헷갈릴 수 있음)
2. 중복스타일을 export, import 하게 되면 css와 다를 바 없음  
3. 협업 시 CSS 담당의 숙련도 이슈  

## 컴포넌트의 Life Cycle ##  

1. mount : 마운트
2. update : 업데이트
3. unmount : 제거
  
useEffect() 함수 주 사용 목적  
1. 고 성능 연산 처리 요구시
2. 서버에서 데이터 가져올 시
3. 타이머 장착 시
  
SideEffect : 함수의 핵심기능과 상관없는 부가기능

## 해봐야할 것 ##
1. state -> 서버 -> DB 연동



<br/>
<br/>

## 참고하면 좋을 링크 ##
https://blog.naver.com/PostView.nhn?blogId=helicopter55&logNo=221873681114
