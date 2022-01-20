# **JavaScript**

> **JavaScript**

JavaScript(이하 **JS**)는 웹 개발에서 콘텐츠를 바꾸고 움직이는 등 페이지의 동적 처리를 담당한다.

<br/>
<br/>

# **타입**

## **String**
```js
const str = "Hello, world!";
```
String은 문자열 리터럴을 말하며, 따옴표로 감싸서 작성한다. 

우리가 흔히 말하는 문자, 글자는 물론 숫자 또한 따옴표로 감싸서 작성하면 문자열 리터럴이 된다.

백틱(``)으로 감싸는 작성법은 **보간법**으로, `${}`를 이용하여 변수에 할당된 값을 출력하는 기능을 갖고 있다.

<br/>

## **Number**  
```js
const num = 123;
```
정수(int) 및 부동소수점(float) 숫자를 말한다.

<br/>

## **Boolean**  
```js
const isTrue = true;
const isFalse = false;
```
`true`와 `false`로 이루어진 논리 데이터 형식이다.

Boolean이 아니지만 `true`, `false`와 같은 의미를 갖는 값이 존재한다.  

- **참과 같은 값**  
true, {}, [], 1, 2, 'false', -5, '0.123'  
그 외 등등 모든 비어있지 않은 문자열과 0을 제외한 수는 참과 같은 의미를 갖는다.

- **거짓과 같은 값**  
false, "", '', ``, null, undefined, 0, -0, Nan  
거짓과 같은 값은 위에 나열한 내용이 전부이다. 위의 값을 제외한 다른 모든 값은 참과 같은 값이라고 볼 수 있다.

<br/>

## **Undefined**  
```js
const empty;
console.log(empty); // undefined
```
값이 할당되지 않은 상태를 나타낸다.

<br/>

## **Null**
```js
const empty = null;
console.log(empty); // null
```
값이 **의도적**으로 비어있음을 의미한다.

<br/>

## **Symbol**
```js
const symbol1 = Symbol("symbol1");
const symbol2 = Symbol("symbol2");
```
심볼은 변경 불가능한 원시 타입의 값이며 다른 값과 중복되지 않는다.  

충돌할 위험이 없는 객체의 프로퍼티 키를 만들기 위해 사용이 가능하다.

인자로 문자열을 전달할 수 있는데, 이는 심볼 값에 영향이 없고 단순한 설명에 불과하다. 디버깅 용도로 사용된다.

`Symbol()` 함수를 호출하여 생성된 심볼은 모두 각자 고유한 값을 갖게 된다.  

따라서 각 심볼은 비교연산자를 통해 비교하였을 때 `false`가 반환된다.

같은 값을 갖는 심볼을 사용하고 싶을 때는 아래의 방법을 사용한다.

```js
const symbol1 = Symbol("symbol1");

const symbol2 = symbol1

// 혹은 Symbol.for() 사용

const symbol1 = Symbol.for("symbol");
const symbol2 = Symbol.for("symbol");
```

심볼의 사용 예시
```js
const apple = Symbol();

const obj = {
  apple: "사과",
  [apple]: "애플"
};

console.log(obj.apple);  // 사과
console.log(obj.[apple]);  // 애플

```

<br/>

## **Object**
```js
const me = {
  name: "RAREBEEF",
  age: 4
};


console.log(me.name);
console.log(me["age"]);
```
객체라고 부르며, **직접 값을 갖지 않고** 다른 데이터들을 `key: value` 쌍으로 저장한다.  

중괄호로 감싸서 작성한다.

객체 내에 저장된 함수는 **메소드**라고 부른다. 후술.

객체에 저장된 데이터의 참조는 두가지 방법이 있다.

- `객체명.key`

- `객체명["key"]`

<br/>

## **Array**  
```js
const arr = [1, true, 3, "a", 4, "b"]

console.log(arr[0]); // 1
console.log(arr[3]); // "a"
```
배열이라고 부르며, 여러 데이터들을 **순차적**으로 저장한다.

대괄호로 감싸서 작성한다.

배열 내의 데이터는 순서대로 index를 부여 받으며,  
이 index를 통해 각 데이터를 참조할 수 있다.

# **연산자**
## **산술 연산자**
덧셈, 곱셈 등 계산에 쓰이는 연산자를 말한다.  

\+ : 덧셈

\- : 뻴셈

\* : 곱셈

\/ : 나눗셈

% : 나머지 연산자 (나머지를 반환한다.)

<br/>

## **할당 연산자**  
값을 할당할 때 쓰는 연산자를 말한다.  

`=` 을 사용하며, 부가적인 연산자를 붙여서 사용하기도 한다.
```js
let a = 2; // 변수 a에 2 할당
a += 1; // a에 1을 더하고 a에 할당
a -= 1; // a에서 1을 빼고 a에 할당
a *= 2; // a에 2를 곱하고 a에 할당
a /= 2; // a를 2로 나누고 a에 할당
a %= 1; // a를 1로 나눈 나머지를 a에 할당
```

<br/>

## **비교 연산자**  
좌항과 우항의 값을 비교하여 boolean 값으로 반환한다.  
```js
const a = 1;
const b = 1;
const c = 2;

a === b // 값이 완전히 같은가? true
a === c // 값이 완전히 같은가? false
1 === "1" // 값이 완전히 같은가? false
1 == "1" // 값이 같은가? true
a !== b // 값이 다른가? false
a < c // 좌항보다 우항이 더 큰가? true
a > c // 우항보다 좌항이 더 큰가? false
a <= c // 좌항보다 우항이 더 크거나 같은가? true
a >= b // 우항보다 좌항이 더 크거나 같은가? true
```

<br/>

## **논리 연산자**  
- `&&`  
and, 좌항과 우항이 모두 true일 때만 true 반환  

- `||`  
or, 좌항과 우항 중 하나만 true여도 true 반환  

- `!`  
not, 반대되는 값을 말한다.  
`!true == false`

<br/>

## **삼항 연산자**
`?`의 좌항이 true일 경우 `:`의 좌항을,  
false일 경우 `:`의 우항을 반환한다.
```js
const a = 1;

a === 1 ? '참' : '거짓'  // '참'
```

<br/>
<br/>

# **변수**
변수는 데이터를 저장하고 참조하는 데이터의 이름을 말한다.

변수의 사용은 선언과 초기화, 그리고 할당의 과정을 거친다.

1. 선언 & 초기화  
`const a;`  
a라는 이름을 변수로 사용하겠다고 선언하는 것을 말한다.  
또한 선언될 때 undefined 값을 갖게 된다.(초기화)

1. 할당  
`a = 1`  
변수에 원하는 데이터를 할당하는 것을 말한다.

이 두 과정을 하나로 단축시킬 수 있다.

1. 선언 & 초기화 & 할당  
`const a = 1;`  
a라는 이름을 변수로 사용하겠다고 선언 & 초기화 후 1이라는 값을 할당한다.

<br/>

## **변수의 종류**

### **`var`**
Function level scope,  
**오직 함수에서 선언된 변수만 지역변수**로 취급한다.

**중복 선언과 재할당이 가능하다.**

많은 경우에서 전역변수 취급을 받고, 중복 선언까지 가능하기 때문에 다른 전역변수를 덮어 쓸 위험이 존재한다.  
따라서 사용하지 않는 것을 권장한다.

<br/>

### **`let`**  
Block level scope,  
{}로 이루어진 스코프 내에서 선언된 변수는 지역변수로 취급한다.  
이 스코프는 함수, 제어문, 반복문 등을 말한다. 

for문은 스코프 밖에서 변수가 선언되지만 예외적으로 지역변수로 취급 받는다.

**재할당은 가능**하지만 **중복 선언은 불가능**하다.

<br/>

### **`const`**
Block level scope,  
{}로 이루어진 스코프 내에서 선언된 변수는 지역변수로 취급한다.  
이 스크포는 함수, 제어문, 반복문 등을 말한다.

for문은 스코프 밖에서 변수가 선언되지만 예외적으로 지역변수로 취급 받는다.

`let`과 거의 동일하지만 유일한 차이점은  
**재할당과 중복 선언이 모두 불가능**하다는 점이다.

<br/>

## **변수의 호이스팅** 

변수의 호이스팅이란, 코드가 실행되기 이전에 JS 엔진이 코드를 미리 훑어보고 변수를 찾아두는 것을 말한다. 

함수의 호이스팅도 존재한다. 후술.

`var`과 `let`, `const`는 호이스팅의 동작 방식에 차이가 있다.

<br/>

### **`var` 호이스팅**

`var`은 호이스팅 단계에서 선언과 초기화가 실행된다. 

따라서 변수의 선언 이전에 호출이 먼저 등장하여도 에러가 발생하지 않는다.

다만 할당은 함수의 선언문에서 실행되기 때문에 `undefined`가 출력된다.
```js
console.log(a); // undefined

var a = 1;

console.log(a); // 1
```

<br/>

### **`let`, `const` 호이스팅**

`let`과 `const`는 호이스팅 단계에서 선언만 실행된다.

변수의 선언 이전에 호출이 먼저 등장할 경우 **초기화가 실행되지 않았기 때문에** 값이 아예 없어서 에러가 발생한다.   

따라서 호이스팅이 없는 것처럼 보일 수 있다.
```js
console.log(a); // Uncaught ReferenceError: a is not defined

const a = 1;

console.log(a); // 1
```
이처럼 변수의 **선언과 초기화 사이**에 변수가 일시적 사각지대에 들어가서 **값을 참조할 수 없는 구간**을 **TDZ**(Temporal Dead Zone)라고 부른다.

