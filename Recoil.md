# Recoil

상태: In progress

# React의 한계

컴포넌트의 상태는 공통된 상위 요소까지 끌어올려야만 공유 가능

→ 거대한 트리가 다시 렌더링됨

# Recoil이란

❗ React를 위한 전역 상태관리 라이브러리

# RecoilRoot

recoil state를 가지는 컴포넌트들이 필요로 하는, **atom context**를 가지는 **root**

Root이하의 컴포넌트는 모두 같은 전역 상태 값을 가진다는 뜻

```jsx
import {RecoilRoot} from 'recoil';

function App() {
  return (
    <RecoilRoot>
      <컴포넌트/>
    </RecoilRoot>
  );
}

export default App;
```

**RecoilRoot**로 감싸주지 않으면 에러 발생

# Atoms

recoil에서 상태를 정의하는 방법

컴포넌트끼리 공유 가능한 가장 작은 단위의 state

```jsx
import { atom } from "recoil";
const todoListState = atom({
	key: 'todoListState',
	default: [],
})
```

상태를 정의할 때는 고유값인 key를 설정하고, 기본값(default)을 설정

→ useRecoilValue, useSetRecoilState, useRecoilState의 훅을 사용 가능

arom 상태가 변경되면 atom으로 만든 상태를 읽는 모든 컴포넌트는 리렌더링 됨

```jsx
// 1
const [todoList, setTodoList] = useRecoilState(todoListState);
// 2
const todoList = useRecoilValue(todoListState);
// 3
const setTodoList = useSetRecoilState(todoListState);
```

1. useRecoilState()
    
    useState()와 동일 [ `원소의 상태` , `원소 상태 업데이트하는 함수` ]
    
2. useRecoilValue()
    
    상태 값만 필요한 경우 사용
    
3. useSetRecoilState()
    
    상태를 업데이트하는 함수만 필요한 경우
    

➕ setTodoList(todo) 업데이트

➕ setTodoList(prev ⇒ [todo, …prev]) 현재 값을 파라미터로 받아서 구현도 가능

# Selector

****************************************************************************************atom에서는 불가능한 비동기 처리****************************************************************************************와 같은 **********************************복잡한 로직**********************************을 구현 가능

atom에서 값을 복제해서 복제된 값을 파싱해서 사용하는 느낌

ex) 필터링된 todo : 전체 todo리스트에서 일부 기준에 따라 필처링 된 새 리스트가 생성되어 파생됨

ex) todo 리스트 통계 : 전체 todo에서 목록의 촌 항문 수, 완료된 항목 수 같은 리스크의 유용한 속성들을 계산하여 파생됨

```jsx
import { atom } from "recoil";

export default atom({
    key: 'countState',
    default: 0,
});
```

```jsx
import { DefaultValue, selector } from "recoil";
import countState from "../atom/countState";

export default selector({
    key: "countSelector",
    get: ({get}): number => {
				// countState를 구독하고 있습니다.
        // countState가 바뀔 때마다 1증가 시켜서 반환합니다.
        const count = get(countState);
        return count + 1;
    },
    set: ({set, get}, newCount)=>{
        return set(countState, newCount + 10)
    }
})
```

## key

atom의 key와  동일

프로젝트 전체에서 고유한 문자열을 가져야 함

## get

******************************************파생된 상태를 반환******************************************하는 곳

countState가 바뀔 때마다 새로운 값을 리턴해줌

`get()`을 여러번 사용 가능 → 하나라도 변하게 되면 리렌더링 됨

## set

**********set을 제공하면 쓰기 가능한 상태를 반환 함**********

selector의 값을 수정하는 것이 아닌 수정 가능한 atom의 값을 바꿔줌

`set()`은 두가지 매개 변수를 받음

set( Recoil의 상태, 바뀔 값=새로운 값 )