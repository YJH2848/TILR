# useRef - 2022/11/23

- ## [useRef란?](#useRef란?)<br>
- ## [useRef 기본형태](#useRef의-기본형태)
- ## [useRef 사용예제](useEffect의-사용예제)
- ## [useRef 이해돕기](#useRef의-이해돕기)
<hr>

## useRef란?

: useState는 값이 변화할때마다 랜더링이 되지만 값이 변해도 useRef는 랜더링이 발생이 되지않는다.

## useRef의 기본형태

```js
import { useRef } from "react";
...

const Ref = useRef(/*넣고 싶은 값 (ex : number | string*/)

...

```

형태는 보시다시피 useState보다 간편한 것을 볼수 있다.

## useRef의 사용예제

```js
import { useRef } from "react";

function App() {
  const plusNum = useRef(0);

  const countRef = () => {
    plusNum.current = plusNum.current + 1;
    console.log(plusNum.current);
  };
  return (
    <div>
      <button onClick={countRef}>Ref 올리기</button>
      <br />
      Ref : {plusNum.current}
    </div>
  );
}

export default App;
```

버튼을 클릭할때마다 +1씩 해주는데 여기서 plusNum이라는 변수명으로 useRef를 만들고 event처럼 current안에 plusNum의 값이 들어있어 plusNum.current라고 해주었다.

하지만 useRef는 아까 말햇듯이 리랜더링이 되지 않기 때문에 값이 실시간으로 업데이트가 되지않는다. 그래서 console에 찍어서 보면 console에 +1씩 잘 되는것을 볼 수 있다.

## useRef 이해돕기

```js
import { useRef, useState } from "react";

function App() {
  const [count, setCount] = useState(0);
  const plusNum = useRef(0);

  const render = () => {
    setCount(count + 1);
  };

  const countRef = () => {
    plusNum.current = plusNum.current + 1;
    console.log(plusNum.current);
  };
  return (
    <div>
      <button onClick={countRef}>Ref 올리기</button>
      <button onClick={render}>renderBtn</button>
      <br />
      Ref : {plusNum.current} | Render : {count}
    </div>
  );
}

export default App;
```

리랜더링 할 수 있도록 useState를 하나 넣어주었다.<br>
Ref버튼을 원하는 만큼 눌러주고 renderBtn버튼을 클릭을 해주면 Ref버튼을 누른 만큼 숫자가 웹페이지에 랜더링되어있다.