여전히 `let`과 `const`는 호이스팅이 없는 것처럼 느껴질 수 있다.  

아래의 예시를 통해 호이스팅이 이루어진다는 것을 알 수 있다.  
함수, 지역변수 & 전역변수의 범위와 우선순위에 대해 이해가 없다면 이해하기 힘들 수 있다. 
```js
let a = 1; // 전역변수 a 선언

function func() {
  console.log(a);  // a 호출
  let a = 1;  // 지역변수 a 선언
};

func(); // Uncaught ReferenceError: a is not defined
```
위의 예시에서 전역변수 `a`는 이미 선언과 초기화, 할당까지 완료되어 호출에 전혀 문제가 없는 상태이다.  

하지만 함수를 통해 변수 `a`를 호출하였을 때 에러가 발생하였다.  

이는 JS 엔진이 지역변수 `a`의 존재를 호이스팅을 통해 이미 알고있는 상태이고 변수의 우선순위에 따라 지역변수 `a`를 참조하려 하였으나 초기화가 이루어지지 않았기에 에러가 발생하는 것이다.

<br/>
<br/>

# **조건문**

조건의 결과(`true`, `false`)에 따라 다른 내용을 실행하는 코드이다.

조건문의 종류로는 `if`, `switch` 두 가지가 있으며,  
주로 `if`문이 쓰이지만 조건의 내용이 특정한 값으로 딱 떨어지는 경우에는 가독성을 위해 `switch`문을 사용하기도 한다.

<br/>

## **`if`**
```js
const a = 1;

if (a === 1) {          // a가 1일 경우
  console.log(1);
} else if (a === 2) {   // a가 2일 경우
  console.log(2);
} else {                // 나머지 경우
  console.log("I don't know.");
};

// 실행 결과 : 1
```

<br/>

## **`switch`**
`switch`문의 경우 각 조건의 실행이 종료될 때 `break`를 통해 `switch`문을 종료시켜주어야 한다.  

나머지 경우를 말하는 `default`의 경우 어차피 마지막이기 때문에 `break`를 생략해도 된다.
```js
const a = 9;

switch (a) {
  case 1: console.log(1); break
  case 2: console.log(2); break
  default: console.log("I don't know.");
}

// 실행 결과 : "I don't know."
```

<br/>
<br/>

# **반복문**

특정 코드를 반복할 때 사용한다.  

`for (시작조건; 종료조건; 변화조건) {반복내용};`  
위의 구조를 갖는다.

각 조건은 보통 아래의 역할을 맡게 된다.

- 시작조건  
반복문의 횟수를 체크할 변수를 선언 & 초기화한다.

- 종료조건  
반복문이 종료되는 조건을 설정한다.  

- 변화조건  
반복문이 1회 반복된 후에 실행할 내용을 설정한다.

```js
// i는 0으로 시작해서 1회 반복된 후 +1,
// i가 5보다 작을 경우 반복
// 반복 시 마다 i의 값 출력

for (let i=0; i<5; i++) {
  console.log(i);
};

// 실행 결과 : 0, 1, 2, 3, 4
```

위의 문법 외에 `for in`, 그리고 `for of`도 존재한다.  
여기서는 `for of`만 설명한다.

<br/>

## **`for of`**
for문에 객체를 전달하고, 그 객체 내부의 요소를 반복문이 순차적으로 꺼내서 내용을 실행한다.  

반복문이 요소를 호출할 때 사용할 변수명을 지정할 수 있다.
```js
const arr = [1, 2, 3, 4, 5];

for (num of arr) {
  console.log(num);
};

// 실행 결과 : 1, 2, 3, 4, 5
```

<br/>
<br/>

# **함수**
함수는 특정 기능을 수행하는 코드의 집합이다.  

한 번 만들어두면 재사용이 용이하다는 장점이 있다.

<br/>

## **함수의 기본 구조**
```js
function 함수명() {
  함수내용
};

//함수의 호출
함수명();
```

<br/>

## **함수의 반환값**

반환값(`return`)은 함수가 호출되어 실행된 후에 함수가 내놓는 값, 즉 결과물을 말한다.

함수에 반환값이 존재할 때 이 함수의 호출을 변수에 할당한다면 결과적으로는 함수의 반환값이 변수에 할당된다.

반환값이 함수에 있어서 필수적인 요소는 아니다.
```js
function func() {
  return 1
};

const a = func();

console.log(a); // 1
```
또한 `return`은 함수의 실행이 종료되는 시점을 나타내기도 한다. 

따라서 `return`이 실행되고 나면 그 뒤에 남은 함수의 내용은 실행되지 않는다.

이를 통해 특정 조건에 부합할 경우 함수의 실행을 종료시키는 코드를 작성할 수도 있다.

<br/>

## **함수의 전달값**

함수는 전달값이란 개념으로 **매개변수(parameters)** 와 **인자(arguments)** 를 갖고 있다.  

이 둘은 거의 같은 의미라고 볼 수 있다.  

함수를 호출할 때 함수에 전달하는 값을 인자, 전달 받은 인자를 저장할 변수를 매개변수라고 부른다.  

결국 하나의 함수에서 매개변수와 인자는 같은 값을 갖게 된다.

함수의 동작에서 필요한 값, 혹은 특정 로직을 거칠 값을 전달값으로 전달한다.

반환값과 마찬가지로 필수적인 요소는 아니다.
```js
function sum(a, b) {     // 매개변수 선언
  return a + b           // 매개변수를 더해서 반환
};

console.log(sum(1, 2));  // 인자로 1, 2를 전달

// 실행 결과 : 3
```

<br/>

## **`arguments`**

함수의 선언 단계에서 매개변수를 선언하지 않았어도 함수에 인자를 전달할 수 있고, 함수는 이 인자를 참조할 수 있다.  

함수가 전달받은 인자는 `arguments` 라는 배열 객체에 순서대로 저장된다.

정확한 매개변수를 함수의 선언 단계에서 함께 선언하는 것이 좋지만, 인자의 개수가 특정되지 않는 상황에서 유용하게 사용할 수 있다.
```js
function sum() {
  let answer = 0;
  for (let i=0; i<arguments.length; i++) {
    answer += arguments[i];
  };
  return answer
};

console.log(sum(1, 2, 3, 4, 5)); // 실행 결과 : 15
```

<br/>

## **익명 함수**
말 그대로 이름이 없는 함수를 익명 함수라고 부른다.  

익명 함수는 선언한다가 아닌 표현한다고 말한다.

익명 함수는 이름이 없어서 일반적인 방법으로는 호출이 불가능하다.  

따라서 표현 단계에서 변수에 할당하거나, 혹은 표현과 동시에 호출한 후 버리는 1회성 함수로 사용한다.

이러한 1회성 함수는 **IIFE(Immediatly-Invoked Function Expression), 즉시 실행 함수**라고 부른다.
```js
// 변수에 할당
const a = function () {
  return "a"
};

// 즉시 실행 함수 1
(function () {
  return "a"
})();

// 즉시 실행 함수 2
(function () {
  return "a"
}());
```

<br/>

## **메소드**  
```js
const me = {
  name: "RAREBEEF",
  age: 4,
  getName: function () {
    return this.name
  };
};

console.log(getName());  
// 실행 결과 : "RAREBEEF"
```
객체 내에 저장된 함수는 메소드라고 부른다.  

메소드에서는 this라는 변수를 사용 가능하다.  
이 this는 메소드 자신이 포함된 부모 객체를 말한다.  
자세한 내용은 후술.

메소드의 호출은 크게 두가지 방법으로 가능하다.

- `객체명.메소드명()`  

- `const 변수명 = 객체명.메소드명(); 변수명;`

<br/>

## **화살표 함수**  
화살표 함수를 사용하면 함수의 선언을 축약시킬 수 있다.
```js
// 일반 함수
function func(a) {
  return a
};

// 화살표 함수, function 생략
const func = (a) => {
  return a
};

// 함수 내용이 return문 하나만 존재한다면 더 축약할 수 있다.
// 화살표 함수, function & {} & return 생략
const func = (a) => a;

// 매개변수가 하나라면 더 축약할 수 있다.
// 화살표 함수, function & {} & return & () 생략
const func = a => a;
```
화살표 함수 사용 시 반환값으로 객체 데이터를 사용할 경우 객체의 중괄호를 소괄호로 한 번 감싸서 `({객체내용})` 구조로 사용해야한다. 화살표 함수가 반환값 객체의 중괄호를 함수 스코프로 인식하기 때문이다.

<br/>

## **콜백 함수**
콜백 함수는 다른 함수의 인자로 사용된 함수를 말한다.  

콜백 매개변수의 이름은 마음대로 선언이 가능하지만 보통 구분을 위해 `callback` 혹은 `cb`와 같이 선언한다.

이 매개변수를 통해 함수의 로직 내에서 전달 받은 콜백 함수의 실행 위치를 지정할 수 있다.
```js
function myName() {
  console.log("소고기는레어");
};

function waterMark(cb) {
  cb();
  console.log("RAREBEEF");
};

waterMark(myName);
// 실행 결과
// "소고기는레어"
// "RAREBEEF"
```

## **타이머 함수**
타이머 함수는 지정한 시간을 바탕으로 실행되는 함수이다. 시간의 단위는 ms이다.

- `setTimeout(함수, 시간)`  
일정 시간 후 함수 실행

- `clearTimeout(함수명)`  
Timeout 함수 종료

- `setInterval(함수, 시간)`  
일정 시간 간격마다 함수 실행

- `clearInterval(함수명)`  
Interval 함수 종료

