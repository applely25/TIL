# 리액트 Context

# 이게 뭐지..?

props를 사용하지 않고 데이터를 넘겨주며 사용할 수 있게 함

❗ 컴포넌트들이 데이터를 쉽게 공유할 수 있도록 함

# 언제 사용?

**********모든 컴포넌트에서 사용할 수 있는 데이터를 전달할 때 유용**********

ex) 테마 데이터(다크, 라이트 모드)

ex) 사용자 데이터(현재 인증된 사용자)

ex) 로케일 데이터(언어 혹은 지역)

데이터는 자주 업데이트할 필요가 없는 리액트 contect에 위치해야 함

❗ 컴포넌트를 위한 전역변수와 같다고 생각

# 해결해주는 문제

******************************************************props drilling을 막는데 도움을 줌******************************************************

→ props drilling : 중첩된 여러 계층의 컴포넌트에게 props를 전달해 주는 것, 해당 props를 사용하지 않는 컴포넌트에게도 전달

```jsx
export default function App({ theme }) {
  return (
    <>
      <Header theme={theme} />
      <Main theme={theme} />
      <Sidebar theme={theme} />
      <Footer theme={theme} />
    </>
  );
}
function Header({ theme }) {
  return (
    <>
      <User theme={theme} />
      <Login theme={theme} />
      <Menu theme={theme} />
    </>
  );
}
```

Header은 theme를 내려주기만 할 뿐 직접 필요가 없다.

# 리액트 context 사용법

리액트 버전 16부터 가능한 내장 API

1. `createContext` 메서드를 사용해 context 생성
2. 생성된 context응 가지고 context provider로 컴포넌트 트리 감싸기
3. `value` prop을 사용해 context provider에 원하는 값을 입력
4. context consumer를 통해 필요한 컴포넌트에서 그 값을 불러옴
    
    ```jsx
    export const UserContext = React.createContext();
    export default function App() {
      return (
        <UserContext.Provider value="Reed">
          <User />
        </UserContext.Provider>
      )
    }
    function User() {
      return (
        <UserContext.Consumer>
          {value => <h1>{value}</h1>} 
          {/* prints: Reed */}
        </UserContext.Consumer>
      )
    }
    ```
    
    1. `React.createContext()` 를 이용하여 `UserContext` 변수 만들기
        
        (`value` prop에 초깃값을 정해줄 수 있음)
        
    2. `UserContext.Provider` 을 사용하기
        
        값을 내려줘야하는 컴포넌트를 Provider로 감싸준다.
        
        전달해주고 싶은 값을 넣기 (여기서는 value prop을 사용함)
        
    3. context가 제공하는 값을 사용하고 싶으면 `UserContext.Consumer`로 감싸기
        
        전달된 값을 사용하기 위해서는 **reander props 패턴**을 사용해야 함(consumer 컴포넌트가 prop처럼 전달하는 함수)
        

# useContext 훅?

context를 사용하기위해 render props패턴을 사용하는 것이 조금 이상해 보임…

❗ ********************************************useContext 훅********************************************을 사용하여 context 사용 가능

`React.useContext` 를 이용하여 전체 context 객체를 내려줄 수 있음

```jsx
import React from 'react';
export const UserContext = React.createContext();
export default function App() {
  return (
    <UserContext.Provider value="Reed">
      <User />
    </UserContext.Provider>
  )
}
function User() {
  const value = React.useContext(UserContext);
  return <h1>{value}</h1>;
}
```

# context가 필요 없을 때

❗ 바로 context를 사용하지 않기! prop drilling을 피하기 위해 컴포넌트를 설계할 수 있는지 먼저 살펴보기!

# 사용시 주의사항

context가 내려주는 값을 업데이트하는 것은 **********************************************************************성능상의 문제로 권장 안함**********************************************************************

→ 리렌더링을 초래한다는 문제가 발생한다

만약 context providder에 객체를 내려주고 그 객체의 프로퍼티가 없데이트가 된다면 → context를 사용하는 모든 컴포넌트가 리렌더링 될 것

❗ state 변경이 자주 일어나지 않는 데이터에서 사용