# 1. React & TypeScript 개괄

1. 많은 분들의 고민들

내가 짠 코드가 잘 짠 코드인가? 에 대한 고민들 ..

피드백 받을 수 있는 환경이 부족하다는 측면들 ..

코드 품질 / 아키텍처 / 적정기술

2. 그래서 전달하고 싶은 것? (강의 목표)

도구: 과거와 달리 많은 도구들이 있음. 바닥부터 개발 X

요즘에는 어떤 도구가 좋을까? 요즘은 거의 70~80%가 도구 이야기 같음

- 언어는 TypeScript
- UI Framework: React

상태 관리자, 비동기, 테스팅, 

3. 목표

**상태**를 어떻게 다룰 것인가?

웹은 특히나 실행**환경**이 다양함 / 개발하는 환경까지도

실제 서비스로 나가는 **제품**. 

각 도구들은 **목표**가 있음. 우리가 만들 제품도 목표가 있음 / 그 도구의 목표를 이해해야 잘 쓰는 것임 1) 만든사람이 P→S 한 부분 Best Practice, 2) 또 다른 사용법을 발견할 수도

**코드** ~ 퀄리티.

**상대적**

---

- 학습 방향

    다루는 양은 굉장히 광범위

    작년엔 React, Redux, TypeScript 위주로 했었음.

    기본적인 것들은 다루고 디테일은 초점만

    나머지는 알아서 키워드 가지고 학습하기

    강의 들을 때는 충분히 들어보고, 나중에 참고 할 수 있도록. (코드 따라하다가 흐름 놓치지 않기)

---