```js
// 1초 간격으로 콘솔 로그 출력
const timer = setTInterval(() => {
  console.log("RAREBEEF");
}, 1000);

// 10초 후 타이밍 함수 종료
setTimeout(() => {
  clearInterval(timer);
}, 10000);
```

<br/>

## **this**
`this`는 함수가 자신의 부모 객체를 가리키는 변수이다.  

함수는 `this`를 통해 자신의 부모 객체가 갖고 있는 데이터를 참조할 수 있는데, 일반 함수와 화살표 함수는 이 `this`를 정의하는 기준이 다르다.

- 일반 함수  
**호출 위치**에서 `this`를 정의한다.

- 화살표 함수  
**자신이 선언된 함수 범위**에서 `this`가 정의된다.

<br/>

### **첫번째 예시**
```js
const obj = {
  name: "rarebeef",
  // 일반 함수
  nomalFunc: function () {console.log(this.name);},
  // 화살표 함수
  arrowFunc: () => console.log(this.name);
};

obj.nomalFunc(); // rarebeef
obj.arrowFunc(); // undefined
```
두 함수(메소드) 모두 `this.name`을 참조하여 출력을 시도하였다.  

일반 함수의 `this`는 호출 위치에서 정의된다.  
위 예시에서 일반 함수의 호출 위치는 객체 `obj`이고, 따라서 `this`는 `obj`를 말한다.

화살표 함수의 `this`는 자신이 선언된 함수 범위에서 정의된다.  
하지만 위 예시에서 화살표 함수를 감싸고 있는 부모 함수는 존재하지 않는다. 따라서 `this`의 정의 조건에 부합하지 않고 undefined를 출력하게 된다.

<br/>

### **두번째 예시**
```js
const timer = {
  message: "Hi",

  
  nomalFunc: function () {
    setTimeout(function () {     // 일반 함수
      console.log(this.message);
    }, 1000)
  },
  
  arrowFunc: function () {
    setTimeout(() => {           // 화살표 함수
      console.log(this.message);
    }, 1000)
  }

};

timer.nomalFunc(); // undefined
timer.arrowFunc(); // "Hi"
```
두 함수 모두 **타이밍 함수의 콜백**으로써 `this.message`를 참조하여 출력을 시도하였다.

위 예시에서 `timer.nomalFunc()`를 실행하면 `nomalFunc`는 내부의 `setTimeout` 함수를 호출하게 된다.  

`setTimeout`이 실행되면 첫번째 인자인 **일반 함수**가 콜백 함수로 들어가고 `setTimeout` 내부 로직에서 호출되고 실행된다.  

일반함수는 `setTimeout`의 콜백 함수이고, 따라서 자신의 호출 위치는 `setTimeout`이기 때문에 `this`는 `setTimeout`을 가리킨다.

<br/>

화살표 함수도 마찬가지로 `setTimeout`의 콜백 함수이다. 하지만 화살표 함수의 `this` 정의는 호출이 아닌 선언 단계에서 이루어지기 때문에 이와는 관련이 없다.

선언 단계에서 화살표 함수가 선언된 함수 범위는 부모 함수인 `arrowFunc`이다.   
따라서 화살표 함수의 `this` 정의는 `arrowFunc`에서 하게 되고 `arrowFunc`의 `this`는 객체 `timer`를 가리키기 때문에 화살표 함수도 이를 상속 받아 사용하게 된다.

<br/>

## **함수 호이스팅**
함수의 호이스팅은 변수의 호이스팅과 동일하게 JS 엔진이 코드를 실행하기 이전에 함수의 선언 찾아서 우선적으로 실행하는 것을 말한다.  

이러한 함수의 호이스팅은 익명 함수의 표현에서는 작동하지 않고 일반 함수의 선언에서만 작동한다.

함수의 호이스팅 덕분에 JS 문서 내 모든 함수의 선언을 최하단으로 몰아 넣어도 코드의 실행이 정상 작동한다.  

따라서 함수의 기능을 어느정도 유추할 수 있도록 함수명을 작명하고 선언부를 모두 문서 최하단으로 몰아 넣어서 코드의 가독성을 높이기도 한다.

<br/>

## **함수의 객체 반환 축약**  
함수의 매개변수와 반환할 객체의 속성이 동일하다면 축약하여 작성이 가능하다.  
```js
function user(name, age) {
  return {name, age}
};

console.log(user("rarebeef", 4));
// {name: "rarebeef", age: 4}
```

<br/>
<br/>

# **Property, 정적 비정적**

Property(프로퍼티)는 이해하기 쉽게 설명하면 **다른 데이터와 쌍으로 연결**되어 있는 데이터라고 말할 수 있다.

프로퍼티는 크게 두 종류로 구분할 수 있다.

- **Instance property, 비정적 프로퍼티**  
해당 object의 인스턴스들이 각각 갖고 있는 속성.

- **Static property, 정적 프로퍼티**   
해당 object의 모든 인스턴스들이 공유하는 공통된 속성.

<br/>

여기서 말하는 인스턴스란, 
```js
const arr = [1, 2, 3, 4];
const obj = {name: "rarebeef", age: 4};

// arr은 배열의 인스턴스이다.  
// obj는 객체의 인스턴스이다.
```
여기서는 간단하게 이 정도만 이해하고 넘어가면 된다.



<br/>

## **Property(속성) 예시**
```js
const me = {
  name: "rarebeef",
  age: 4,
  getName: function () {
    return this.name
  };
};
```
위 예시에서 `name`, `age`, `getName`은 **객체의 인스턴스**인 `me`의 **프로퍼티**이다.  
각각 연결된 데이터를 갖고 있다. 

`getName`은 메소드지만, JS에서는 함수도 값으로써 사용될 수 있기 때문에 프로퍼티라고 볼 수 있다. 

JS의 많은 내장 메소드들 또한 프로퍼티인데, 예시로 `length`는 인스턴스의 길이에 대한 데이터와 연결되어 있기 때문에 인스턴스 프로퍼티, 즉 **인스턴스 메소드**라고 볼 수 있다. 

<br/>

## **정적 메소드와 비정적 메소드**
스태틱 메소드는 **정적 메소드**,  
인스턴스 메소드는 **비정적 메소드**라고도 부를 수 있다.

앞서 인스턴스 프로퍼티는 인스턴스들이 각각 갖고 있는 속성이고  
스태틱 프로퍼티는 특정 오브젝트의 모든 인스턴스들이 공통으로 공유하는 속성이라고 말했는데,

메소드도 프로퍼티의 일종이기 때문에 **비정적 메소드**는 인스턴스들이 **각각 갖고 있는 메소드**,  
**정적 메소드**는 특정 오브젝트의 모든 인스턴스들이 **공통으로 공유하는 메소드**라고 볼 수 있다.

이해하기 쉽도록 Array를 예시로 설명하자면,  

- Array의 인스턴스들이 각자 소유하고 있는 메소드는 비정적 메소드

- Array가 직접 소유하고 있는 메소드는 정적 메소드

비정적 메소드의 예시는 앞서 말한 `length`가 있다. Array의 각 인스턴스들은 각자 다 다른 길이를 갖고 있기 때문에 비정적 메소드이다.

정적 메소드의 예시로는 대상이 배열인지 확인하는 `Array.isArray()` 가 있다.  
판별의 대상으로 배열이 들어올지 문자열이 들어올지 아무도 모르기 때문에 인스턴스 메소드로는 작동할 수 없다.  
따라서 Array가 직접 소유한 정적 메소드로써 대상의 데이터 타입을 판별한다.

<br/>

### **Array의 정적/비정적 메소드 사용 예시**
```js
const a = [1, 2, 3, 4, 5];

a.length; // 비정적 메소드, 인스턴스명이 앞에 온다.

Array.isArray(a); // 정적 메소드, 오브젝트명이 앞에 오고 대상은 인자로 전달한다.
```

<br/>
<br/>

# **생성자 함수**

객체는 속성과 메소드로 구성될 수 있다. 이 모든 구성 요소를 통틀어서 멤버라고 부른다.  

동일한 멤버를 갖지만 값이 다른 객체를 여러개 생성하기 위해서는 중복된 코드를 각 객체마다 반복해서 작성해야 하기 때문에 메모리와 시간 낭비가 발생한다.

이러한 문제점을 생성자 함수를 통해 해결할 수 있다.

<br/>

## **생성자의 사용**
```js
// 생성자 만들기
// 인스턴스마다 값이 다른 속성을 매개변수로 전달 받는다.
function User (name, age) {
    // 각 매개변수를 속성에 부여
  this.name = name;  
  this.age = age;
    // 공통을 사용될 메소드 선언
  this.getName = function () {
    return this.name
  };
};

// 생성자로 객체 만들기
// 인스턴스마다 값이 다른 속성을 인자로 전달한다.
const user1 = new User("rarebeef", 4);

// 생성자로 만든 객체의 구조
{
  name: "rarebeef",
  age: 4,
  getName: function () {
    return this.name
  }
}
```
위의 `user1`과 같이 생성자를 통해 생성한 객체를 담는 변수를 인스턴스라고 부른다.

인스턴스마다 값이 다른 속성만 매개변수로 전달 받아서 **각각 다른 속성값을 갖고 있는 동일한 구조의 객체**를 여러개 생성할 수 있다.



생성자 함수의 이름은 일반 함수와 구분하기 위해 파스칼 케이스(모든 단어의 첫글자를 대문자로)로 작성한다.

<br/>

## **Prototype**
위 생성자의 예시에서 `name`과 `age`는 인스턴스마다 값이 다르기 때문에 통일하여 메모리를 관리할 수 없다.

