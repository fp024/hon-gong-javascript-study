# Chapter 02. 자료와 변수

## 02-1 기본 자료형

* 문자열 선택 연산
  * '안녕하세요'[2] 
    *  '하' 
    * 인덱스는 0부터 시작
* 숫자 자료형
  * 소수점이 있든 없든 모두 같은 숫자 자료형 


* 자료형 검사
  * typeof 10 === 'number' 
    * true

* 템플릿 문자열 (backtick 사용(`` ` ``))
  * console.log(`` `표현식 273 + 52의 값은 ${273 + 52}입니다! ` ``)
    표현식 273 + 52의 값은 325입니다!



### 문제 

1. 문제

   1. boolean
   2. number
   3. number
   4. boolean

2. 문제

   ```
   # 연습문제
   \\\\
   ```

3. 문제

   ```
   '녕'
   '하'
   '세'
   '요'
   ```

4. 문제

   ```
   0
   4
   ```

   



## 02-2 상수와 변수

* 상수 선언

  ```javascript
  const 이름 = 값
  ```

* 변수 선언

  ```javascript
  let 이름 = 값
  ```

* undefined 자료형

  ```javascript
  typeof(abc) // abc는 정의하지 않은 식별자
  >> undefined
  ```

  * 상수나 변수로 선언하지 않은 식별자

  * 변수를 선언하면서 값을 지정하지 않은 경우

    ```javascript
    let l
    >> undefined
    typeof(l)
    >> 'undefined'
    ```

    

### 문제

1. 문제

   * 1

2. 문제

   * 2

3. 문제

   1. `Uncaught SyntaxError: Missing initializer in const declaration`

   2. 에러 없음

      ```
      넓이 = 314
      2-2-exam-3-2.html:14 둘레 = 62.800000000000004
      ```

4. 문제

   ```
   11
   11
   13
   13
   
   틀림..
   const number 였다. 😥
   ```

   

   

## 02-3 자료형 변환

* 문자열 입력

  ```javascript
  const input = prompt('message', '_default')
  ```

* bool 입력

  ```javascript
  const input = confirm('수락하시겠습니까?')
  ```

* 숫자 자료형으로 변환하기

  ```javascript
  Number("273")
  > 273
  typeof(Number("273"))
  > 'number'
  Number("$273")
  > NaN
  typeof(Number("$273")) // NaN이 타입은 number임
  ```

  

* 문자열 자료형으로 변환하기

  ```javascript
  String(자료)
  ```

  ```javascript
  String(52.273)
  > '52.273'
  String(true)
  > 'true'
  String(false)
  > 'false'
  ```

* 불 자료형으로 변환하기

  ```javascript
  Boolean(자료)
  ```

  ```javascript
  Boolean(0)
  > false
  Boolean(NaN)
  > false
  Boolean("")
  > false
  Boolean(null)
  > false
  let i
  > undefined
  Boolean(i)
  > false
  ```

* 논리 부정연산자를 사용해 자료형 변환하기

  ```javascript
  !!273
  > true
  !!0
  > false
  !!'안녕하세요'
  > true
  !!''
  > false
  ```

  * 다른 자료형에 논리부정연산자(!!)를 사용하면 불자료형으로 바꿀 수 있음. 



### 확인 문제

1. 문제
   * 3
2. 문제
   1. String()
   2. Boolean()
3. 문제
   * [2-3-exam-3.html](2-3-exam-3.html)
4. 문제
   * [2-3-exam-4.html](2-3-exam-4.html)
5. 문제
   * [2-3-exam-5.html](2-3-exam-5.html)
6. 문제
   1. 미터 - 마일 계산
   2. 킬로그램 - 파운드 계산
   3. Byte - GB 계산





## 의견

* 백틱 않의 ${} 구문안에 계산식 넣을 수 있는 것을 잊고 있었다.
* 6번의 저자님 답을 보니, 역시 저자님 사고가 다양함 😃



