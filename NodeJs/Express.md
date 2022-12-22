# Express로 서버 띄워보기 - 2022/12/20

나는 프론트로 만족을 하지못하고 백엔드까지 공부를 하기 위해 오늘 2022/12/21부터 Node.js를 공부할것이다.
그래서 오늘은 가장 기본적인 express를 이용하여 서버를 가동시켜볼건데

```js
const express = require("express");
const app = express();

app.listen(3000, () => {
  console.log("서버 가동");
});
```

app.listen(3000)은 3000포트로 서버를 가동시킨다는 말이된다.
그래서 서버를 가동시켜봤으면 이제 한번 내용도 넣어보고 싶어서 봤더니

```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("여기는 서버 가동 후 페이지");
});

app.listen(3000, () => {
  console.log("서버 가동");
});
```

요런식으로 get을 이용하여 내용을 넣을 수 있었다.

찾아보니깐 express말고 좀 더 힘든 방법으로 서버를 가동시키는게 있었는데
그걸 보니 왜 express를 쓰는지 알거 같았다.

```js
const http = require("http");
const app = http.createServer((req, res) => {
  if (req.url == "/") {
    res.end("여기는 루트입니다.");
  } else if (req.url == "/login") {
    res.end("여기는 로그인 페이지입니다.");
  }
});

app.listen(3001, () => {
  console.log("http로 가동 된 서버입니다");
});
```

대강 이런식인데 express가 아니면 send를 못쓴다고 했고 res.url로 주소를 받아오는 식이라서 페이지가 많아지면 if문으로 도배가 되어 코드가 지저분해지는 것을 볼 수 있다.<br>
그리고 문제는 이 뿐만 아니라 이런식으로만 하면 또 한글도 깨져서 나오게 되는데

```js
res.writeHead(200, { "Content-type": "text/html; charset=utf-8" });
```

이 한줄을 추가를 해줘야 한글이 안꺠지게 된다.
express는 신이구나를 깨닫게 되었다.