하지만 `getName()` 메소드는 인스턴스가 모두 동일하게 갖는 내용이기 때문에 더 효율적으로 메모리를 관리하도록 만들 수 있다.

이 때 사용하는 것이 바로 Prototype이다.
```js
function User(name, age) {
  this.name = name;
  this.age = age;
};

User.prototype.getName = function () {
  return this.name
};
```
`name`과 `age`는 인스턴스가 생성될 때 마다 메모리에 각각 저장되지만 프로토타입으로 생성한 `getName()` 메소드는 메모리에 단 한 번만 저장된다.  

따라서 각 인스턴스는 각자의 `getName()`을 소유한 것이 아닌 하나의 `getName()`을 빌려서 사용하게 된다.

<br/>
<br/>

# **ES6 Classes**

ES6에 타 언어의 class와 비슷한 문법이 추가되었다.  

이 class를 통해 기존의 생성자 함수를 대체할 수 있다.

<br/>

## **클래스 사용법**
```js
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  };
  getName() {
    return this.name
  };
};

const user1 = new User("rarebeef", 4);
```
내부 로직은 기존의 생성자 함수와 비슷하게 생겼다.  

다른 점은 `constructor` 라는 함수가 추가되었다. 이 함수의 매개변수로 인스턴스마다 값이 다른 속성을 넣고 함수 내부에서 매개변수를 속성에 할당한다.

`constructor`의 뒤에 인스턴스가 공통으로 갖게 될 속성을 넣는다. 이 부분에 작성한 속성은 객체의 프로토타입으로 작동하게 된다.

<br/>

## **상속(확장)**

상속은 새로운 클래스를 생성할 때 다른 클래스에서 공통된 내용을 불러오는 것을 말한다. 

상속을 통해 하위 클래스들을 비교적 간단하게 생성할 수 있다.
```js
// 기존 클래스
class User {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  };
  getName() {
    return this.name
  };
};

// 상속 받은 클래스
class UserEmail extends User {
  constructor(name, age, email) {
    super(name, age);
    this.email = email
  };
  getEmail() {
    return this.email
  };
}

const user1 = UserEmail("rarebeef", 4, "email@email.com");
```
`extends`를 통해 내용을 불러올 클래스를 지정하고, `constructor` 내부에서 `super()` 함수를 통해 상속 받을 매개변수를 지정한다.  

상속 받을 내용 외 추가할 내용은 기존의 클래스와 동일하게 작성한다.

메소드는 상속을 따로 지정하지 않아도 자동으로 상속된다.

<br/>
<br/>

# **Import / Export**
프로젝트의 여러 부분과 여러 JS 파일들에서 자주 쓰이는 함수와 메소드들을 각 JS 파일마다 따로 선언하는 것은 효율적이지 못하다.  

자주 쓰이는 코드들을 별도의 JS 파일로 분리하여 생성해두고 필요한 곳에 불러와서 쓰는 방법이 권장되는데, 이를 모듈화라고 부른다.  

이러한 모듈들을 내보내고 불러올 때 사용하는 문법이 바로 `import`와 `export`이다.   

내가 필요에 따라 직접 생성한 모듈은 물론 JS의 여러 서드파티 모듈(라이브러리, 패키지 등)을 불러올 때도 사용하게 되니 필수적으로 알아두는 것이 좋다.

<br/>

### **`export`**
모듈을 `import` 하기 위해서는 당연히 `export` 할 모듈을 먼저 생성해야 한다.

모듈의 확장자는 다른 JS 파일들과 마찬가지로 `.js`이다.  
파일명은 자유지만 내용을 알아보기 쉽게 작명할 것.

모듈 내에 저장할 데이터는 크게 두가지로 나눌 수 있는데, 이 두가지는 뒤에 나올 `import` 방식에서 차이가 있다.

- **Default export**  
하나의 모듈에서 **단 하나만 선언**할 수 있는 데이터이다.  
모듈 생성시 해당 데이터는 별도의 이름을 지정하지 않아도 되지만 **`import` 시에는 참조를 위한 이름을 지정**해야한다.  
모듈 생성시 이름을 지정해도 상관 없지만 `import`시 이름 지정은 문법상 필수이다.  
`export default`를 통해 내보낸다.

- **Named export**  
**개수 제한이 없는** 데이터들이다. **모듈 생성시 반드시 이름을 지정**해야한다.  
`export`를 통해 내보낸다.

```js
// module.js

// default export, 하나만 생성 가능
export default function () {
  console.log("Hello, world!");
};

// named export, 복수 생성 가능
export function myName() {
  console.log("RAREBEEF")
};
export function myEmail() {
  console.log("myemail@email.com")
};
```

<br/>

### **`import`**
모듈을 생성하고 `export` 할 데이터를 정의하였다면 이제 다른 JS파일에서 해당 모듈의 데이터들을 `import` 할 수 있다.  

`import 데이터 from "모듈경로"` 의 기본 구조를 갖고 있다.  

`데이터` 부분에 데이터를 참조할 때 사용할 이름을 지정한다.  

`"모듈경로"` 부분은 말 그대로 모듈의 경로를 작성하는데, 상대경로 `./`을 명시하지 않을 경우 NPM의 node_modules 폴더에 있는 패키지를 탐색하게 되니 주의.  

JS 파일은 확장자를 생략해도 정상적으로 불러들인다.

- **Default export 불러오기**  
이름이 없는 경우가 있기 때문에 `import` 할 때 반드시 이름을 지정해야 한다.  
`import 이름 from "경로"`

- **Named export 불러오기**  
모듈 생성시 지정한 이름으로 불러온다.  
이 이름을 중괄호로 감싸서 작성하며, 중괄호 내에 쉼표 구분을 통해 복수의 데이터를 불러올 수 있다.  
또한 `as` 를 통해 생성시 지정한 이름이 아닌 다른 이름을 지정이 가능하다.  
`import {이름 as 다른이름 [, ...] } from "경로"`


```js
// main.js

// default export 불러오기
// 참조에 사용할 이름을 지정한다.
import hi from "./module.js"

// named export 불러오기
import {myName as name, myEmail as email} from "./module.js"
```
<br/>
<br/>

# **데이터 불변성**  
JS의 데이터는 크게 두가지 개념으로 분류가 가능하다.  

- **원시 데이터**  
String, Number, Boolean, undefined, null

- **참조형 데이터**  
Object, Array, Function

이 데이터들은 모두 메모리에 저장된다. 

 `a`라는 변수에 `apple` 이라는 값을 할당할 경우 메모리에 `apple` 이라는 데이터가 저장되고 변수는 이 데이터가 저장된 메모리 주소를 가리키는 일종의 표지판 역할을 한다.  

 따라서 정확히 말하면 데이터는 메모리에 저장되고, 변수는 이 메모리의 주소가 저장되는 것이다.

 <br/>

 ## **원시 데이터**  
 **원시 데이터**는 **불변성**이라는 특성을 갖고 있다.  

1. 변수 `a`에 `"apple";` 을 할당하면 특정 메모리 주소에 `apple` 이 저장되고 `a`는 이 메모리 주소를 가리킨다.

2. 이후 변수 `a`에 `"banana"`를 재할당하면 새로운 메모리 주소에 `"banana"`가 저장된다.

3. 이 때 기존의 `"apple"` 은 사라지지 않고 그대로 메모리 주소에 남아있게 된다. 더 이상 이 메모리 주소를 가리키는 변수가 없어도 마찬가지이다.  

4. 새로운 변수 `b`를 선언하고 이 변수에 `"apple"`을 할당하면 변수 `b`는 기존에 남아있던 `"apple"`의 메모리 주소를 가리키게 된다.

5. 이 변수 `b`에 변수 `a`를 재할당할 경우 `b`는 `a`가 가리키는, 즉 `"banana"`의 메모리 주소를 가리키게 된다.

6. 새로운 변수 `c`를 선언하고 `"banana"`를 할당하였다.  
변수 `a`, `b`, `c`는 모두 `"banana"`가 저장된 메모리 주소를 가리키게 된다.  

7. 이 때 까지도`"apple"`은 여전히 메모리 주소에 남아있다.

위 예시처럼 원시 데이터는 변수에 할당한 데이터가 이미 메모리 주소에 존재할 경우 **데이터를 메모리에 새롭게 생성하는 것이 아닌 기존의 데이터를 사용**하게 된다.  

또한 그 메모리 주소를 가리키는 변수가 더 이상 존재하지 않더라도 해당 **데이터는 메모리에 계속 유지**된다.  

이를 **데이터의 불변성**이라고 부르며, 원시 데이터의 가장 큰 특징이다.

<br/>

## **참조형 데이터**
**참조형 데이터**는 원시 데이터와 달리 **불변성이 없다.** 이를 **가변한다**고 표현한다.  

따라서 참조형 데이터는 원시 데이터와 메모리의 참조 방식이 다르다.  

1. 변수 `a`와 `b` 둘 모두에 `{num: 1}`라는 객체 데이터를 할당하였다.  
메모리는 `{num: 1}`라는 데이터를 서로 다른 주소에 따로 저장하게 된다.  
따라서 `a`와 `b`는 같은 데이터를 갖고 있음에도 불구하고 서로 다른 메모리 주소를 가리킨다.

2. 변수 `a`에 `{num: 2}`라는 객체를 재할당하였다.  
기존의 변수 `a`가 가리키던 메모리 주소의 `{num: 1}`은 제거되고, 그 자리를 `{num: 2}`가 차지하게 된다. 

3. 변수 `b`에 변수 `a`를 재할당하였다.  
변수 `b`와 변수 `a`는 같은 메모리 주소를 가리키게 되고, 둘 다 `{num: 2}`라는 데이터를 갖게 된다.

