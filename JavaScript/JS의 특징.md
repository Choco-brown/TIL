JS의 특징

## 변수의 범위(Scope)는 어디까지인가?

---

- JavaScript엔진은 코드를 실행하기 전(정적인 시점)에 선언된 변수를 전부 생성해둔다

  → 단, 생성된 변수는 초기화하지 않고 undefined 상태로 되어있다!

- **전역 변수**(글로벌 변수) : 어떤 변수 영역 내에서도 접근할 수 있다

  → `<script>`태그에서 곧바로 사용되고, 전역 스코프에 선언하므로 함수나 객체 어디서든 사용할 수 있다

- **지역 변수** : 변수가 선언된 영역 내에서만 접근 가능하다

  → 변수를 선언한 블록 내에서만 접근하므로 블록 영역 외에서 사용할 시 `Uncaught ReferenceError` 에러 발생

  → 중괄호 블록{ }만 있는 블록 스코프의 지역변수는 무시된다

  ```jsx
  // 전역변수 선언
  var num = 10;
  function func() {
    console.log(num);
  } // 10, 에러없이 사용 가능

  //지역변수 선언
  function f() {
    // 함수 지역 스코프
    var value = 20;
    console.log(value);
  }
  f(); //20, 에러 없이 사용 가능

  console.log(value); //에러, 지역변수는 지역스코프를 벗어나 사용할 수 없다
  ```

### 호이스팅, Hoisting

---

- "끌어올리기"
- 변수의 선언코드 또는 함수의 정의코드가 해당 스코프의 가장 첫 부분에 작성이 되어있는 것처럼 사용할 수 있도록 만드는 현상

  ※스코프, Scope : { }중괄호로 구분된 코드 영역

  → function(){ }

- 실제 코드는 영역의 첫 부분에 존재하지 않지만 미리 선언되어 있는 것처럼 사용할 수 있게 된다

  ex)

  ```jsx
  console.log(data); //에러가 나지 않음, undefined(호이스팅 현상)
  var data = 100;
  console.log(data); // 100
  ```

- 변수의 생성(Instantiation)과 초기화(Initialization)의 작업이 분리되어 진행되는 것이 원인

> 호이스팅은 변수나 함수를 사용하기 전 먼저 선언해야 한다는 규칙을 무시하므로 코드의 구조를 엉성해 보이게 만들수도 있다.

### 변수의 종류 : VAR , LET, CONST

---

- **var** : 기본 변수 선언 키워드(유연하다)

  → 같은 이름의 변수를 여러 번 선언해도 에러가 나지 않는다(하나의 변수로 취급)

  ex)

  ```jsx
  var num = 10;
  var num = 20;
  //에러 없음, data변수가 10 초기화 이후 20으로 새로 대입

  data = "hello"
  var data
  //hoisting으로 인해 에러가 발생하지 않음

  for(var i=0; i<5 ; i++{  }
  console.log(i) // 5, var지역변수는 function 스코프에만 영향을 받고 다른 블록 스코프에는 영향받지 않는다
  ```

- **let** : 추가된 변수 선언 키워드(ECMA Script 6(ES6)에서 추가됨)

  → 같은 이름의 변수로 여러 번 선언할 수 없다(`변수 재선언 불가능`)

  →

  ex)

  ```jsx
  let data = 10;
  let data = 20; //에러, 변수 재선언 불가능

  let num = 365;
  num = 678;
  console.log(num); //678, 변수 재할당 가능

  for (let j = 0; j < 5; j++) {}
  console.log(j);
  //Uncaught ReferenceError: j is not defined 에러 발생
  //let지역변수는 블록 스코프에도 영향을 받는다
  ```

- **const** : 추가된 변수 선언 키워드(ECMA Script 6(ES6)에서 추가됨)

  → let과 동작은 비슷함(`변수 재선언 불가능`)

  - 변수의 초기화는 가능하지만 이후에 대입이 되지 않는 변수(`변수 재할당 불가능`)

    (java의 final 변수와 비슷함)

  - 변수값의 초기화는 필수, 초기화하지 않으면 에러 발생

  ex)

  ```jsx
  const data; // 에러, 초기화하지 않음
  const data = 30;
  ```

**※ 변수마다 적용되는 스코프**

- var : function scope
- let, const : function scope, block scope
- var 변수는 함수 내부에서만 지역스코프 특성이 부여된다
- let, const는 블록에서 만들어진 변수라면 지역스코프 특성이 부여된다

  → let, const는 익명블록, 제어문, 함수 등등에서 지역스코프가 적용된다

**※ 호이스팅 적용**

- var, let, const 모두 호이스팅이 발생한다
- var는 선언코드 이전에 변수에 접근 가능하다
- let, const는 선언코드 이전에 변수에 접근할 수 없도록 금지하고 있다

## 콜백함수(Callback Function)

---

- 이벤트 발생이나 특정 시점에 개발자가 등록해 둔 함수가 실행된다
- 다른 시스템에 의해 호출된다.
- 특정 함수의 인자로 넘겨서 코드 내부에서 호출되는 것도 콜백 함수가 될 수 있다

```jsx
//덧셈의 결과를 저장하는 함수
function sum(n1, n2, 콜백함수) {
  var result = n1 + n2; //지역변수 result에 결과값 저장
  callback(res); //콜백함수에 result를 매개변수로 대입
}

//console로 출력해주는 함수
function display(data) {
  console.log("결과값: " + data);
} // console에 결과값: data 가 출력된다

//sum함수 호출
sum(100, 200, display);
// 결과값: 300, display()함수가 콜백함수로 호출된다
```

```jsx
//덧셈의 결과를 저장하는 함수
function sum(n1, n2, 콜백함수){
	var result = n1 + n2 //지역변수 result에 결과값 저장
	callback(res); //콜백함수에 result를 매개변수로 대입
}

//결과값을 알림창으로 출력하는 함수
function alertResult(data){
	alert("결과값은 : " + data)
}

sum함수 호출
sum(300,400,alertResult);
//결과값 : 700 알림창, alertResult()함수가 콜백함수로 호출된다
```

### 타이머(Timer)함수

---

- `setInterval(callback, millis)` : timerid

  - 지정된 밀리초마다 `callback`함수를 반복적으로 실행한다

  - 타이머 객체의 id를 반환한다

  ```jsx
  // hello를 출력하는 함수
  function hello(){
  	console.log("hello")

  //1초(1000밀리초)마다 hello 함수 호출하기
  var tid = setInterval(hello, 1000)
  ```

- `setTimeout(callback, millis)` : timerid

  - 지정된 밀리초 이후에 `callback` 함수를 한 번 실행한다

  - 타이머 객체의 id를 반환한다

  ```jsx
  //3초(3000밀리초) 이후에 hello를 출력하는 함수를 실행
  setTimeout(function(){console.log("hello)}, 3000)
  ```

- `clearInterval(timerid)` : undefined

  - 지정된 타이머 객체를 즉시 종료시킨다

  - `setInterval`, `setTimeout` 둘 모두 종료시킬 수 있다

  ```jsx
  var tid = setInterval(hello, 1000);
  function stop() {
    clearInterval(tid);
  }
  setTimeout(stop, 3000); //3초 뒤에 setInterval 타이머 객체 종료
  ```
