# Chapter 06. 객체

## 06-1 객체의 기본

#### 화살표 함수를 사용한 메서드

객체의 메서드에 화살표 함수를 사용하면 내부에 this가 가리키는 대상이 그 객체가 아닌 다른 것이 될 수 있음. 그 이유로 메서드에는 화살표 함수를 사용하지 않고 익명 함수를 씀.

* [6-1-5.html](6-1-5.html)
  * 익명함수는 this의 대상이 Window 객체, 그런데, 환경에 따라 달라질 수 있음. (node 상에서 실행하면 다르겠다...)



### 확인 문제

1. [6-1-exam-1.html](6-1-exam-1.html)
2. 3
3. 1
4. [6-1-exam-4.html](6-1-exam-4.html)
   * 빵은 스페인어로 pan입니다.



## 06-2 객체의 속성과 메서드 사용하기

#### 기본 자료형

* 숫자, 문자열, 불

#### 기본 자료형을 객체로 선언

```javascript
> const g = Number(1)  // 기본 자료형으로 생성됨
undefined
> g.sample = 10   // 속성을 추가하려해도 추가가 안된다.
10
> g
1
> const o = new Number(1)  // 객체로 생성됨
undefined
> o.sample = 10   // 속성이 추가된다.
10
> o
Number {1, sample: 10}
```

#### 기본 자료형의 일시적 승급

* Javascript는 사용의 편리성을 위해 기본 자료형의 속성과 메서드를 호출 할 때, 일시적으로 기본자료형을 객체로 승급시킴

  ```javascript
  > '안녕하세요'.anchor('greeting')
  '<a name="greeting">안녕하세요</a>'
  > '안녕하세요'.bold()
  '<b>안녕하세요</b>'
  ```



#### Number 객체

* 숫자 N번째 자릿수까지 출력하기: toFixed

  ```javascript
  > const l = 123.456789
  undefined
  > l.toFixed(2)
  '123.46'
  > l.toFixed(3)
  '123.457'
  > l.toFixed(4)
  '123.4568'
  ```

* NaN과 Infinity 확인하기: isNaN(), isFinite()

  ```javascript
  > const m = Number('숫자로 변환할 수 없는 경우')
  undefined
  > m
  NaN
  > m === NaN // NaN과 비교해서는 NaN인지 확인할 수 없음
  false
  > Number.isNaN(m)
  true
  ```

  ```javascript
  > const n = 10 / 0
  undefined
  > n
  Infinity      // 양의 무한대
  > const o = -10 / 0
  undefined
  > o
  -Infinity    // 음의 무한대
  > Number.isFinite(n)    // 유한한 수인지 검사
  false
  > Number.isFinite(o)
  false
  
  > Number.isFinite(1)
  true
  > Number.isFinite(10)
  true
  
  ```

  무한대 값은 비교 연산자(===)로 비교 가능



#### String 객체

* 문자열 양쪽 끝의 공백 없애기: trim()

  ```javascript
  > const stringA = `
        메시지를 입력하다보니 앞에 줄바꿈도 들어가고`
  undefined
  > const stringB = `    앞과 뒤에 공백도 들어가고      `
  undefined
  > stringA
  '\n      메시지를 입력하다보니 앞에 줄바꿈도 들어가고'
  > stringB
  '    앞과 뒤에 공백도 들어가고      '
  > stringA.trim()
  '메시지를 입력하다보니 앞에 줄바꿈도 들어가고'
  > stringB.trim()
  '앞과 뒤에 공백도 들어가고'
  ```

* 문자열을 특정 기호로 자르기: split()

#### JSON 객체

* JSON 형식 규칙
  * 값을 표현할 때는 문자열, 숫자, 불 자료형만 사용할 수 있음 (함수등은 사용불가)
  * 문자열은 반드시 큰 따옴표로 만들어야합니다.
  * 키<sup>key</sup>에도 반드시 따옴표를 붙여야 합니다.

#### 프로토타입 객체

객체의 틀을 의미하며, 이곳에 속성과 메서드를 추가혀면 해당 객체 전체에서 사용할 수 있음.



### 확인 문제

1. [6-2-exam-1.html](6-2-exam-1.html)

   * `Uncaught TypeError: num.원 is not a function`
   * num 이 객체가 아니다. 제대로 출력하기 위해서는 num = new Number(52000) 으로 넣어야함.
     * 모든 Number에 원() 함수를 추가하려면 prototype에 추가해야함.

2. [6-2-exam-2.html](6-2-exam-2.html)

   ```javascript
   printLang("ko"): 한국어
   printLang("en"): 영어
   ```

