

# Chapter 05. 함수

## 05-1 함수의 기본 형태

* p216에 첫번째 예제에 undefined 에 따옴표를 넣어줘야했다. ([5-1-16-1.html](5-1-16-1.html))

  ```javascript
        wage = typeof (wage) != 'undefined' ? wage : 8590
        hours = typeof (hours) != 'undefined' ? hours : 52
  ```

* 매개변수로 들어오는 값이 false 또는 false로 변환되는 값 (0, 빈문자열) 등이 아니라는 게 확실하면 짦은 조건문 사용가능 ([5-1-16-2.html](5-1-16-2.html))

  ```javascript
        wage = wage || 8590
        hours = hours || 52
  ```

  

### 확인 문제

1. [5-1-exam-1.html](5-1-exam-1.html)
2.  문제
   1. [5-1-exam-2-1.html](5-1-exam-2-1.html)
   2. [5-1-exam-2-2.html](5-1-exam-2-2.html)
   3. [5-1-exam-2-3.html](5-1-exam-2-3.html)



## 05-2 함수 고급

* 콜백 함수 (callback)
  * 매개변수로 전달하는 함수

* 화살표 함수

  ```javascript
  (매개변수) => {
  
  }
  ```

  ```javascript
  (매개변수) => 리턴값
  ```

* 타이머 함수

  | 함수 이름               | 설명                                    |
  | ----------------------- | --------------------------------------- |
  | setTimeout(함수, 시간)  | 특정 시간 후에 함수를 한 번 호출합니다. |
  | setInterval(함수, 시간) | 특정 시간마다 함수를 호출합니다.        |

* 타이머 함수 종료

  | 함수 이름                | 설명                                             |
  | ------------------------ | ------------------------------------------------ |
  | clearTimeout(타이머_ID)  | setTimeout() 함수로 설정한 타이머를 제거합니다.  |
  | clearInterval(타이머_ID) | setInterval() 함수로 설정한 타이버를 제거합니다. |

* 엄격 모드의 일반적인 사용패턴

  블럭의 최상단에 선언

  ```html
  <script>
  	(function() {
        'use strict'
        문장
        문장
      })()
  </script>
  ```

* 익명함수, 선언적함수 둘중에 하나로 통일해서 사용하는 것이 낫고, 가능하면 익명함수를 사용하는 것이 나음.



### 확인문제

1. [5-2-exam-1.html](5-2-exam-1.html)
2. [5-2-exam-2.html](5-2-exam-2.html)



## 의견

* 지금 부터는 내용이 꽤 많이 시작했다. 😃

