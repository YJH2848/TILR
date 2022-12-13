# useState 한 박자 느리게 반응(깨달음) - 2022/12/13

kakao map api를 이용해서 json에 있는 title을 검색하는 검색기능을 구현하고 있었다.

```js
const [lat, setLat] = useState(35.224508);
const [lng, setLng] = useState(129.092587);
```

현재 state에는 웹페이지가 랜더링 했을 때 제일 먼저 뜨는 map 좌표를 넣어두고

```js
const onClick = () => {
  markerdata.markerdata.map(el => {
    if (search == el.title) {
      if (el.id == 1) {
        setLat(el.lat);
        setLng(el.lng);
      }
    } else if (search == "") {
      setNone("보고싶은 지역을 입력해주십시요.");
    }
    setSearch("");
  });
};
```

버튼을 클릭했을 때 setLat와 setLng에 json에 있는 좌표값을 넣고

```js
position: new kakao.maps.LatLng(el.lat, el.lng),
```

position에 el.lat, el.lng을 넣어주었다.
map띄우는 코드를 useEffect로 묶었는데

```js
  useEffect(() => {
    const container = document.getElementById("map");
    const options = {
      center: new kakao.maps.LatLng(lat, lng),
      mapTypeId: kakao.maps.MapTypeId.ROADMAP,
      level: 3,
    };
    ...
    (중략)
    ...
    const zoomControl = new kakao.maps.ZoomControl();
    map.addControl(zoomControl, kakao.maps.ControlPosition.RIGHT);
  }, []);
```

이런식으로 작성이 되어있는데 그냥 이런식으로 하게 되니까 맵 좌표가 한박자 늦게 올라가게되었다 그래서 나는 구글링을 해보았는데

```js
useEffect(() => {
    ...
},[lat, lng])
```

여기다가 lat와 lng를 넣으면 된다고 한다.
