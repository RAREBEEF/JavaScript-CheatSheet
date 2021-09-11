# **JavaScript**

> **JavaScript**

JavaScript(이하 **JS**)는 웹 개발에서 콘텐츠를 바꾸고 움직이는 등 페이지의 동적 처리를 담당한다.

<br/>
<br/>

# **자료형**

## **String**
```js
const str = "Hello, world!";
```
String은 문자열 리터럴을 말하며, 따옴표로 감싸서 작성한다. 

우리가 흔히 말하는 문자, 글자는 물론 숫자 또한 따옴표로 감싸서 작성하면 문자열 리터럴이 된다.

백틱(``)으로 감싸는 작성법은 **보관법**으로, `${}`를 이용하여 변수에 할당된 값을 출력하는 기능을 갖고 있다.

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

## **Object**
```js
const me = {
  name: "RAREBEEF",
  age: 4
};


console.log(me.name);
console.log(me["age"]);
```
객체라고 부르며, 여러 데이터를 `key: value` 쌍으로 저장한다.  

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