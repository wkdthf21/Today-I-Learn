# let과 const
---
- 공통점
  - 변수 선언시 사용
- 차이점
  - const로 선언한 변수는 선언 이후 값을 바꿀 수 없다
  - let으로 선언한 변수는 바꿀 수 있다
    - 그래서 함수 스코프 안에서 let으로 선언한 변수는 함수 밖에서 호출할 수 없다

<br>

## 둘 중 어떤걸 써야 하나요?
---
- 정해진 규칙이 있는건 아니지만
- 변수 선언은 우선 const로 하고
- 선언한 변수를 바꿔야할 때 let으로 바꿔라

<br>

## React에서는 어떻게 쓰일까?
---
- 변수가 필요한 모든 곳에서

```js
import React, { Component } from 'react';

class App extends Component {
    render(){
        const greeting = 'Hello React!';
        return(
            <h1>{greeting}</h1>
        );
    }
}
```
- greeting 변수는 어플리케이션 전체 생명주기 동안 변하지 않기 때문에 const 키워드 사용


<br>