3. [6-2-exam-3.html](6-2-exam-3.html)

   ```javascript
   // Math.sin(x)에서 x파라미터를 라디안으로 받으므로, 각도 90을 라디안으로 바꿔야한다.
   function toRadian(degree) {
     return degree * (Math.PI / 180)
   }
   let sin90 = Math.sin(toRadian(90))
   console.log('sin 90:', sin90)
   ```

4. 2

5. [6-2-exam-5.html](6-2-exam-5.html)





## 06-3 객체와 배열 고급

#### 배열 기반의 다중 할당

* 다중 할당

  ```javascript
  [식별자, 식별자, 식별자, ...] = 배열
  ```

  ```javascript
  > let [a, b] = [1, 2]
  undefined
  > console.log(a, b)
  1 2
  undefined
  > [a, b] = [b, a]
  (2) [2, 1]
  > console.log(a, b)
  2 1
  undefined
  ```

  ```javascript
  let arrayA = [1, 2, 3, 4, 5]
  undefined
  const [a, b, c] = arrayA
  undefined
  console.log(a, b, c)
  1 2 3
  undefined
  ```

#### 객체 전개 연산자

* 전개 연산자를 사용한 객채 복사

  ```javascript
  {...객체}
  ```

  

### 확인 문제

1. 2

2. `popular javascript libraries 2022`

   1. jQuery library

      ```
      jQuery는 빠르고 작고 기능이 풍부한 JavaScript 라이브러리입니다. 여러 브라우저에서 작동하는 사용하기 쉬운 API를 사용하여 HTML 문서 탐색 및 조작, 이벤트 처리, 애니메이션 및 Ajax와 같은 작업을 훨씬 더 간단하게 만듭니다. 다목적성과 확장성의 조합으로 jQuery는 수백만 명의 사람들이 JavaScript를 작성하는 방식을 변화시켰습니다.
      ```

   2. React library

      사용자 인터페이스를 만들기 위한 JavaScript 라이브러리

      * 선언형
        * React는 상호작용이 많은 UI를 만들 때 생기는 어려움을 줄여줍니다. 애플리케이션의 각 상태에 대한 간단한 뷰만 설계하세요. 그럼 React는 데이터가 변경됨에 따라 적절한 컴포넌트만 효율적으로 갱신하고 렌더링합니다.
        * 선언형 뷰는 코드를 예측 가능하고 디버그하기 쉽게 만들어 줍니다.
      *  컴포넌트 기반
        * 스스로 상태를 관리하는 캡슐화된 컴포넌트를 만드세요. 그리고 이를 조합해 복잡한 UI를 만들어보세요.
        * 컴포넌트 로직은 템플릿이 아닌 JavaScript로 작성됩니다. 따라서 다양한 형식의 데이터를 앱 안에서 손쉽게 전달할 수 있고, DOM과는 별개로 상태를 관리할 수 있습니다.
      * 한 번 배워서 어디서나 사용하기
        * 기술 스택의 나머지 부분에는 관여하지 않기 때문에, 기존 코드를 다시 작성하지 않고도 React의 새로운 기능을 이용해 개발할 수 있습니다.
        * React는 Node 서버에서 렌더링을 할 수도 있고, [React Native](https://reactnative.dev/)를 이용하면 모바일 앱도 만들 수 있습니다.

   3. D3.js library

      ```
      D3.js는 데이터를 기반으로 문서를 조작하기 위한 JavaScript 라이브러리입니다. D3는 HTML, SVG 및 CSS를 사용하여 데이터에 생명을 불어넣는 데 도움이 됩니다. 웹 표준에 대한 D3의 강조는 강력한 시각화 구성 요소와 DOM 조작에 대한 데이터 중심 접근 방식을 결합하여 독점 프레임워크에 자신을 묶지 않고도 최신 브라우저의 모든 기능을 제공합니다.
      ```

   4. Underscore library

      ```
      Underscore는 내장 객체를 확장하지 않고도 유용한 함수형 프로그래밍 도우미를 제공하는 JavaScript 라이브러리입니다
      ```

   5. Lodash library

      Lodash는 배열, 숫자, 객체, 문자열 등으로 작업하는 번거로움을 없애 JavaScript를 더 쉽게 만듭니다.
      Lodash의 모듈식 방법은 다음과 같은 경우에 적합합니다.

      * 배열, 객체 및 문자열 반복
      * 값 조작 및 테스트
      * 복합 함수 만들기

      

## 의견

* 재미있었다. 😁😁😁