4. 변수 `b`에 `{num: 3}`을 재할당하였다.  
기존의 변수 `b`가 가리키던 메모리 주소의 `{num: 2}`는 제거되고, 그 자리를 `{num: 3}`가 차지하게 된다.  

5. 이 때 해당 메모리 주소를 먼저 가리키고 있던 변수 `a`의 데이터도 `{num: 3}`로 변한다.

위 예시처럼 참조형 데이터는 메모리에 저장된 데이터가 변할 수 있다.  

또한 원시 데이터와는 달리 참조형 데이터는 변수에 할당된 값을 변경할 경우 변수가 메모리 주소를 옮기는 것이 아닌 메모리 주소에 저장된 값이 변경되기 때문에 **같은 메모리 주소를 바라보는 변수가 여러개 존재할 경우 그 변수들의 값도 변하게 된다.**

따라서 참조형 데이터를 다룰 때 변수에 변수를 할당하는 경우 주의할 필요가 있다.  

의도치 않게 다른 변수의 값이 변경되는 것을 방지하기 위해 **복사** 라는 방법을 사용할 수 있다.

<br/>
<br/>

# **복사**
참조형 데이터 사용 시 **복사**라는 방법을 사용하면 원본을 훼손하지 않고 사본을 수정할 수 있다.  

복사의 방법은 얕은 복사와 깊은 복사 두가지로 나누어진다.  

여기서는 복사에 사용하는 문법과 패키지에 대해 간단히만 설명하고, 나중에 차례가 오면 더 자세히 설명할 예정.

<br/>

## **얕은 복사**
복사는 참조형 데이터의 내용을 복사해서 새로운 메모리 주소에 저장하게 된다. 복사를 통해 생성한 사본은 이 새로운 메모리 주소를 가리키게 된다.  

이 때 얕은 복사의 경우 데이터의 겉표면만 복사를 하기 때문에 그 내부에 또 다른 참조형 데이터가 존재한다면, 얕은 복사는 이 데이터에 간섭하지 않았으므로 내부의 참조형 데이터는 여전히 원본의 메모리 주소를 가리키고 있게 된다.

- 얕은 복사의 방법

  - **`Object.assign()`**  
  여러 객체를 하나로 합쳐서 반환하는 정적 메소드이다.  
  인자로 전달한 객체 중 첫번째 객체에 나머지 인자의 객체를 합쳐서 반환하기 때문에 첫번째 인자의 객체는 원본이 훼손된다.  
  첫번째 인자로 빈 객체`{}`를 전달하고 합칠 객체들을 그 나머지 인자로 전달하는 방법을 통해 원본 훼손 없이 객체를 합칠 수 있다. 얕은 복사도 이 방법을 사용하게 된다.
  

  - **전개 연산자 (`...`)**   
  전개 연산자는 객체 혹은 배열의 내부 요소를 하나의 객체(배열)이 아닌 개별로 꺼내준다.  
  이 개별로 꺼낸 요소들을 새 객체에 할당하여 얕은 복사를 할 수 있다.

```js
const user = {
  name: "rarebeef",
  age: 4,
  skill: ["html", "css", "js"]
};

// Object.assign()
const userCopy1 = Object.assign({}, user);

// 전개 연산자
const userCopy2 = {...user};
```
복사할 참조형 데이터의 내부에 참조형 데이터가 없을 경우 얕은 복사로 간단하게 복사할 수 있다.  

하지만 위 예시의 `user.skill` 과 같이 내부에 참조형 데이터가 또 존재할 경우 **깊은 복사** 방법을 사용해야 한다.

<br/>

## **깊은 복사**
재귀함수를 이용하여 깊은 복사를 할 수 있다.  

재귀함수란, 함수의 내부에서 자기 자신을 다시 실행하는 함수를 말한다.  

깊은 복사에 사용하는 재귀 함수는 복사할 데이터에 있는 모든 요소를 끄집어내서 복사하는데, 끄집어낸  요소가 참조형 데이터일 경우 그 요소에 대해 자기 자신을 다시 한 번 실행한다.  

또 다른 방법은 lodash 패키지를 사용하는 것이다.  

이 방법이 더 간단하므로 이 문서에서는 lodash를 이용한 깊은 복사만 소개한다.
```js
// lodash import
import _ from "lodash"

const user = {
  name: "rarebeef",
  age: 4,
  skill: ["html", "css", "js"]
};

// lodash를 이용한 깊은 복사
const userCopy = _.cloneDeep(user);
```

<br/>
<br/>


# **JSON & Storage**
스토리지는 브라우저에서 관리되는 데이터 저장소이다.  

key:value 쌍으로 데이터가 저장되며, key와 value 모두 string으로 저장하는 것을 권장한다.  

브라우저의 개발자도구 -> 어플리케이션 -> 스토리지 탭에서 확인이 가능하다.

lodash 기반의 lowdb 패키지로 쉽게 관리가 가능하지만, 이 문서에서는 다루지 않는다.  

저장할 데이터는 string으로 형변환이 필요하다.

<br/>

## **JSON**

JSON을 이용하여 특정 데이터를 네트워크를 통해 전송하기 용이한 형태(string)로 변환하고, 다시 원래의 형태로 파싱할 수 있다.

<br/>

### **`JSON.stringify()`**  
특정 데이터를 string으로 형변환한다.
```js
const obj = {name: "rarebeef"};
const arr = [1, 2, 3, 4]

const objStr = JSON.stringify(obj);
const arrStr = JSON.stringify(arr);

console.log(typeof objStr);  // string 
```

<br/>

### **`JSON.parse()`**  
`JSON.stringify()`로 형변환 한 데이터를 분석하여 적합한 데이터 타입으로 다시 형변환한다.
```js
const objParse = JSON.parse(objStr);

console.log(typeof objParse);  // object
```

<br/>

## **Storage**
스토리지의 종류는 로컬 스토리지와 세션 스토리지 두 종류가 있다.  

로컬 스토리지의 데이터는 만료되지 않아서 반영구적으로 사용이 가능한 반면에 세션 스토리지는 세션이 만료될 때 데이터도 사라진다.

이 문서는 로컬 스토리지만 다룬다.
```js
const obj = {name: "rarebeef", age: 4};

// 객체를 string으로 형변환 후 스토리지의 user라는 key에 저장
localStorage.setItem("user", JSON.stringify(obj));

// 스토리지의 데이터를 불러온 후 파싱하기
const getData = JSON.parse(localStorage.getItem("user"));

// 스토리지에서 데이터 제거
localStorage.removeItem("user");
```

<br/>
<br/>

# **JS의 다양한 문법**

<br/>

## **`console.log`**  
브라우저의 콘솔에 인자를 출력한다.  
```js
const name = "rarebeef";
console.log(name);

// "rarebeef"
```

<br/>
<br/>

## **`typeof`**  
해당 요소의 데이터 타입을 반환한다.
```js
console.log(typeof "Hi"); // string
console.log(typeof 123); // number
console.log(typeof null); // object
console.log(typeof []); // object
console.log(typeof {}); // object
```
위처럼 null과 [], {} 모두 object라고 출력한다.  

보다 정확한 데이터 타입을 확인하기 위해서는 아래의 함수를 선언하여 사용할 수 있다.
```js
function getType() {
  return Object.prototype.toString.call(data).slice(8, -1);
};

console.log(getType(null)); // Null
```

<br/>
<br/>

## **String 관련 문법**

<br/>

### **`indexOf()`**  
주어진 문자열에서 인자로 전달한 값과 일치하는 **첫번째** 인덱스를 반환한다.  

배열에도 적용할 수 있다. 후술.

일치하는 값이 없으면 -1을 반환하며, 이를 이용해 문자열에 특정 값이 존재하는지 여부를 확인할 수 있다.  
```js
const str = "My name is rarebeef.";
const search = "name";

console.log(str.indexOf(search));  // 3

// 값의 존재 여부 확인하기
// 존재하면 true, 반대의 경우 false 반환
console.log(str.indexOf("Hello") !== -1);  
// false
```

<br/>

### **`length`**
문자열의 길이를 반환한다.  

문자열 외에 다양한 타입의 데이터에서도 사용이 가능하다.
```js
console.log("rarebeef".length);  // 8
```

<br/>

### **`slice()`**  

문자열에서 시작 위치와 종료 위치 직전까지 잘라서 반환한다.  

종료 index는 반환값에 포함되지 않고, 종료 index의 직전까지만 포함된다.  

인자로 시작 index와 종료 index를 전달하며, 종료 index는 선택사항이다. 시작 index만 전달 시 시작 index부터 문자열 끝까지 반환한다.  

반대로 시작 index를 0으로 전달하면 문자열의 처음부터 종료 index의 직전까지 반환한다.

인자로 음수를 전달 시 `문자열 길이 + 음수인자` 로 계산된다.  
이는 전체 문자열 길이를 특정할 수 없을 때, 뒤에서 몇번째까지 자를지 지정하는데 유용하다. 음수는 -1부터 시작한다.
```js
str = "abcde";
str.slice(0); // 0번째부터 출력, abcde
str.slice(1); // 1번째부터 출력, bcde
str.slice(3); // 3번째부터 출력, de
str.slice(2, 4); // 2번째부터 3번째까지 출력, cd
str.slice(-3, 4); // (5-3=2)번째부터 3번째까지 출력, cd
str.slice(0, -1); // 0번째부터 (5-1=4)번째까지 출력, abcd
```

<br/>

### **`replace()`**  
주어진 문자열에서 첫번째 인자값을 찾아 두번째 인자값으로 교체한다.  

