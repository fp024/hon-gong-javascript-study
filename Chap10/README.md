# Chapter 10. 리액트 라이브러리 맛보기

## 10-1 리액트의 기본

#### 리액트 라이브러리 사용 준비하기

* 리액트 라이브러리를 사용하는 기본적인 방법 

  * 아래 3개의 Javascript를 로딩

    ```javascript
    <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
    ```

  * Chrome에 React Dev Tools 설치

    * https://ko.reactjs.org/blog/2015/09/02/new-react-developer-tools.html#installation
    * https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi
      * 확장기능 설정에서 파일 수준에서 접근할 수 있게해야 예제 파일에서 사용할 수 있다.
    * 그외
      * FireFox
        * https://addons.mozilla.org/en-US/firefox/addon/react-devtools/

  * 바벨

    * 리엑트를 위해서 개발된 자바스크립트 확장 문법을 사용하여 바벨이란 변환기가 필요, 바벨로 적용할 부분을 지정해야함.

      ```javascript
      <script type="text/babel">
      ```

   *    프로덕션용 스크립트를 미리 컴파일 해야한다는 메시지

        * You are using the in-browser Babel transformer. Be sure to precompile your scripts for production - https://babeljs.io/docs/setup/

        * 로컬 파일에서만 확인해서, 지금은 특별히 신경안써도 될 것 같다.

          

          

#### 루트 컴포넌트 출력하기

* 컴포넌트 생성하기

  ```react
  <컴포넌트 이름></컴포넌트 이름>
  ```

  

* 컴포넌트 출력하기

  ```react
  ReactDOM.render(컴포넌트, 데이터)
  ```

  

* 바벨 REPL도구로 어떤식으로 코드가 바뀌는지 확인

  ```react
  // 컴포넌트와 컨테이너 생성하기
  const component = <h1>리액트 기본</h1>
  const container = document.getElementById('root')
  
  // 출력하기
  ReactDOM.render(component, container)
  ```

  ```javascript
  "use strict";
  
  // 컴포넌트와 컨테이너 생성하기
  const component = /*#__PURE__*/React.createElement("h1", null, "\uB9AC\uC561\uD2B8 \uAE30\uBCF8");
  const container = document.getElementById('root'); // 출력하기
  
  ReactDOM.render(component, container);
  ```

  

#### JSX 기본 문법

```react
<태그>{표현식}</태그>
<태그 속성={표현식}/> <!-- 따옴표를 사용하지 않음 -->
```

* 사전 컴파일이 안되어있어서 페이지 띄울때 느린 감이 있긴함..😅



#### 클래스 컴포넌트

클래스로 만드는 컴포넌트

```react
class 컴포넌트 이름 extends React.Component {
  render() {
    return <h1>출력할 것</h1>
  }
}
```

그외 함수로 만드는 컴포넌트도 있음. -> 함수 컴포넌트



#### 컴포넌트의 기본적이 속성과 메서드

* React.Component 클래스는 여러 속성과 메서드를 제공해줌
  * 필요에 따라 이 클래스를 상속해서 메서드를 오버라이드 해서 사용.

* 클래스의 메서드 오버라이드 하기

  ```react
  class App extends React.Component {
    constructor (props) {
      super(props) // React.Component 생성자가 여러 일을 하므로 부모 생성자를 호출해준다.
      // 생성자 코드
    }
  
    render () {
      // 출력할 것
    }
  
    componentDidMount () {
      // 컴포넌트가 화면에 출력될 때 호출
    }
  
    componentWillUnmount () {
      // 컴포넌트가 화면에서 제거될 때 호출
    }
  }
  ```

* state 속성 사용

  ```react
  // 상태 선언하기 (생성자 위치)
  this.state = { 속성: 값 }
  // 상태 변경하기 (이외의 위치)
  this.setState({ 변경할 속성: 값 })
  ```

  

#### 이벤트 연결하기

##### 컴포넌트에 이벤트 연결 방법

1. 메서드 선언
2. 메서드에 this 바인드
3. render() 메서드에서 출력하는 태그의 이벤트 속성에 메서드를 입력해서 연결

