# 몽고DB와 NodeJs 연결 2022/12/22

나는 백엔드는 Node를 쓸거고 db는 MongoDB를 쓸것이기에
가장 먼저 헤야될 NodeJs와 MongoDB연결하는 방법을 수색하였다
그런데 보니까 생각보다 쉬웠는데
가장 먼저
<b>MongoDB</b>사이트에 들어가서 Create Database를 만들어주고 <b>Connect</b>를 눌러 <b>Connect your application</b>을 눌러서

`Add your connection string into your application code`
에 있는 코드를 복사를 해준다.

```js
const mongoose = require("mongoose");
mongoose
  .connect(
    "mongodb+srv://yunjonghyuck:dbswhdgur2843@nodejstest.9oytatc.mongodb.net/?retryWrites=true&w=majority",
    {
      useNewUrlParser: true,
      useUnifiedTopology: true,
      //   useCreateIndex: true,
      //   useFindAndModify: false,
    }
  )
  .then(() => console.log("MongoDB Connected..."))
  .catch(err => console.log(err));
```