두번째 인자로 빈 문자를 넣으면 찾은 문자열을 삭제할 수 있다.
```js
const str = "Hello world!"

console.log(str.replace("world", "rarebeef));  
// "Hello, rarebeef!"
```

<br/>

### **`match()`**  
인자로 전달한 정규표현식에 부합하는 문자열을 검색하고 그에 대한 정보들을 배열 형태로 반환한다.

<br/>

### **`trim()`**
문자열의 앞 뒤 공백을 전부 제거한다.
```js
const name = "    rarebeef    ";
console.log(name.trim());
// rarebeef
```

<br/>
<br/>

## **숫자, Math 문법**

<br/>

### **`toFixed`**  
소수를 반올림하여 **문자열로 반환**한다.  
인자로 받은 숫자까지 소수점 자리수를 유지한다.  

<br/>

### **`parse`**  
인자의 값을 분석하여 그에 맞는 자료형으로 변환하여 반환한다.  

- `parseInt`  
인자에서 정수 부분만 추출하여 number 형식으로 반환한다.  

- `parseFloat`  
위와 같지만 소수점 부분도 전부 추출하여 number 형식으로 반환한다.  

이 때, 두 함수 모두 가장 처음 등장한 숫자열 부분만 반환되고, 나머지는 버려진다. 
```js
const str = "abc3.13abcde12345"

console.log(parseInt(str));
// 3

console.log(parseFloat(str)); 
// 3.14
```

<br/>

### **`Math.abs()`**  
인자의 절대값을 반환한다.

<br/>

### **`MAth.min()`**  
인자들 중 최소값을 반환한다.

<br/>

### **`Math.max()`**  
인자들 중 최대값을 반환한다.  

<br/>

### **`Math.ceil()`**  
인자를 올림하여 정수로 반환한다.  

<br/>

### **`Math.floor()`**  
인자를 내림하여 정수로 반환한다.  

<br/>

### **`Math.round()`**  
인자를 반올림하여 정수로 반환한다.  

<br/>

### **`Math.random()`**  
0~1 사이의 난수를 반환한다.
```js
// min, max 사이의 난수를 반환하는 함수,
// toFixed의 인자로 소수점 자리수를 지정할 수 있다.
// toFixed는 반환값이 string이기 때문에 parse를 통해 number로 변환한다.
function random(min, max) {
  return 
    parseFloat(
      (Math.random() * (max - min) + min)
      .toFixed(2)
    )
};
```

<br/>
<br/>

## **Array(배열) 문법**

<br/>

### **`length`**  
배열의 길이, 즉 요소의 개수를 반환한다.

<br/>

### **`concat()`**  
두 배열을 병합하여 반환한다.  

원본 배열은 수정하지 않는다.
```js
const num = [1, 2, 3];
const str = ["a", "b", "c"];

console.log(num.concat(str));
/// [1, 2, 3, "a", "b", "c"]
```

<br/>

### **`forEach()`**  
배열의 각 요소마다 인자로 전달한 함수를 콜백하여 순차적으로 반복 실행한다.  

반환값이 없는 메소드로, 결과를 변수에 할당하면 undefined가 출력된다.

콜백에서 사용 가능한 매개변수는 아래와 같다.  

- element  
현재 차례의 요소를 말한다.

- index  
현재 차례의 index를 말한다.  

- array  
메소드를 실행한 배열 자체를 말한다.



```js
const nums = [1, 2, 3, 4];

nums.forEach(function (el, i, arr) {
  console.log(el, i, arr);
});
// 1, 0, [1, 2, 3, 4]
// 2, 1, [1, 2, 3, 4]
// 3, 2, [1, 2, 3, 4]
// 4, 3, [1, 2, 3, 4]

// 화살표 함수 버전
nums.forEach((el, i, arr) => console.log(el, i, arr));
```

<br/>

### **`find()`**  
주어진 **판별 함수를 만족**하는 배열의 **첫 번째 요소**를 반환한다.  

인자로 판별 함수와 thisArg를 전달하며, thisArg는 판별 함수가 실행될 때 this로 사용할 객체를 가리키지만 잘 쓰이지 않는다.  

판별함수는 콜백되어 배열의 각 요소와 비교하여 true와 false를 반환한다. 최초로 true가 반환되면 콜백이 중단되고 남은 요소는 판별하지 않는다. 즉 조건에 부합하는 요소 하나만 반환한다.  

콜백에서 사용 가능한 매개변수는 아래와 같다.

- element  
현재 차례의 요소를 말한다.

- index  
현재 차례의 index를 말한다.  

- array  
메소드를 실행한 배열 자체를 말한다.

```js
const nums = [1, 2, 3, 4];

const found = nums.find(el => el > 2);

console.log(found);
// 3
```

<br/>

### **`findIndex()`**  
주어진 **판별 함수를 만족**하는 배열의 **첫 번째 요소 index**를 반환한다.  

`find()`의 index 버전

<br/>

### **`indexOf()`**  
인자로 **주어진 값과 일치**하는 배열의 **첫 번째 요소 index**를 반환한다.  

`findIndex()`와는 달리 인자로 판별 함수가 아닌 찾고자 하는 값을 전달한다.  

찾고자 하는 값이 없으면 -1을 반환하는 특징을 이용하여 해당 값이 배열 내에 존재하는지 확인할 수 있다.

프로그래머스 코딩 테스트 문제를 이 메소드를 사용해 풀어보았다.
```js
// 일부 숫자가 0으로 지워진 로또 용지와 당첨 번호가 배열로 주어질 때,
// 가능한 최대 순위와 최저 순위를 배열로 반환

function solution(lottos, win_nums) {
  let correct = 0;
  let ranks = [6, 6, 5, 4, 3, 2, 1];

  for (let i=0; i<win_nums.length; i++) {
    win_nums.indexOf(lottos[i]) !== -1 ? correct+1 : correcr+=0
  };

  return 
    [wins[correct+lottos.filter(num => num === 0).length], wins[correct]]
};
```

<br/>

### **`map()`**  
배열의 각 요소마다 **인자로 전달한 함수**를 콜백하여 **순차적으로 반복 실행**하고, 이 함수의 **반환값을 저장하여 새로운 배열로 반환**한다.  

`forEach()`와 유사하지만 반환값이 있다는 차이점이 존재한다. 따라서 변수에 할당이 가능하다.  

인자로 판별 함수를 전달하면 모든 요소에 대한 boolean 값을 반환한다.

콜백에서 사용 가능한 매개변수는 아래와 같다.  

- element  
현재 차례의 요소를 말한다.

- index  
현재 차례의 index를 말한다.  

- array  
메소드를 실행한 배열 자체를 말한다.

```js
const nums = [1, 2, 3, 4];

const a = nums.map(el => el+10);

console.log(a);
// [11, 12, 13, 14]
```

<br/>

### **`filter()`**  
주어진 **판별 함수를 만족**하는 **배열의 모든 요소를 반환**한다.  

위에 나온 `map()`, `find()`, `findIndex()`는  
boolean 값이나 첫 번째 요소만 리턴하는데 `filter()`는 조건에 만족하는 모든 요소 자체를 반환한다.

```js
const nums = [1, 2, 3, 4];
const found = nums.filter(el => el > 2);
console.log(found);
// 3, 4
```

<br/>

### **`includes()`**  
인자로 전달한 값이 배열 내에 존재하는지 boolean 값으로 반환한다.  
```js
const nums = [1, 2, 3, 4];
const isInclude = nums.includes(9);
console.log(isIncludes);
// false
```

<br/>

### **`push()`**  
배열의 가장 뒤에 인자값을 추가한다.  

**원본이 수정된다.**  
```js
const nums = [1, 2, 3, 4];
nums.push(5);
console.log(nums);
// [1, 2, 3, 4, 5]
```

<br/>

### **`unshift()`**  
배열의 가장 앞에 인자값을 추가한다.

**원본이 수정된다.**

<br/>

### **`reverse()`**  
배열의 순서를 뒤집는다.

**원본이 수정된다.**

<br/>

### **`splice()`**  
배열의 요소를 첫번째 인자인 시작 index에서 두번째 인자의 수만큼 삭제한다. 

세번째+@ 인자로 요소를 삭제한 자리에 새롭게 추가할 요소를 지정할 수 있다. 

두번째와 세번째 인자는 선택사항이다.

시작 index를 음수로 전달할 시 배열의 뒤에서부터 카운트한다.  

두번째 인자를 0으로 전달 시 요소를 삭제하지 않는다.  
아예 전달하지 않을 시 시작 index부터 모든 요소를 삭제한다.

**원본이 수정된다.**
```js
  const nums = [1, 2, 3, 4, 5, 6, 7 ,8, 9];

  nums.splice(3, 2);
  console.log(nums);
  // [1, 2, 3, 6, 7, 8, 9]

  nums.splice(3, 0, 4, 5);
  console.log(nums);
  // [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

<br/>
<br/>

## **Object(객체) 문법**

<br/>

### **`Object.assign()`**  
하나 이상의 출처 객체를 **대상 객체**로 속성을 **복사/붙여넣기**하여 **대상 객체를 반환**한다.  

첫번째 인자는 대상 객체, 두번째부터는 출처 객체이다.

대상 객체와 출처 객체들을 합쳐서 대상 객체를 반환하는 정적 메소드이다. 이 때 **대상 객체는 원본이 수정된다.**  

따라서 반환값을 변수에 할당하면 해당 변수와 대상 객체는 같은 메모리 주소를 갖게 된다.

원본 객체를 수정하고 싶지 않다면 대상 객체로 빈 객체를 전달하고 합칠 내용들을 출처 객체로 전달하면 된다.
```js
const userName = {
  name: "rarebeef"
};
const userAge = {
  age: 4
};

