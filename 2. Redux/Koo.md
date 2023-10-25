# Redux
- 자바스크립트 어플리케이션을 위한 예측가능한 상태 컨테이너
- 어플리케이션이 복잡해지면서 동일한 상태 공유가 필요한 경우 props를 계속 전달해야하는 문제가 발생하고 유지관리가 어려워짐에 따라 한 곳에서 상태를 저장하고 추적가능하도록함
- 상태가 예측 가능한 방식으로만 업데이트 가능하도록 규칙 존재
  - state는 읽기 전용이며 state를 변화시키는 유일한 방법은 action을 통해 가능해 쉬운 디버깅이 가능
  - state의 변화를 일으키는 [reducer는 순수 함수여야하며](https://redux.js.org/faq/reducers#reducers) 기존 state 값을 변경하는 것이 아니라 새로운 state를 만들어 반환
  - 하나의 어플리케이션은 하나의 Store(state 저장소) 만 존재함
- React Developer Tools를 통해 보다 여느 상태 관리 보다 디버깅이 용이함
- 상태관리를위해 많은 코드 작성이 선행되는 문제가 있어 최근에는 Redux Toolkit 같은 라이브러리가 권장되는 추세

## Store
- 앱의 전체 상태 트리를 가지고 있는 저장소
- dispatch 같은 일부 내장함수들을 가지고 있음
```js

const { createStore } = require('redux');

// 초기 상태를 정의
const initialState = {
  count: 0
}

// ...

// createStore 함수를 사용하여 스토어를 생성
const store = createStore(counterReducer);
```

## Reducer
리듀서는 현재의 상태와 액션을 입력 받아 일치하는 액션의 다음 상태를 반환하는 순수함수

```js
function myReducer(state = initialState, action) {
  switch (action.type) {
    case 'SOME_ACTION':
      // 새로운 상태를 반환
      return {
        ...state,
        // 상태 업데이트 로직
      };
    case 'ANOTHER_ACTION':
      // 다른 액션에 대한 상태 업데이트 로직
      return {
        ...state,
        // 상태 업데이트 내용
      };
    default:
      // 액션 타입이 맞지 않을 경우 현재 상태 그대로 반환
      return state;
  }
}
```


### Action과 dispatch
- action은 무엇이 일어날지 서술하는 객체
- dispatch는 action을 발생시키는 메소드
- 액션은 다음과 같은 구조를 가짐
  - type:  액션의 종류를 식별
  - payload: 액션의 실행에 필요한 데이터를 전달

```js
// dispatch 메소드에 액션 (type과 payload)를 전달하여 state를 갱신할 수 있다. 
store.dispatch({ type: 'INCREMENT', payload: 1 });
```

# Reference
- [Redux 공식문서](https://redux.js.org/)