# Destructuring-Assignment
---
## 구조 분해 할당
---
- ES6에 새로 도입
- 구조 분해 할당을 사용하면 **객체나 배열 일부를 쉽게 변수로 해체할 수 있다**

<br>

## 객체에서의 구조 분해 할당
---
- key를 사용해서 분해
- 새로운 변수에 할당하고 싶을 때는 <key : 새로운 변수>

```js
const person = {
    name : 'wkdthf21',
    age : 25,
    height : 163
}

const {name, age} = person;
console.log(name) // wkdthf21
console.log(age) // 25
console.log(person) // return person object

const {name : id} = person;
console.log(id); // wkdthf21
```
<br>

## 배열에서의 구조 분해 할당
---
- 배열에서는 key가 아니라 배열 순서대로 대응
- , 를 이용하면 중간 index를 건너뛰고 할당할 수 있다

```js
const nums = [1, 2, 3, 4, 5];
const [one, two] = numbers;
// one = 1, two = 2
const [one, two, , four] = numbers;
// one = 1, two = 2, four = 4
```

<br>

## React에서는 어떻게 쓰일까?
---
- 매서드 안에서 state를 해체할당 하는데 자주 사용된다

```js
reactFunction = () => {
    const { name, age } = this.state;
}
```

<br>

- stateless 함수형 컴포넌트에서도 자주 사용된다

- 원래 코드
```js
const HelloWorld = (props) => {
    return <h1>{props.hello}</h1>;
}
```

- 매개변수를 바로 분해해서 대입하는 코드
```js
const HelloWorld = ({hello}) => {
    return <h1>{hello}</h1>;
}
```