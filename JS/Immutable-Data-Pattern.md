# Immutable Data Pattern
---
## 불변 데이터 패턴?
---
- **같은 주소를 참조하는 다른 객체에서 객체를 변경**하기 때문에 의도하지 않은 객체의 변경이 발생
- 문제의 해결 방법은 **객체를 Immutable(불변) 객체로 만들어서 변경을 방지하고, 변경이 필요한 경우에는 참조가 아닌 방어적 복사를 하는 것** 혹은 **Immutable.js 사용**

- 해결 방법
    - 객체의 방어적 복사(defensive copy)
        - Object.assign
    - 불변객체로 만들기
        - Object.freeze
    - Immutable.js 사용


<br>

## Object.assign
---
- 타겟 객체로 소스 객체의 값을 복사
- 이때, 소스 객체의 값과 동일한 값을 가진 타겟 객체의 값들은 소스 객체의 값들로 덮어쓰기가 된다
- 리턴 값으로는 타겟 객체를 반환
- ES6에 추가된 메소드
    ```js
    Object.assign(target, ...sources)
    ```
<br>

- 예제1
    ```js
    // Copy
    const obj = {a:1};
    const copy = Object.assign({}, obj);
    console.log(copy); //{a:1}
    console.log(obj == copy); // false
    ```

<br>

- 예제2
    ```js
    const o1 = { a: 1 };
    const o2 = { b: 2 };
    const o3 = { c: 3 };

    const merge1 = Object.assign(o1, o2, o3);

    console.log(merge1); // { a: 1, b: 2, c: 3 }
    console.log(o1);     // { a: 1, b: 2, c: 3 }, 타겟 객체가 변경

    const o4 = { a: 1 };
    const o5 = { b: 2 };
    const o6 = { c: 3 };

    const merge2 = Object.assign({}, o4, o5, o6);

    console.log(merge2); // { a: 1, b: 2, c: 3 }
    console.log(o4);     // { a: 1 }
    ```

<br>

- 예제3
    ```js
    const user1 = {
    name: 'Lee',
    address: {
        city: 'Seoul'
    }
    };

    // 새로운 빈 객체에 user1을 copy
    const user2 = Object.assign({}, user1);
    console.log(user1 === user2); // false

    user2.name = 'Kim';
    console.log(user1.name); // Lee
    console.log(user2.name); // Kim

    // 객체 내부의 객체(Nested Object)는 Shallow copy된다.
    console.log(user1.address === user2.address); // true

    user1.address.city = 'Busan';
    console.log(user1.address.city); // Busan
    console.log(user2.address.city); // Busan
    ```
- user1과 user2는 주소를 공유하지 않는다
- 주의할 것은 user1, user2의 객체가 const로 선언되어 재할당은 할 수 없지만
- **객체의 값이 변경될 수 있다는 것이다**

- Object.assign을 사용해서 기존 객체를 변경하지 않고 객체를 복사해서 사용할 수 있다
- 하지만, **완전한 deep copy를 지원하지 않는다**
- 객체 내부의 객체(Nested Object)는 Shallow Copy가 된다

<br>

- Nested Data의 복제
    - Nested Data가 Array인 경우
    - 복제해서 사용해야 원본 데이터를 유지할 수 있다(concat 함수)
    ```js
    const user1 = {
    name: 'Lee',
    score:[1,2]
    };

    const user2 = Object.assign({}, user1);

    user2.score = user1.score.concat();

    user2.score.push(3);
    console.log(user1.score); // [1,2]
    console.log(user2.score); // [1,2,3]
    ```


<br>

## Object.freeze
---
- **Immutable(불변) 객체로 만들 수 있다**

```js
const user1 = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

// Object.assign은 완전한 deep copy를 지원하지 않는다.
const user2 = Object.assign({}, user1, {name: 'Kim'});

console.log(user1.name); // Lee
console.log(user2.name); // Kim

Object.freeze(user1);

user1.name = 'Kim'; // 무시된다!

console.log(user1); // { name: 'Lee', address: { city: 'Seoul' } }

console.log(Object.isFrozen(user1)); // true
```

<br>

- 하지만 **객체 내부의 객체는 변경이 가능하다**

- 내부 객체까지 변경이 불가능하게 하려면 **Deep Freeze**를 해야 한다

```js
function deepFreeze(obj) {
  const props = Object.getOwnPropertyNames(obj);

  props.forEach((name) => {
    const prop = obj[name];
    if(typeof prop === 'object' && prop !== null) {
      deepFreeze(prop);
    }
  });
  return Object.freeze(obj);
}

const user = {
  name: 'Lee',
  address: {
    city: 'Seoul'
  }
};

deepFreeze(user);

user.name = 'Kim';           // 무시된다
user.address.city = 'Busan'; // 무시된다

console.log(user); // { name: 'Lee', address: { city: 'Seoul' } }
```
<br>

- 참고 : let vs const vs Object.freeze
    - let : 재선언 불가, 재할당은 가능
    - const : 재선언 & 재할당 불가, 값은 변경될 수 있다
    - Object.freeze : 값 자체를 바꿀 수가 없음
    - 예시
        ```js
        let o1 = {name : "Hello"};
        const o2 = o1;
        
        o1.name = "Hi";
        console.log(o2.name); // Hi
        
        const o3 = o1;

        Object.freeze(o3);

        o1.name = "Hello"; // 무시
        console.log(o1.name); // "Hi" 
        console.log(o3.name); // "Hi" 
        ```


<br>

## Immutable.js
---
- Object.assign과 Object.freeze를 사용하는 방법들은 **번거롭고 성능상 이슈가 있어, 큰 객체에는 사용하지 않는 것이 좋다**
- 대신 facebook이 제공하는 Immutable.js를 사용할 수 있다
- Immutable.js는 **List, Stack, Map, OrderedMap, Set, OrderedSet, Record와 같은 영구 불변 데이터 구조를 제공한다**

- 설치
```js
$ npm install immutable
```

- 예제
```js
const map1 = Map({ a: 1, b: 2, c: 3 })
const map2 = map1.set('b', 50)
map1.get('b') // 2
map2.get('b') // 50
```
- map1.set()을 해도 map1의 값은 불변
- map1.set()은 결과를 반영한 새로운 객체를 반환