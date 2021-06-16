# React Dev Tool
---
## React Developer Tools
---
- https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=ko
- 리렌더링 되는 컴포넌트 하이라이트

  [이미지]


<br>
<br>

## Redux DevTools
---
- https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?page=1&hl=ko&itemlang=en-GB

<br>


### 프로젝트에 적용
---
- 설치
```
$ npm install redux-devtools-extension
```


- index.js
```js
import React from 'react';
import ReactDOM from 'react-dom';
import { createStore } from "redux"; 
import { Provider } from "react-redux"; 
import App from './App';
import reportWebVitals from './reportWebVitals';
import rootReducer from './store/reducers/index';
import { composeWithDevTools } from 'redux-devtools-extension'; // 리덕스 개발자 도구


const store = createStore(rootReducer, composeWithDevTools());

ReactDOM.render(

  <Provider store={store}>
    <App />
  </Provider>
  ,
  document.getElementById('root')
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```


### Usage
---
- Inspector

  [이미지]

    - 현재 스토어의 상태
    - 어떤 액션들이 dispatch 되었는지 
    - 액션에 따라 상태가 어떻게 변화했는지
    - 액션을 직접 dispatch 하는 것도 가능

      [이미지]

<br>

- Log monitor
    - 기록을 변경할 수 있는 상태 및 작업의 로그
    - 시간 여행 가능

      [이미지]

        - 4번째 로그 클릭
        - 증가했던 로그가 삭제되면서
        - number가 2에서 1이됨