Object.assign(userName, userAge);
console.log(userName);
// {name: "rarebeef", age: 4}

// 원본을 유지하고 객체 합치기
const user = Object.assign({}, userName, userAge);
```

<br/>

### **`Object.keys()`**
인자로 전달한 객체의 key들을 배열로 반환한다.
```js
const user = {
  name: "rarebeef",
  age: 4
};

userKeys = Object.keys(user);

console.log(userKeys);
// ["name", "age"]

// Key 배열로 객체의 value 배열 만들기
const userValues = userKeys.map(key => user[key]);

console.log(userValues);
["rarebeef", 4]
```

<br/>
<br/>

## **비구조화 할당 (구조 분해 할당)**  
객체, 배열 데이터의 구조를 분해하여 변수에 할당 후 참조한다.  

각 요소를 보다 간단하게 참조가 가능해진다는 장점이 있다.

<br/>

### **객체 비구조화 할당**

객체의 비구조화 할당은 아래 코드를 통해 이루어진다.

`const {key1, key2...} = obj`

참조 시 사용할 변수명을 지정할 수 있다.  

존재하지 않는 속성도 비구조화 할당이 가능한데, 이 경우 undefined가 할당된다.  
이 undefined는 원하는 값으로 대체할 수 있다.  

해당 객체의 모든 속성을 비구조화 할당할 필요는 없다. 필요한 속성만 골라서 비구조화 할당이 가능하다.
```js
const user = {
  name: "rarebeef", 
  age: 4,
  country: "South Korea"
};

// 비구조화 할당 & 참조
let {name, age, country} = user;
console.log(country);  // "South Korea"

// 참조 시 사용할 변수명을 지정할 수 있다.
let {name: 이름, age: 나이, country: 국적} = user;
console.log(이름);  // "rarebeef"

// 존재하지 않는 속성을 비구조화 할당하고 기본값 할당
let {name, age, country, email = "none"} = user;
console.log(email);  // "none"
```

<br/>

### **배열 비구조화 할당**

배열의 비구조화 할당은 아래 코드를 통해 이루어진다.

`const [var1, var2...] = arr`

객체와 달리 key가 존재하지 않고, 대신 순서가 있기 때문에 순서대로 비구조화 할당이 진행된다.  

따라서 할당하지 않을 요소도 빈칸으로 남기고 쉼표로 구분하여 순서를 건너뜀을 명시해야 한다.

```js
const nums = [1, 2, 3, 4, 5];

// 비구조화 할당 & 참조
let [a, b, c, d, e] = nums;
console.log(c);  // 3

// 일부 요소만 비구조화 할당
let [ , , , d, e] = nums;
console.log(d);  // 4
```

<br/>
<br/>

## **전개 연산자**
`...`  

전개 연산자는 배열의 형태가 아닌 요소를 각각의 값으로 참조할 때 사용한다.
```js
const nums = [1, 2, 3, 4];

// 일반 참조
console.log(nums); // [1, 2, 3, 4]

// 전개 연산자 참조
console.log(...nums); // 1 2 3 4
```

<br/> 

### **Rest parameter**  
전개 연산자를 매개변수에 사용 시 개수를 초과한 인자를 전부 해당 매개변수에 배열로 저장한다.
```js
const toObj = (a, b, ...c) => ({a, b, c});

console.log(toObj(1, 2, 3, 4, 5));
// {a: 1, b: 2, c: [3, 4, 5]}
```

<br/>
<br/>

## **DOM API**
> **Document Object Model  
Application Programming Interface**  

DOM API는 JS에서 HTML의 요소를 제어하는 명령이다.  

<br/>

### **`document.querySelector()`**

인자로 전달한 선택자와 일치하는 HTML 요소를 하나만 찾아서 반환한다.
```js
const h1El = document.querySelector("div h1");
```

<br/>

### **`document.querySelectorAll()`**

인자로 전달한 선택자와 일치하는 모든 HTML 요소를 반환한다.  

`forEach()`를 통해 찾은 요소들을 제어할 수 있다.
```js
const h1El = document.querySelectorAll("div h1");
```

<br/>

### **`.textContent`**
대상 요소의 텍스트 내용을 불러오거나 지정할 수 있다.
```js
liEl.textContent = "Hello, world!";

console.log(liEl.textContent);
// "Hello, world!"
```

<br/>

### **`.innerText`**
대상 요소에서 출력할 텍스트를 지정할 수 있다.
```js
liEl.innerText = "Hello, world!";
```


<br/>

### **`document.createElement()`**  
HTML 요소를 생성한다.  
이 메소드만으로는 HTML 구조에 요소가 삽입되지는 않지만 메모리 상에는 해당 요소가 생성된다.

아래의 `.appendChild()`를 통해 요소를 HTML에 실제 삽입할 수 있다.
```js
const liEl = document.createElement("li");
```

<br/>

### **`.appendChild()`**  
인자로 전달한 요소를 대상 요소의 하위로 집어넣는다.
```js
const ulEl = document.querySelector("ul");
const liEl = document.createElement("li");

ulEl.appendChild("liEl");
```

<br/>

### **`.addEventListener()`**  
대상 요소에 지정한 이벤트가 발생하면 지정한 함수를 실행한다.  

이 때 실행될 지정한 함수는 핸들러라고 부른다.

**이벤트 목록**
- click  
요소 클릭

- focus  
요소 포커스

- blur  
포커스 해제  

- scroll  
스크롤  

```js
liEl.addEventListener("click", () => {
  console.log("Clicked");
})
```

<br/>

### **`.classList`**  
대상 요소의 클래스를 제어한다.

**.classList.add()**  
대상 요소에 클래스를 추가한다.

**.classList.remove()**  
대상 요소에서 클래스를 제거한다.

**.classList.contains()**  
대상 요소에 클래스가 존재하는지 확인한다.

```js
liEl.classList.add("x");

let isContains = liEl.classList.contains("x");

console.log(isContains);  // true

liEl.classList.remove("x");

// isContains 재할당, 생략시 값이 true로 유지된다. 최신화를 위해 재할당한다.
isContains = liEl.classList.contains("x");

console.log(isContains);  // false
```

<br/>

### **`.focus`**  
대상 요소에 focus 효과를 적용한다.  

상위 요소 클릭시 대상 요소를 focus 시킬 때 유용하다.
```js
inputEl.focus();
```

<br/>

### **`.style`**  
대상 요소의 style을 제어한다.  

적용할 스타일명을 체이닝하여 사용한다.
```js
liEl.style.color = "red";
```

<br/>

### **`.속성 = ""`**  
대상 요소의 속성을 제어한다.  

아래 `setAttribute()`와의 차이가 아직 이해되지 않아서 좀 더 알아볼 예정.
```js
imgEl.src = "./images/1.jpg";
```

<br/>

### **`setAttribute("속성", "값")`**  
대상 요소에 속성과 값을 부여한다.  
```js
inputEl.setAttribute("placeholder", "검색");
```

<br/>
<br/>

# **라이브러리**
JS의 다양한 라이브러리에 대해서 (매우) 간략히 정리하였다.

<br/>
<br/>

## **lodash**
`import _ from "lodash"`

<br/>

### **`_.throttle()`**
함수 등이 반복하여 실행될 때, 과부하를 방지하기 위해 실행 간격을 제어한다.

인자로 핸들러와 시간을 전달한다.
```js
// 스크롤 시 1초 간격으로 로그에 "scroll" 출력
window.addEventListener(
  "scroll", 
  _.throttle(
    () => console.log("scroll"),
    1000
  )
);
```

<br/>

### **`_.uniq()`**  
배열에서 유니크 값만 반환한다.
```js
const nums = [1, 2, 3, 4, 4, 4];

console.log(_.uniq(arr));
// [1, 2, 3, 4]
```

<br/>

### **`_.uniqBy()`**
객체가 포함된 배열에서 지정한 속성을 기준으로 유니크 값만 반환한다.

첫번째 인자로 배열, 두번째 인자로 기준 속성을 전달한다.

```js
const users = [
  {id: 1, name: "rarebeef"},
  {id: 1, name: "peter"},
  {id: 2, name: "gildong"},
  {id: 2, name: "stark"}
];