```react
class App extends React.Component {
  constructor (props) {
    super(props)
    this.메서드_이름 = this.메서드_이름.bind(this)  // (2) 메서드에 this를 바인드합니다
  }
  
  render () {
    return <h1 이벤트_이름={this.메서드_이름}></h1> // (3) 이벤트를 연결합니다.
  }

  메서드_이름 (event) {
    // 이벤트가 호출될 때 실행할 코드 // (1) 메서드를 선언합니다.
  }
}
```



#### 스타일 지정하기

```react
render () {
  const style = { }
  return <h1 style={style}>글자</h1>
}
```

| CSS 스타일 속성 이름 | 가능한 형태(1)               | 가능한 형태(2)                 |
| -------------------- | ---------------------------- | ------------------------------ |
| color: red           | {<br />  color: 'red'<br />} | {<br />  'color': 'red'<br />} |
| font-size: 2px       | {<br />  fontSize: 2<br />}  | {<br />  'fontSize': 2<br />}  |





### 확인 문제

1. ~~2~~  ==> 3
2. ~~4~~  ==> 2
3. 1
4. [10-1-exam-4.html](10-1-exam-4.html)
5. [10-1-exam-5.html](10-1-exam-5.html)
   * 난 따로 calc 함수를 만들어 계산했는데, 저자님은 option의 value에 직접 단위 값을 넣어서 해결하셨다.
   * select의 option에 defaultValue를 줘야지만 초기값이 state에 제대로 인식되었다.
6. [10-1-exam-6.html](10-1-exam-6.html)
   * 난 onBlur하고 onForcus 그대로 썼는데, 저자님은 componentDidMount(), componentWillUnmount()를 활용하셨다.



## 10-2 리액트와 데이터

### 여러 개의 컴포넌트 사용하기



### 부모에서 자식의 state 속성 변경하기

* 부모에서 자식 컴포넌트로 어떤 데이터를 전달할 때는 this.props 사용 이후 화면 내용을 변경할 때도 this.props 사용

* [10-2-2.html](10-2-2.html)

  * 부모에서 타이머를 통해 계속 시간을 1초마다 상태를 바꾸면서 Item의 state를 바꾸는데, 그냥은 화면 출력을 바꿀 수는 없고, `componentDidUpdate(prevProps)` 메서드를 오버라이드 해서 여기서 변경값을 state를 설정해야 바뀔 수 있다.

    ```javascript
    componentDidUpdate(prevProps) {
      // 자식 컴포넌트에서 변경을 적용할 때 사용하는 코드
      if (prevProps.value !== this.props.value) {
        this.setState({
          value: this.props.value,
        })
      }
    }
    ```

    

### 자식에서 부모의 state 속성 변경하기

부모 컴포넌트에서 자신(부모)의 속성을 변경하는 메서드를 자식에게 전달한 뒤, 자식에서 이를 호출하게 만듦

* [10-2-4.html](10-2-4.html)



### 리액트로 만드는 할 일 목록 애플리케이션

* [10-2-5.html](10-2-5.html)

  * key를 지정하는 것을 경로 로그로 권장하는데, 이 때문에 TodoItem 컴포넌트에 key를 todo.key를 값으로 지정했다. 단순하게 생각해서 기존 dataKey를 key 같이 쓸수 없지 않나라고 생각할 수 있는데, 이것은 컴포넌트의 props로 전달되지 않는다고 함. 그래서 저자님이 dataKey라는 것을 따로 만드신 것 같다.

    * https://ko.reactjs.org/warnings/special-props.html

    * https://ko.reactjs.org/docs/lists-and-keys.html#keys

      

## 의견

* react 부분은 역시 어려워서 생활코딩 리엑트 기초를 모두 본다음에 연습문제를 풀었다. 기초를 익히니 좀 이해가 간다. 😂😂😂
* 마지막의 TODO 리스트 만드는 것은 무념무상으로 따라치긴 했는데, key 경고가 나오던 부분은 검색해서 고쳐봤다.



#### 정오표

* p430 `</컴포넌트 f이름>` 에서 f가 빠지면 되겠다.
