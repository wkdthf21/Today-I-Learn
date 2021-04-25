# Arrow Function
---
## 화살표 함수
---
- ES6에서 도입된 새로운 피처
- 코드를 간결하게 만들어 준다

```js
const regularRunction = function(){
    // ...
}

const arrowFunction = () => {
    // ...
}
```

<br>

- 괄호 안에 매개변수가 하나라면 괄호를 생략

```js
const twoParam = (name, age) => {
    return name + ' and ' + age;
}

const singleParam = name => {
    return name;
}
```

<br>

## 암묵적 변환 (Implict return)
---
- body가 한 줄이라면 return 키워드와 중괄호 {} 생략 가능

```js
const function = () => 'hello';
```

<br>

## React에서 어떻게 쓰이나요?
---
- React Component를 만들 때 화살표 함수를 사용할 수 있다

```js
const HelloWorld = (props) => {
    return <h1>{props.hello}</h1>
}
```

<br>

- 화살표 함수를 사용해서 만든 React Component는 ES6 class Component와 같다

```js
class HelloWorld extends Component{
    render(){
        return(
            <h1>{props.hello}</h1>
        );
    }
}
```

<br>

- 화살표 함수는 코드를 좀 더 간결하게 만들어 준다
- 대신 Component에서 라이프사이클을 활용하지 못한다는 단점이 있다
- 이런 종류의 Component를 **stateless 함수형 컴포넌트**라고 부른다
  - Hooks를 이용하면 함수형 컴포넌트에서도 라이프사이클을 이용할 수 있다고 합니다

<br>

