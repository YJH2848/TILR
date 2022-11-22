# useEffect - 2022/11/22

## 사용이유

- 굳이 여러번 랜더링될 필요 없을 때
  (Ex : map api)

## 사용법

```js
import { useEffect } from "react"
...

  useEffect(() => {
    //실행할 내용
  });

...

```

가장 기본적인 형태이며

```js
import { useEffect } from "react"
...

  useEffect(() => {
    //실행할 내용
  }, [/* 실행시키고 싶은 함수*/]);

...
```

이런식으로 대괄호안에 내가 실행시키고 싶은 함수를 넣어 지정을 해줄 수 있다.

useEffect로 예제를 한개 만들어보면

```js
import { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);
  const rendering = () => {
    setCount(count + 1);
    console.log("버튼 클릭햇습니다!");
  };

  useEffect(() => {
    console.log("rendering");
  });

  return (
    <div>
      <button onClick={rendering}>update</button>
      count : {count}
    </div>
  );
}

export default App;
```

이런식으로 update버튼을 클릭할때마다 useState가 리랜더링되어서
useEffect가 리랜더링될때마다 console에 "rendering"을 띄우게 된다.<br>아까의 코드에서 조금만 더 추가해서 useEffect를 알아보면

```js
import { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);
  const [msg, setMsg] = useState("");
  const rendering = () => {
    setCount(count + 1);
    console.log("버튼 클릭햇습니다!");
  };
  const onChange = e => {
    setMsg(e.target.value);
  };
  useEffect(() => {
    console.log("rendering");
  }, [count]);

  return (
    <div>
      <input onChange={onChange} type="text" value={msg}></input>
      text : {msg}
      <br />
      <button onClick={rendering}>update</button>
      count : {count}
    </div>
  );
}

export default App;
```

onChange 라는 useState를 한개 더 만들어주고 useEffect -> []에 count함수를 넣어주면 update버튼을 눌렀을 때만 "rendering"이라는 문구가 뜨게된다.
