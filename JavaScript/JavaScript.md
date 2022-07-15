# JavaScript
## 설명
|내용|설명|
|:--|:--|
|`<script></script>`|안에 들어오는 내용은 자바 스크립트임을 알려준다|
|`on'이벤트'`|몇몇 이벤트가 발생 되었을 때 뒤에 오는 코드를 실행 시킨다|
|`typeof "내용"`|타입 확인, 결과 문자열로 반환|

## 변수 선언
`var` : 변수 재선언 가능, 변수 재할당 가능

`let` : 변수 재선언 불가능, 변수 재할당 가능

`const` : 변수 재선언 불가능, 변수 재할당 불가능

## 연산자
### 대입 연산자
`=`
### 산술 연산자
`+`,`-`,`*`,`/`,`%`,`**`
### 비교 연산자
`===`:==<br>
`!==`:!=<br>
`&&`:and<br>
`||`:or



## 제어할 태그 선택
``` javascript
//아이디로 찾기
document.getElementById('아이디');

//클래스명으로 찾기
document.getElementsByClassName('클래스명');

//태그이름으로 찾기
document.getElementsByTagName('태그이름');

//CSS Selector로 찾기
//id 찾을때는 앞에 #, Class로 선택시 앞에 .
document.querySelector('CSS Selector');		//한개
document.querySelectorAll('CSS Selector');	//여러개
```
> getElemet 에서 id는 단수 class와 tag는 복수로 사용
>* id는 한개밖에 없기 때문

>querySelector와 querySelectorAll도 마찬가지

## 조건문
``` javascript
if(조건문){
    동작
} else if(조건문2){
    동작2
}else{
    동작3
}
```
>조건문 true-> 동작 실행<br>
조건문 false-> 조건문2 true-> 동작2 실행<br>
조건문 false-> 조건문2 false-> 동작3 실행

## 리팩토링 중복의 제거
`this` : 태그 자신은 가르키는 코드<br>
변수를 설정하여 같은 내용을 중복 사용하지 않도록 한다

## 반복문
``` javascript
while(조건문){
    동작
}
```
>조건문이 false가 될 때 까지 반복

## 함수
```javascript
funcrtion 함수명(){
    명령1;
    명령2;
    return value;
}

함수명(); //함수 호출
```

## 객체
```javascript
객체명={명칭:내용} //객체를 생성
객체명.명칭 //객체에서 내용을 가져옴
객체명.명칭=내용 //객체에 내용 추가
객체명[명칭]=내용 //명칭에 띄어쓰기가 있는 경우

for(ver key in 객체명){} //객체의 모든 키 값을 가져옴
객체명[key] //key에 해당하는 정보

객체명.함수명=function(){} //객체에 함수를 추가
객체명.함수명() //객체 안에 있는 함수를 실행
```

## 파일
javascript를 다루는 파일을 따로 생성<br>
`<script src=파일명></script>`를 통해 javascript를 적용

---
[javascript](https://opentutorials.org/course/3085/18868)