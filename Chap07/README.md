# Chapter 07. 문서 객체 모델

## 07-1 문서 객체 조작하기

#### DOMContentLoaded 이벤트

```javascript
document.addEventListener('DOMContentLoaded', () => {
    // 문장
})
```

#### 문서 객체 가져오기

* 웹브라우저에서 당연히 있을 것이라 전제하고 만든 속성

  ```javascript
  document.head
  document.body
  document.title
  ```

* head나 body 내부에 만든 다른 요소는 별도의 메서드를 사용해서 접근함.

  ```javascript
  document.querySelector(선택자)
  document.querySelectorAll(선택자)
  ```

* 많이 쓰이는 선택자 예)

  | 이름          | 선택자 형태     | 설명                                 |
  | ------------- | --------------- | ------------------------------------ |
  | 태그 선택자   | 태그            | 특정 태그를 가진 요소를 추출         |
  | 아이디 선택자 | #아이디         | 특정 id 속성을 가진 요소를 추출      |
  | 클래스 선택자 | .클래스         | 특정 class 속성을 가진 요소를 추출   |
  | 속성 선택자   | \[속성=값]      | 특정 속성 값을 갖고 있는 요소를 추출 |
  | 후손 선택자   | 선택자A 선택자B | 선택자A 아래에 있는 선택자B를 선택   |



#### 글자 조작하기

| 속성 이름             | 설명                                    |
| --------------------- | --------------------------------------- |
| 문서_객체.textContent | 입력된 문자열을 그대로 넣습니다.        |
| 문서_객체.innerHTML   | 입력된 문자열을 HTML 형식으로 넣습니다. |



#### 속성 조작하기

| 메서드 이름                             | 설명                    |
| --------------------------------------- | ----------------------- |
| 문서\_객체.setAttribute(속성\_이름, 값) | 특정 속성에 값을 지정함 |
| 문서\_객체.getAttribute(속성\_이름)     | 특정 속성을 추출        |



#### 문서 객체 생성하기

```javascript
document.createElement(문서_객체_이름)

부모_객체.appendChild(자식_객체)
```



#### 문서 객체 이동하기

문서 객체의 부모<sup>parent</sup>는 언제나 하나이여야하기 때문에.. 문서 객체를 다른 문서 객체에 추가하면 문서 객체가 이동됨

* [7-1-9.html](7-1-9.html)



#### 문서 객체 제거하기

```javascript
부모_객체.removeChild(자식_객체)
```



#### 이벤트 설정하기

* 이벤트 연결
  ```javascript
  문서_객체.addEventListener(이벤트_이름, 콜백_함수)
  ```

* 이벤트 제거

  ```javascript
  문서_객체.removeEventListener(이벤트_이름, 이벤트_리스너)
  ```

  



### 확인문제

1. 2
2. 선택자
   1. `#header` / `h1` / `h1#header`
   2. `.active` / `span` / `span.active`
   3. `#name-input` / `input` / `input#name-input` / `input[type="text"]` / `input[name="name"]`
3. 4
4. 식별자
   1. borderRadius
   2. fontFamily
   3. lineHeight
   4. width
   5. boxSizing





## 07-2 이벤트 활용

#### 이벤트 모델

* **표준 이벤트 모델** : addEventListener() 메서드 사용

  ```javascript
  document.body.addEventListener('keyup', ()=> {
  
  })
  ```

* **고전 이벤트 모델** : onXXX로 시작하는 속성에 함수를 할당해서 사용

  ```javascript
  document.body.onkeyup = (event) => {
  
  }
  ```

* **인라인 이벤트 모델** : onXXX으로 시작하는 속성을 HTML 요소에 직접 넣어서 이벤트를 연결

  ```html
  <script>
    const listener = (event) => {
        
    }
  </script>
  
  <body onkeyup="listener(event)">
    
  </body>
  ```

현재는 표준 이벤트 모델과, 인라인 이벤트 모델(프레임 워크등에서 사용)이 주로 사용됨



#### 키보드 이벤트

| 이벤트   | 설명                                                         |
| -------- | ------------------------------------------------------------ |
| keydown  | 키가 눌릴 때 실행됨. 키보드를 꾹 누르고 있을 때도, 입력될 때도 실행됨. |
| keypress | 키가 입력 되었을 때 실행됨. 그러나 웹 브라우저에 따라서 아시아권의 문자를 제대로 처리하지 못하는 문제가 있음. |
| keyup    | 키보드에서 키가 떨어질 때 실행됨                             |

* 아시아권 문자에서 keydown, keypress 처리에 문제가 있을 수 있어 보통 keyup을 사용함.



#### 키보드 키 코드 사용하기

| 이벤트 속성 이름 | 설명                      |
| ---------------- | ------------------------- |
| code             | 입력한 키                 |
| keyCode          | 입력한 키를 나타내는 숫자 |
| altKey           | `[Alt]` 키를 눌렀는지     |
| ctrlKey          | `[Ctrl]` 키를 눌렀는지    |
| shiftKey         | `[Shift]` 키를 눌렀는지   |



#### 이벤트 발생 객체

코드의 규모가 커져서, 이벤트 리스너를 외부로 분리 했을 때, 리스터에서 문서 객체 접근시 아래 2가지 속성을 사용할 수 있음.

1. `event.currentTarget` 속성 사용

2. `this` 키워드 사용

   this키워드로 참조할 때는 리스너 구현 함수는 화살표 함수로 만들면 안됨



#### 기본 이벤트 막기

* 기본이벤트
  * 어떤 이벤트가 발생했을 때, 웹 브라우저가 기본적으로 처리해주는 이벤트



#### localStorage 객체

* localStorage.getItem(키)
  * 저장된 값을 추출, 없으면 undefined
* localStorage.setItem(키, 값)
  * 값을 저장
* localStorage.removeItem(키)
  * 특정 키의 값을 제거
* localStorage.clear()
  * 저장된 모든 값을 제거





### 확인문제

1. 이벤트 모델의 이름과 코드 연결

   1. a -> 3
   2. b -> 2
   3. c -> 1

2. 3

3. 이벤트 이름과 이벤트가 발생하는 상황 연결

   1. a -> 2
   2. b -> 1
   3. c -> 3
   4. d -> 4

4. 1

5. 2, 3

6. 입력 양식들을 활용해서 만들 수 있는 프로그램

   * 이부분은 생략하자.

   

## 의견

점점 어려워지고 있다. 😄😄😄



