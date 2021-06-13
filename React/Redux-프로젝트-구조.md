# Redux 프로젝트 구조
---
## components
---
- Redux와 연동되지 않은 컴포넌트
- 단순히 보여주기 위한 컴포넌트로 **프레젠테이션 컴포넌트**라고 부른다

<br>

## containers
---
- Redux와 연동된 컴포넌트를 **컨테이너**라고 한다

<br>

## store/modules
---
- module : redux에서 사용되는 Action과 Reducer를 기능별로 분류해서 작성한 것
- 보통은 Action과 Reducer를 구분해서 사용
- 합쳐서 사용하는 기법을 duck 기법이라고 부름

<br>

## store/configure.js
---
- Redux Store 생성하는 함수를 분리해놓은 파일


<br>

## store/index.js
---
- Store 생성 후 내보내는 역할
- combineReducers 사용해서 rootReducer 만들기
- middele ware 설정
    - redux-thunk