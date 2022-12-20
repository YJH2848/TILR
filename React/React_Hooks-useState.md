# useRef - 2022/11/24 (까먹고 이제올림)

- ## [useState란?](#useState란?)<br>
- ## [useState 사용법](useState의-사용법)
- ## [useState 사용예제](useState의-사용예제)

## useState란?

## useState 사용법

```js
import { useState } from "react"
...
const [state, setState] = useState(/* state의 초기 값 */)

...

```

여기서 state는 초기값이며 setState는 변한 값을 다시 state에 넣어주는
역할을 해준다. 이해를 쉽게 하기 위해 사용 예제를 만들어보자면
가장 대표적인 예제는 count이다

## useState 사용예제

```js
import { useState } from "react";

export default function App() {
  const [count, setCount] = useState(0);
  const onClick = () => {
    setCount(count + 1);
  };
  return (
    <div>
      <button onClick={onClick}>plus</button>
      Number : {count}
    </div>
  );
}
```

보면 onClick으로 버튼을 클릭했을 때 setCount에 count + 1의 값을 넣어주고 다시 count에 그 값을 넣어준다. 그러면 return 안에 {count}가
증가하는 것을 볼 수 있다.
