# Props & Childern
---
## Props 사용법
---
- 컴포넌트 내부에서 코드를 작성한다
~~~ js
<Hello name = "react"></Hello>
~~~
- 받는 컴포넌트에서는 props라는 예약어를 통해 받는다
~~~ js
function Hello(props) {
  return (
    <div>
      안녕하세요 {props.name}
    </div>
  )
}
~~~

<br/>

## 비구조화 할당
---
- 컴포넌트 파라미터 안에서 {} 안에 받는 내용을 미리 표기한다
~~~ js
function Hello({name}) {
  return (
    <div>
      안녕하세요 {name}
    </div>
  )
}
~~~

<br/>

## defaultProps
---
- props에 값이 할당되지 않았을 때 사용할 default 값을 설정할 수 있다

~~~ js
function Hello({name}) {
  return (
    <div>
      안녕하세요 {name}
    </div>
  )
}

Hello.defaultProps = {
  name : "아무거나"
}
~~~

<br/>

## props.children
- 컴포넌트 태그 사이에 값이 껴 있을때, childern이란 예약어를 사용해 컴포넌트 태그 사이에 껴 있는 값을 가져올 수 있다.

~~~ js
// Wrapper.js
function Wrapper( {children} ) {
  const style = {
    backgroundColor : "red"
  }
  return (
    <div style={style}>
      {childern}
    </div>
  )
}
~~~

~~~ js
// App.js
function App() {
  return (
    <Wrapper>
      <Hello name="react" color="red" />
      <Hello color="pink"/>
    </Wrapper>
  );
}
~~~

- Wrapper.js에서 태그 사이에 껴있는 Hello를 props.children이라는 예약어를 통해 조회하지 않으면 렌더링 되지 않는다.
