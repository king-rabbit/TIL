# 자바스크립트 DOM & EVENT

# DOM?

- Document Object Model 의 약자
- HTML 문서의 요소를 트리 형식으로 표현. 하나의 객체가 노드이며 부모 노드 - 자식 노드의 관계를 갖게 됨. 최상단이 루트 노드.
- 자바스트립트를 이용해서 요소를 생성하거나 수정, 삭제할 수 있음.

### document에 접근하기

```jsx
document.documentElement; // 문서에 접근
document.body; //body에 접근
document.head; //head에 접근
```

### 스타일 제어하기

```jsx
document.body.style; // 스타일 객체에 접근
document.body.style.opaticy = '0.5'; // 반투명
document.body.style.padding = '100px'; // 패딩 주기
```

### id, tag로 접근하기

```jsx
const el = document.getElementById('first'); //id는 문서당 1번만 사용할 수 있음!!

const pList = document.getElementsByTagName('p');
// 반복문으로 스타일 변경하기
for(p of pList){
	p.style.fontSize='30px';
}
for(p of pList){
	p.style.opacity = String(Math.random());
}
```

### class 이름, 노드 이름으로 접근하기

```jsx
document.getElementByClassName('link');
```

### querySelectorAll

```jsx
document.querySelectorAll('.link');  //class명으로 조회
document.querySelector('#first'); //id명으로 조회

document.querySelector('h3:nth-of-type(2)'); // h3중 2번째 요소를 가져옴
document.querySelector('h3:nth-of-type(2)').style.color = 'red'; // 스타일 변경

const pList = document.quertSelectorAll('p:nth-of-type(2n)') // 짝수번째 p 태그들만 선택
for(p of pList){
	p.style.backgroundColor='#000';
	p.style.color = '#fff';
}
```

### NodeList와 HTMLCollection의 자치

- .querySelectorAll ⇒ NodeList를 반환
- .getElementsByTagName ⇒ HTMLCollection을 반환
- NodeList와 달리 HTMLCollection은 요소의 변동상황을 실시간으로 반영함.

## 부모/자식/형제 노드 접근하기

```jsx
const red = document.getElementById('red');

//부모 노드 접근하기
red.parentNode; //부모 노드를 반환한다 (공백 등도 text로 인식해 모두 가져옴)
red.parentElement; //부모 노드 중에 '요소 노드(html 태그로 이뤄진 노드)'만 반환

//자식 노드 접근하기
const ul = document.getElementById('color');
ul.childNodes; //NodeList 반환 
ul.children; //HTMLCollection 반환
ul.firstChild; //첫번째 자식 노드 반환
ul.lastChild; //마지막 자식 노드 반환
ul.firstElementChild; // 첫번째 자식 요소 노드 반환
ul.firstElementChild; // 마지막 자식 요소 노드 반환

//형제 노드 접근하기: 이전/다음 형제 노드 반환
const blue = document.getElementById('blue');
blue.previousSibling; // 이전 형제 노드 반환
blue.nextSibling; // 다음 형제 노드 반환
blue.previousElementSibling; // 이전 형제 요소 노드 반환
blue.nextElementSibling; // 다음 형제 요소 노드 반환
```

## 노드 수정하기

```jsx

```