console.log(_.uniqBy(users, "id"));
//[{id: 1, name: "rarebeef"},
//{id: 2, name: "gildong"}]
```

<br/>

### **`_.unionBy()`**
객체가 포함된 두 배열을 지정한 속성을 기준으로 유니크 값만 병합하여 반환한다.

첫번째와 두번째 인자로 배열, 세번째 인자로 기준 속성을 전달한다.

```js
const users1 = [
  {id: 1, name: "rarebeef"},
  {id: 2, name: "gildong}
];
const users2 = [
  {id: 1, name: "peter"},
  {id: 2, name: "stark"}
];

console.log(_.unionBy(users1, users2, "id"));
//[{id: 1, name: "rarebeef"},
//{id: 2, name: "gildong"}]
```

<br/>

### **`_.find()`**
객체를 포함한 배열에서 지정한 속성값을 갖는 요소를 **하나** 반환한다.

첫번째 인자로 배열, 두번째 인자로 {속성:값}을 전달한다.
```js
const users = [
  {id: 1, name: "rarebeef"},
  {id: 2, name: "gildong"}
];

console.log(_.find(users, {id: 2}));
// {id: 2, name: "gildong"}
```

<br/>

### **`_.findIndex()`**
객체를 포함한 배열에서 지정한 속성값을 갖는 요소의 index를 **하나** 반환한다.

<br/>

### **`_.remove()`**
객체를 포함한 배열에서 지정한 속성값을 갖는 요소를 **하나** 삭제한다.

<br/>
<br/>

## **gsap**

<br/>

### **`gsap.to()`**  
HTML 요소에 애니메이션 효과를 추가한다.

전달하는 인자는 순서대로 대상 요소, 지속시간, 옵션을 의미한다.  

대상 요소는 변수에 할당하지 않고 css 선택자로도 전달할 수 있다.  

지속시간은 애니메이션 효과가 몇 초에 걸쳐 적용될 것인지를 의미한다. 부드러운 효과를 주는데 유용하다.

옵션은 객체 데이터로 전달하며 key는 css의 속성, value는 속성값을 의미한다.

**가용 옵션**

- **delay**  
애니메이션 효과에 delay를 적용한다.  
`delay: (index+1) * 0.5` 와 같이 각 요소의 효과가 0.5초 간격으로 실행되도록 할 수도 있다.

- **repeat**  
애니메이션의 반복 횟수를 지정한다.  
-1을 부여하면 무한 반복이 된다.

- **yoyo: true**   
애니메이션이 끝나면 역재생하여 처음 상태로 돌아간다.

- **scrollTo**  
window의 스크롤 위치 이동을 지정한다.  
최상단 스크롤 버튼 등에 사용된다.
gsap의 scrollTo 플러그인을 별도로 불러와야 한다.

```js
// 단일 요소에 효과 주기
gsap.to(itemEl, .6, {
  opacity: 0;
});

// 여러 요소에 순차적 효과 주기
itemEls.forEach((itemEl, index) => {
  gsap.to(itemEl, .6, {
    opacity: 0,
    delay: (index+1)*.5
  })
});
```

<br/>
<br/>

## **swiper**  
슬라이드 효과를 갖는 요소를 만들 때 사용한다.

swiper를 사용하기 위해서는 HTML 구조에 라이브러리에서 지정한 클래스명을 갖는 요소들이 있어야한다.

<br/>

**필요한 HTML 클래스**

- **swiper-container**  
swiper-wraper의 부모, swiper-slide의 상위 요소이다.

- **swiper-wraper**  
swiper-slide의 부모 요소이다.  
모든 swiper-slide를 감싼다.

- **swiper-slide**  
실제 swiper가 동작할 요소이다.  
swiper가 동작하여 현재 화면에 출력되는 요소는 swiper-slide-active 클래스가 자동으로 부여된다.

<br/>

**선택적 HTML 클래스**  
부가 기능을 사용할 때 필요한 클래스이다.  
swiper-container의 형제 요소로 추가한다.

- **swiper-pagination**  
페이지 번호를 표시한다.  
position: absolute가 자동으로 부여된다.

- **swiper-bullet**  
swiper-pagination이 있으면 슬라이드 수만큼 자동으로 생성되는 가상 요소이다.  
슬라이드가 화면에 출력되면 해당하는 bullet에 자동으로 active 클래스가 부여된다.

- **swiper-prev**  
이전 슬라이드로 이동하기 위한 버튼 요소이다.

- **swiper-next**  
다음 슬라이드로 이동하기 위한 버튼 요소이다.

<br/>

**HTML 구조 예시**
```html
<div class="swiper-container">
	<div class="swiper-wraper">
		<div class="swiper-slide">slide1</div>
		<div class="swiper-slide">slide2</div>
		<div class="swiper-slide">slide3</div>
	</div>
</div>

<div class="swiper-pagination"> </div>
<div class="swiper-prev"> </div>
<div class="swiper-next"> </div>
```

<br/>

**`new Swiper`**  
생성한 HTML의 요소에 대해 JS에서 기능을 부여한다.

생성자로 Swiper를 추가하고, 인자로 swiper-container의 선택자와 옵션을 전달한다.

**가용 옵션**  
`swiper()`에 key: value 형태의 객체로 옵션을 전달한다.

- **direction**  
슬라이드 방향을 지정한다. 
  - horizontal, 기본값

  - vertical

- **autoplay**  
자동 슬라이드를 지정한다.  
(true, false)  
객체로 다양한 옵션을 지정할 수 있다.

- **loop**  
반복 여부를 지정한다.

- **slidesPreview**  
한 번에 보여질 슬라이드의 수를 지정한다.  

- **spaceBetween**  
슬라이드 사이 간격을 px 단위로 지정한다.

- **centeredSlides**  
1번 슬라이드가 가운데 출력될지 지정한다. 
(true, false)

- **pagination**  
페이지네이션을 추가한다.  
옵션으로 페이지네이션 요소와 다양한 기능을 부여한다.

- **navigation**  
네비게이션을 추가한다.  
옵션으로 버튼으로 사용할 요소를 지정한다.

<br/>

**`new Swiper` 예시**
```js
new Swiper(.swiper-container, {
  direction: 'vertical',
  loop: true,
  autoplay: {
    delay: 1000},
  pagination: {
    el: 'swiper-pagination',
    clickable: true},
  navigation: {
    prevEl: 'swiper-prev',
    nextEl: 'swiper-next'}
});
```

<br/>
<br/>

## **axios**  
HTTP 요청을 처리한다.
사용한다.
<br/>

### **`axios.get("")`**
요청 주소를 인자로 전달하여 데이터를 받아온다.  
이 때 사용하는 주소는 https를 권장한다.

<br/>

### **`.then()`**  
받은 데이터를 처리할 함수를 실행한다.  

`axios.get("")` 과 메소드 체이닝하여 사용한다.  

함수는 응답 받은 데이터를 매개변수로 사용한다.

<br/>

### **axios 예시**
```js
axios
  .get("주소")
  .then(res => console.log(res));
```

  <br/>
  <br/>

## **scrollMagic**
스크롤과 관련된 라이브러리이다.  

스크롤을 통해 해당 요소가 화면에 출력되면 클래스를 부여하고 해당 클래스를 CSS에서 제어하는 방법으로 사용이 가능하다.

아래의 메소드들을 체이닝하여 사용한다.

<br/>

### **`Scene()`**  
요소를 감시하는 옵션을 지정한다.

**옵션**

- **triggerElement**  
감시할 요소를 지정한다.

- **triggerHook**  
요소가 감지될 지점을 지정한다.  
뷰포트 최상단이 0, 최하단이 1이다.

### **`setClassToggle()`**  
요소가 감지되면 첫번째 인자로 전달한 요소에 두번째 인자로 전달한 클래스를 추가한다.  

<br/>

### **`addTo(new ScrollMagic.Controller())`**  
scrollMagic에 필수적인 메소드이다. 체이닝 마지막에 붙이면 된다.

<br/>

### **scrollMagic 예시**
특정 요소가 감지되면 클래스를 추가하고 그 클래스의 하위 요소에 대해 CSS 스타일을 선언하여  
특정 요소가 감지되면 하위 요소의 애니메이션이 동작하도록 처리할 수 있다.
```js
new ScrollMagic.Scene({
  triggerElement: containerEl,
  triggerHook: .9
  })
  .setClassToggle(containerEl, 'show')
  .addTo(new ScrollMagic.Controller())
```

<br/>
<br/>

# **팁**

<br/>

## **youtube**
유튜브 영상을 삽입하는 방법.

아래 내용을 별도의 js파일로 만들고 HTML에 불러오는데, 다른 스크립트보다 먼저 불러온다.


```js
const tag = document.createElement('script');

tag.src = "https://www.youtube.com/iframe_api";
const firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);


// 유튜브 영상을 삽입하고 객체 데이터로 다양한 옵션을 부여한다.
function onYouTubeIframeAPIReady() {
  new YT.Player('player', {          //영상이 삽입될 요소의 id, 앞에 #은 붙이지 않는다.
    videoId: 'G8UAwoUwnZg',          //삽입할 영상의 id, 유튜브 링크에 명시된다.
    playerVars: {                    //옵션부여
      autoplay: true,                   //자동재생 여부,
      loop: true,                       //루프 여부
      playlist: 'G8UAwoUwnZg'           //루프할 영상들 목록
    },
    events: {                        //
      onReady: function (event) {      //영상이 준비가 되면 익명함수를 실행한다. 매개변수 event는 영상이 실행될 때의 상황을 의미한다.
				event.target.mute()            //영상(target)을 음소거한다.
      }
    }
  });
}
```

<br/>
<br/>

## **OMBd**
query string으로 영화 정보를 불러온다.

<br/>

### **Query string**
query string은 입력한 데이터를 서버로 전달하는 방법 중 하나이며, 데이터를 `속성=값` 쌍으로 전달한다. 이 속성은 사전에 정의되어 있어야 한다.  

주소 엔드포인트 뒤에 `?`를 붙여서 쿼리스트링을 입력할 수 있다. 전달할 데이터가 복수인 경우 `&`을 사용하여 구분한다.

<br/>

### **요청**  
아래의 query string을 통해 정보를 받아오게 된다.
`https://www.ombdapi.com/?apikey=yourkey&`  
`apikey`는 홈페이지에서 사용자 인증을 통해 발급이 가능하다.

기본적인 속성으로 `s`가 있다. s는 영화 제목을 의미한다. 그 외 속성은 홈페이지 참고.

<br/>

### **axios를 활용한 출력**
```js
import axios from "axios"

function findMovie() {
  axios
    .get(`https://www.ombdapi.com/?apikey=key&s=title`)
    .then(res => {
      h1El.textContent = res.data.Search[0].Title;
      imgEl.src = res.data.Search[0].Poster;
    });
};
```
