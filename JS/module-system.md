# module-system
---
## ES6 모듈 시스템
---
- js가 모듈을 import하고, 선언하여 내보낼 수 있게 export 해줌


<br>

## export / import
---
- 모듈은 **export** 키워드를 통해 하나 혹은 여러 값을 선언하여 외부로 내보낼 수 있게 해주는 JS 파일

- JS 파일을 **import** 할 때는 확장자를 생략해도 된다

- **default export**
  - 모듈 하나에 딱 한 개만 허용됨
  - **{}를 사용하지 않으면서, 상응하는 이름 없이도 import가 가능**

- **named export**
  - 모듈 하나에 여러 개가 있을 수 있음
  - {}를 사용해서 import 해야하고
  - 정확한 이름도 명시해줘야 함
  - as를 사용하면 별칭 사용 가능

```js
// util.js 파일
// default export
export default function square(x) {
    return x * x;
}

// named export
export function plusTwo(num) {
    return num + 2;
}

```

```js
// App.js 파일
// named export
import {plusTwo as plus2} from './util.js'

// default export
import s from './util.js'

console.log(plus2(5)); // 7
console.log(k(7)); // 49
```

<br>


- 절대 이름(absolute name)을 이용해서 import하는 것도 가능
```js
import React from 'react';
```
- 절대 이름을 사용해서 import할 때는 패키지 이름을 **node_modules**에서 검색한다

<br>


## React에서는 어떻게 쓰이나요?
---
- 예시 : export된 App 컴포넌트가 렌더링되고 있는 index.js 파일

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

- ./App 디렉토리에서 import한 App은 js 파일이라 확장자를 쓰지 않았다
- react-dom은 DOM 렌더링에 사용되는 노드 모듈