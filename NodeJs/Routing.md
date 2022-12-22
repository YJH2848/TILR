# 라우팅 및 Mvc패턴 적용 - 2022/12/21

## 라우팅

<br>
저번에 express로 서버를 가동시켜 res.send로 텍스트 띄우기를 해봤는데
이번에는 res.send로 텍스트를 띄우는 것이 아닌 따로 html파일을 만들어서 그 html 파일과 라우팅을 해볼 것이다.

```
NodeJs
----views
    ----home
        index.ejs
----app.js
```

이런 형태로 파일을 만들어 주고

```js
app.set("views", "./views");
app.set("view engine", "ejs");
```

app.set을 이용하여 앱 세팅을 해준다 여기서 view engine은 ejs로 해줄건데 ejs는 html과 거의 똑같다고 보면된다.
라우팅 하기 전 app.js파일에다 하는것이 아닌

```
NodeJs
----routes
    ----home
        index.js

----views
    ----home
        index.ejs
----app.js
```

따로 라우팅 파일 분리 시켜 그안에 라우팅하는 코드를 넣어준다
저번엔 res.send를 썻다면 이제는 res.render을 이용하여
파일을 연결 시킬건데 render을 쓰기 위해선

```js
const app = express();
```

가 아닌

```js
const render = express.Router();
```

로 해주면 된다.

```js
router.get("/", (req, res) => {
  res.render("home/index");
});
```

이렇게 해주면 된다<br>
res.render안에 ./views/home/index가 아닌 hone/index로 한 이유는 아까 앱 세팅을 할때 우리가 ./views를 미리 세팅해주었기에 저렇게 사용한것이다

<br>
저번 시간에 놓친게 있는데 app.listen에 포트를 직방으로 3000을 넣어주면 별로 좋지 못한 코드이기에 따로 port라는 변수에 3000을 넣어두고 불러준다

```js

const PORT = 3000;

...

app.listen(PORT, () => {
  console.log("서버 가동");
});

```
