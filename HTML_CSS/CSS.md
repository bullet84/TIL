# CSS
## 설명
|내용|설명|
|:--|:--|
|`<stlye></style>`|해당 태그 안에 들어오는 코드는 CSS를 따라서 해석|
|`font-size`|px : 폰트 사이즈 변하지 않음<br> em, rem : 폰트 사이즈 변경 가능|
|`color`|color name : 몇가지 색상의 이름이 정해져 있음<br> RGB : rgb(0~255,0~255,0~255)형식으로 표현<br> hex(16진수) : #ff0000 형식 (rgb와 크게 다르지 않음)|
|`text-align`|left , center, right : 왼쪽, 가운데, 오른쪽 정렬<br> justify : 양쪽 균등 정렬|
|`font-family`|글꼴 설정(글꼴 이름이 띄어쓰기가 되어 있는 경우 ""로 묶어줘야함<br> serif : 장식이 있는 글꼴<br> sans-serif : 장식이 없는 글꼴<br> monospace : 고정 폭|
|`font-weight`|폰트의 두께 bold를 사용하면 두껍게|
|`line-height`|줄 간격 설정|
|`font`|`font-style font-variant font-weight font-size/line-height font-family|caption|icon|menu|message-box|small-caption|status-bar|initial|inherit;`<br> 폰트와 관련된 여러 속성을 축양형으로 표현하는 속성<br> <b>font-size</b>,<b>font-family</b>는 필수 포함|


## CSS를 삽입하는 두가지 방법
### 태그에 직접설정
```
<h1 style="color:red">Hello World</h1>
```

### style 태그를 이용
```
<style>
    h2{color:blue}
</style>

<h2>Hello World</h2>
```

## 선택자(selector)
### 태그 선택자
```
<style>
    li{color:red}
</style>

<ul>
    <li>A</li>
    <li>B</li>
    <li>C</li>
</ul>
```
>모든 li태그에 적용된다, 태그를 통해 사용

### id 선택자
```
<style>
    #select{font-size:100px}
</style>

<ul>
    <li>A</li>
    <li id="select">B</li>
    <li>C</li>
</ul>
```
>id가 select인 태그에만 적용된다, #id를 통해 사용 (같은 아이디를 중복사용 하면 안된다)

### class 선택자
```
<style>
    #select{font-size:100px}
    .deactive{text-decoration: lijne-through}
</style>

<ul>
    <li class="deactive">A</li>
    <li id="select">B</li>
    <li class="deactive">C</li>
</ul>
```
>class가 deactive인 태그에 적용된다, .class를 통해 사용

### 부모 자식 선택자
```
<style>
    ul li{color:red}
    #lecture>li{color:blue}
    ul, ol{background-color:powerblue}
</style>

<ul>
    <li>A</li>
    <li>B</li>
    <li>C</li>
</ul>
<ol id="lecture">
    <li>A</li>
    <li>B
        <ul>
            <li>a</li>
            <li>b</li>
    </li>
    <li>C</li>
</ol>
```
>ul li : ul 밑에있는 li에 적용<br>
#lecture>li : lecture 바로 밑에 있는 li에만 적용<br>
ul, ol : ul 과 ol 에 동등하게 적용

[CSS 설명](https://opentutorials.org/module/2367/13339)