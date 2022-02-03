# Chapter 04. 반복문

## 04-1 배열

* 배열 뒷부분에 요소 추가하기

  * 배열.push(요소)

* 자바스크립트에서 배열의 길이는 고정이 아님

  ```javascript
  > const fruitsA = ['사과', '배', '바나나']
  undefined
  
  > fruitsA[10] = '귤'
  '귤'
  
  > fruitsA
  (11) ['사과', '배', '바나나', 비어 있음 × 7, '귤']
  ```

* 배열의 마지막 위치에 요소추가

  ```javascript
  > const fruitsA = ['사과', '배', '바나나']
  undefined
  
  > fruitsA[fruitsA.length] = '귤'
  '귤'
  
  > fruitsA
  (11) ['사과', '배', '바나나', '귤']
  ```



### 배열 요소 제거하기

##### 인덱스로 제거

```javascript
배열.splice(인덱스, 제거할 요소의 개수)
```

```javascript
> const itemsA = ['사과', '배', '바나나']
undefined

> itemsA.splice(2, 1) // 배열의 2번째 인덱스로 부터 1개의 요소를 제거함.
['바나나']   // 제거된 요소가 배열로 리턴됨

> itemsA
(2) ['사과', '배']
```



##### 값으로 요소 제거하기

indexOf로 값의 인덱스를 찾은뒤에, splice로 제거

```javascript
const 인덱스 = 배열.indexOf(요소)
배열.splice(인덱스, 1)
```

* 문자열의 indexOf()

  ```javascript
  > const stringA = '동해물과 백두산이 마르고 닳도록'
  undefined
  
  > stringA.indexOf('백두산')
  5
  ```

* 배열 내부에서 특정 값을 가진 요소 모두 제거하기

  indexOf()와 splice()메서드는 배열 내부요소 하나만 제거할 수 있음, 특정 값을 가진 요소를 모두 제거하고 싶을 때는 filter() 메서드를 사용!

  ```javascript
  > const itemE = ['사과', '배', '바나나', '귤']
  undefined
  
  > itemE.filter((item) => item != '귤')
  (3) ['사과', '배', '바나나']
  ```

  

### 배열의 특정 위치에 요소 추가하기

```javascript
배열.splice(인덱스, 0, 요소)
```

```javascript
> const itemsD = ["사과", "귤", "바나나", "오랜지"]
undefined

> itemsD.splice(1, 0, "양파")
[]

> itemsD
(5) ['사과', '양파', '귤', '바나나', '오랜지']
```



### 자료의 비파과와 파괴

* **비파괴적 처리**: 처리 후에 원본 내용이 변경되지 않음.
* **파괴적 처리**: 처리 후에 원본 내용이 변경됨.
  * 앞에서 다뤘던 push(), splice()등을 사용해 배열 자체를 바꾸는 파괴적 처리를함.

* 배열과 같이 거대해질 수 있는 자료는 메모리를 절약할 수 있게 대부분 **파괴적 처리**로 되어있음.
* 메모리가 여유로운 현대의 프로그래밍 언어와 라이브러리는 자료 보호를 위해 대부분 **비파괴적 처리**를함.
  * 최근 표준화 된 것들은 비파과적 처리를 많이함.



### 확인 문제

1. 문제1

   1. "3"
   2. "바나나"
   3. 32

2. 실행결과

   ```
   4
   [1, 2, 3, 4, 5]
   ```

3. 파괴적 비파괴적 구분

   1. 비파괴적 처리
   2. 파과적 처리
   3. 비파괴적 처리
   4. 비 파괴적 처리





## 04-2 반복문



### 확인 문제

1. 실행결과

   ```
   # for in 반복문
   0
   1
   2
   3
   # for of 반복문
   사과
   배
   귤
   바나나
   ```

2. 실행결과

   ```
   for문의 증감변수 i가 const로 선언되어있어 오류가 난다.
   Uncaught TypeError: Assignment to constant variable.
   
   for문의 conet i를 let i로 바꾸면 오류가 없다. 
   [3, 6, 9]
   ```

3. [4-2-exam-3.html](4-2-exam-3.html)

   ```
   1~100까지의 곱: 9.33262154439441e+157
   ```

   

4. [4-2-exam-4.html](4-2-exam-4.html)





## 의견

* 마지막 다이아몬드 그리는게 은근히 힘들었다. 😅😅😅