- 사이트

    1) Playgroud [https://www.typescriptlang.org/play](https://www.typescriptlang.org/play) TS를 JS로 Translate

    2) CodeSandbox [https://codesandbox.io/index2](https://codesandbox.io/index2) 예제 만들때 사용 / 작년 예제 링크 공유 예정

    3) React [https://reactjs.org/](https://reactjs.org/)

    4) Redux [https://redux.js.org/](https://redux.js.org/)

    5) Mobx [https://mobx.js.org/README.html](https://mobx.js.org/README.html)

    6) Redux-saga [https://redux-saga.js.org/](https://redux-saga.js.org/)

    7) Blueprint [https://blueprintjs.com/](https://blueprintjs.com/) UI, TS로 만들어져 있음. 컴포넌트를 어떻게 올바르게 만들지? 라는 측면에서 볼 것임   

    8) Testing Library [https://testing-library.com/](https://testing-library.com/)

어떤 관점에서 이런 라이브러리와 프레임워크를 바라보고 있는지 개괄적으로 볼 것임

![1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled.png](1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled.png)

유의미한 질문들

---

## 1. TypeScript

### 1) **Type Checking**

```tsx
let foo = 10; // foo는 number형 (암묵적)

let foo: number = 10; // (명시적)
```

Type 명시하지 않아도 알아서 인식한다.

**(명시적)**인 것이 더 좋다? : 요즘은 코드가 길어져도 이해하기 쉬운 코드를 선호한다.

[공식 Docs의 Basic Types](https://www.typescriptlang.org/docs/handbook/basic-types.html)

### 2) **Type Alias**

Primitive Type 장점: 재활용성(나이, 몸무게 등 포괄해서 number 하나로 쓸 수 있다는 의미) 

근데 의미 부여해서 쓰고 싶다? → 가독성 높이기

```tsx
type Age = number; // Type Alias

let age: Age = 10;
```

- **Compile Time** / Runtime Time

    [*Compile Time]* Generic, **Alias** 등 | **TypeScript**는 Compile시에 에러 체킹 多

    [*Runtime]*  Compile Time 이후

- **객체(Object)**에 **Type Alias** 적용

    ```tsx
    type Foo = {
    	age: number;
    	name: string;
    }

    const foo: Foo = {
    	age: 10, 
    	name: 'kim'
    }
    ```

     

### 3) I**nterface**

```tsx
type Foo = { // Type Alias
	age: number;
	name: string;
}

interface Bar = { // interface
	age: number;
	name: string;
}

// ------------------------------------------------

const foo: Foo = { // Obejct: type alias
	age: 10, 
	name: 'kim',
}

const bar: Bar = { // Object: interface
	age: 10, 
	name: 'kim',
}
```

- 캡쳐본

    ![1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%201.png](1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%201.png)

**type alias**, **interface** 비슷해보이는데, 무슨 차이?

→ 앞으로 차근차근, 어떤 경우에 각각을 쓰는게 유용한지 이야기 해볼 것임

- TS는 JS의 상위개념

    타입스크립트는 자바스크립트로 컴파일되는, 자바스크립트의 타입이 있는 상위집합입니다. TypeScript is a typed **superset** of JavaScript that compiles to plain JavaScript.

    TypeScript는 JavaScript와 엄청난 차이는 없음. 그래서 오해들이 있긴한데 ㅋㅋ

---

## 2. React

React **기본 프로젝트 만들기** (Node.js 설치되어 있음을 전제)

 **[create-react-app(CRA)](https://create-react-app.dev/docs/adding-typescript/)**: react 구조를 가장 빠르게 만드는 방법

- 그런데,

    **CRA**는 실제 Product 용으로는 잘 안쓴다고 한다. (뭐라고 설명하셨는데..)

`yarn create react-app (폴더명) —template typescript` → yarn (Package Manager 중 하나)

- 부가설명

    react scripts

    Configuration 너무 多 했었는데 → Zero Configuration

- Window에서는 ..

    나는 저대로 따라했는데 안됐다. 그래서 npx를 이용함

![1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%202.png](1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%202.png)

React - TypeScript 기본 구조

**tsconfig.json** (typescript 설정파일)

```json
{
  "compilerOptions": {
    "target": "es5",
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "allowJs": true,
    "skipLibCheck": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "forceConsistentCasingInFileNames": true,
    "module": "esnext",
    "moduleResolution": "node",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react"
  },
  "include": [
    "src"
  ]
}
```

**src/index.tsx**

```tsx
import React from 'react';
import ReactDOM from 'react-dom';

function App() {
  return (
    <h1>Tech Hello?</h1>
  );
}

ReactDOM.render(
  <React.StrictMode>
    <App /> 
  </React.StrictMode>,
  document.getElementById('root')
);
```

jsx to js transpiler: **BABEL**(The compiler for next generation JavaScript.

![1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%203.png](1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%203.png)

![1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%204.png](1%20React%20&%20TypeScript%20%E1%84%80%E1%85%A2%E1%84%80%E1%85%AA%E1%86%AF%209f48c3ea9be84858800076a88405e981/Untitled%204.png)

**src/index.tsx**

```tsx
import React from 'react';
import ReactDOM from 'react-dom';

interface AppProps { // interface 추가
  title: string;
  color: string;
}

function App(props: AppProps) { // inferface ~
  return (
  <h1 color="{props.color}">{props.title}</h1>
  )
}

// 아직은 정적 상태임
ReactDOM.render(
  <React.StrictMode>
    <App title ="Hello?" color="red"/>
  </React.StrictMode>,
  document.getElementById('root')
);
```

상태: 시간 흐름에 따라 값이 변하는 형태.

현재는 상태가 없지. 불변

→ 상태 쓸 때는 좀 더 복잡하겠지

---

### 3. 상태관리

- [flux 아키텍처](https://haruair.github.io/flux/docs/overview.html): 전통적인 MVC와 다름

- **Redux:** flux 아키텍처를 정형화함.

    react - 상태관리: 짝을 이뤄서 다님

    너무 간단하다. 그래서 오히려 어려워 하기도? → 포인트를 살펴볼 것임

- **MobX**: 상태 관리 패러다임을 완전히 바꾼 것임. Redux와 좀 다른 것임 / MST(Mobx State Tree)

---