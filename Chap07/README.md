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



### 확인문제



## 의견



