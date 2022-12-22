# Props - 2022/12/21

- ### [Props란?](#Props란?)
- 
- ### [Props 사용예제](Props의-사용예제1)
- ### [Props 사용예제](Props의-사용예제2)

## Props란?

: 상위 컴포넌트에 있는 값을 하위 컴포넌트로 전달할 때 사용

## Props의 사용예제1

<br>

### 부모컴포넌트

```js
import Child from "./child";

export default function Parents() {
  const name = "윤종혁";
  return (
    <div>
      부모 컴포넌트
      <div>
        <Child name={name} />
      </div>
    </div>
  );
}
```

이런식으로 내가 넘기고싶은 변 수나 state를 자식 컴포넌트안에 넣어주면 자식 컴포넌트는 그 값을 읽어올 수 있다.
<br>

### 자식컴포넌트

```js
export default function Child(props) {
  return (
    <div>
      자식 컴포넌트
      <div>전달 값 : {props.name}</div>
    </div>
  );
}
```

전달한 값을 함수 괄호 안에 넣고 return 안에 props.name을 해주면 그 값이 잘 전달되는 것을 확인할 수 있다.
<br>
이를 가지고 다른 예시를 들어보자

## Props의 사용예제2

<br />

### 부모컴포넌트

```js
import { useState } from "react";
import Child from "./child";

export default function Parents() {
  const [count, setCount] = useState(0);
  const onClick = () => {
    setCount(count + 1);
  };
  return (
    <div>
      <button onClick={onClick}>count</button>

      <Child count={count} />
    </div>
  );
}
```

<br>

### 자식컴포넌트

```js
export default function Child({ count }) {
  return (
    <div>
      <div>cnt : {count}</div>
    </div>
  );
}
```

요런것도 할수 있다.
