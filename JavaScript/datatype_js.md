
# 자바스크립트,JavaScript


> 브라우저(클라이언트)에 자바스크립트 코드가 전달되므로 민감한 코드를 작성하지 않아야 한다!

- HTML문서에서 요소들의 동작을 제어하는 언어

    ex) `button` 을 클릭했을때 발생하는 이벤트 처리

- HTML문서 `head` 태그 안에 `script` 태그를 작성하여 자바스크립트 코드를 작성한다
- 브라우저의 자바 스크립트 엔진에 의해 인터프리트 방식으로 실행되므로 빠른 시간 내에 스크립트 코드를 작성할 수 있다

    → 인터프리트 방식 : 코드를 실행할 때 필요한 부분만 곧바로 번역하여 기능을 수행한다

- 자바스크립트 파일(.js)을 HTML문서 외부에 두고 가져와 사용하기도 한다
- 브라우저(클라이언트 측 웹)에 의해 해석되고 실행된다
- HTML, CSS와는 달리 겉으로 보이지 않는 동적인 기능을 수행한다

> Javascript는 인터프리트 형태 자바가 아니다!

- 언어학습의 편의성을 위해 java와 C++의 언어구조의 구문 일부를 사용하며 거의 비슷한 동작을 수행한다
- 객체 기반이지만 상속과 클래스의 개념은 없다
- 절차지향(prcedural) + 객체지향(object oriented), 두 형태로 만들 수 있다

    → 실시간으로 빈 객체를 오버라이딩하여 메소드와 프로퍼티를 연결한다

## JS 데이터 타입

⇒ 자바 스크립트의 데이터 타입은 `typeof()` 연산자를 통해 조회할 수 있다

```jsx
console.log(typeof(123)) // number

console.log(typeof({a:1, b:2})) //object

console.log(typeof([1,2,3])) //object
```

- Number : 숫자
- String : 문자
- Boolean : 논리
- Object : 객체

    ⇒ `{객체}` , `{키1:값1, 키2:값2, ...}` 형태로 표현한다

    ```jsx
    //object타입, 객체
    console.log({}) //빈 객체(empty object)
    console.log({"A" :123,  "B" :true, "C": "Cherry"})
    	//키(key)는 String 타입이다
    	//값(value)는 자바스트립트 데이터로 표현
    console.log({A:123, B:true, C:"Cherry"})
    	//키(key)는 반드시 String 타입이어야 한다
    	//" "를 생략해도 String 으로 인식한다
    ```

- Array : 배열

    ⇒ `[배열]` , `[요소1, 요소2, ...]` 형태로 표현한다

    ```jsx
    //Array타입, 배열
    console.log([]) //빈 배열
    console.log([1,2,3,4,5])
    console.log([123,'abc', true, null, {a:1, b:2}, ['a',5]])
    ```

    ※ Array타입은 자바스크립트 내부에서 object 타입을 이용하여 구현되어 있다

- null : 참조 대상이 없음을 나타내는 키워드(비어있음)
- undefined :  값이 정의되지 않은 상태를 표현

    → 변수도 만들어지지 않음 ,값이 생성되지 않음

- NaN : Not a Number의 약자

    → Number타입의 특수 키워드

    → Number 타입으로 값이 사용되어야 할 때  Number가 아닌 데이터를 사용하면 반환

- Infinity : 무한대

     - Number타입의 특수 키워드

     - 특정 숫자를 0으로 나누었을 때 표현되는 특수 데이터

    - `Infinity` → 양의 무한대
    - `-Infinity` → 음의 무한대
    - `isfinite()` 함수를 통해 전달 인자값이 유한한 값인지(!Infinity) 확인할 수 있다

    ```jsx
    var y = 123;
    if(isFinite(y)){ // true, 유한한 값을 가질때 조건문 수행 }
    ```

### ※ undefined 키워드와 null 키워드의 관계

- undefined 키워드

     - 변수가 초기화되지 않은 상태

     - 변수의 데이터 타입, 값이 결정되지 않은 상태( 변수는 존재한다)

- null 키워드

     - object타입의 키워드

     - 참조대상이 없음

     - 참조형 변수의 값을 일부러 비워둔 상태

### JS 자동 형변환

---

- 자동 형 변환
    - String 타입과  '+'연산을 하면 문자열로 변환된다

        **Number** + **String** = **String, Boolean** + **String** = **String**

        ```jsx
        console.log(50 +'50') //5050
        console.log('50' + 50) //5050

        console.log(true + 'Hello') //trueHello
        console.log('HI' + false) //HIfalse
        ```

    - Boolean타입과 Number타입을 '+'연산하면 Boolean타입을 숫자로 취급한다
    - true == 1, false == 0

        ```jsx
        console.log(true + 11) // number, 12
        console.log(false + 11) // number, 11
        ```

- 강제 형 변환
    - 문자 → 숫자
        - parseInt("숫자형식문자")    ⇒ 정수값 반환
        parseFloat("숫자형식문자")   ⇒ 실수값 반환
        Number("숫자형식문자")      ⇒ 정수, 실수 가능

        ```jsx
        console.log(parseInt("123.456")) // 123
        console.log(parseFloat("123.456")) // 123.456
        console.log(Number("123.456")) // 123.456
        ```

        - 숫자형과 문자형이 합쳐진 문자열일 경우 문자형 바로 앞 숫자형까지만 숫자로 반환한다

        ```jsx
        console.log(parseInt("50")) //50
        console.log(parseInt("123HI")) //123
        console.log(parseInt("HI123")) // NaN(숫자로 나타낼 수 없음)
        console.log(parseInt("456HI123")) // 456
        ```

    - 숫자 → 문자
        - 숫자데이터.toString(n)  ⇒ 정수를 진법을 지정하여 문자로 변환
        숫자데이터.toFixed(n)  ⇒ 소수점 자릿수를 지정하여 문자로 변환
        String(숫자)  ⇒ 숫자를 문자로 변환

        ```jsx
        var n1 = 567.89;

        console.log(n1.toString()) //10진수로 변환, "567.89"
        console.log(n1.toFixed(1)) //소수점 첫째자리까지 변환, "567.8"
        console.log(String(567.89)) // "567.89"
        ```

### ※ =, ==, === 연산자

---

- = 연산자 : 대입 연산자
- == 연산자 :  동등비교 연산자(**추상** 동등 비교, Abstract Equality Comparison)

    → 피 연산자가의 데이터 타입이 다를 경우 타입을 강제로 변환하여 비교한다

    → 동등 비교 규칙이 따로 정해져 있다

    ```jsx
    var data;
    console.log(data) //undefined, 값이 정해지지 않음
    if( data == undefined){} // true, 실행됨
    if( data == null){} // true, 실행됨
    ```

- === 연산자 : 동등비교 연산자(**강력** 동등 비교, Strict Equality Comparison)

    → 데이터 타입을 먼저 비교 후, 같은 타일일 때에만 비교한다

    ```jsx
    var data;
    console.log(data) //undefined, 값이 정해지지 않음
    if( data === null){} //false, 실행되지 않음
    ```

> 일부 데이터타입은 논리값이 아니어도 논리연산에서 **false**처럼 여겨진다

- 논리 연산에서 false처럼 여겨지는 데이터들

    ```undefined
     null
     false
     NaN
     0
     "" 
