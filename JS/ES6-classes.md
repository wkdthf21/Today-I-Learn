# ES6 classes
---
## ES6 
---
- ECMA 스크립트
- Ecma International이 ECMA-262 기술 규격에 따라 정의하고 있는 표준화된 스크립트 프로그래밍 언어
- JS를 표준화하기 위해서 만들어짐

<br>

## ES6 클래스
---
- ES6에서 객체지향언어에서 사용되는 클래스가 도입됨

```js
class Person {
    constructor(name, age){
        this.name = name;
        this.age = age;
    }

    hello() {
        return 'Hello World! I am ' + this.name + ' and I am ' + age + 'years old';
    }
}
```
```js
var me = new Person('wkdthf21', '25');
me.hello();
```

<br>

## 클래스 상속
---
```js
class Child extends Person {
    playGames() {
        return 'playing games...';
    }

    // hello를 오버라이드
    hello(){
        return 'Hello World! I am ' + this.name + ' and I am young !';
    }
}
```


<br>

## React에서의 ES6 클래스와 상속
---
- React 클래스는 React Component
- Component는 단순히 React 패키지로부터 import한 React Component 클래스를 상속받은, ES6 클래스

```js
import React, { Component } from 'react';

class App extends Component {
    render(){
        return(
            <h1>Hello React!<h1>
        );
    }
}
```
- React 컴포넌트 클래스를 상속받았기 때문에 render(), JSX, this.state등 다양한 메서드를 사용할 수 있다
- 이 메서드들이 모두 Component 클래스에 정의되어 있기 때문

<br>



