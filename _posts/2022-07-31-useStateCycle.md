---
layout: post
title: "useState 실행 순서"
categories:
  - React
---

```jsx

function MyTrashcan() {
  const [loading, setLoading] = useState(false);
  const [trashList, setTrashList] = useState([]);

  const onLoadTrashList = async () => {
    try {
      // 요청이 시작 할 때에는 error 와 users 를 초기화하고
      //   setError(null);
      //   setUsers(null);
      // loading 상태를 true 로 바꿉니다.
      setLoading(true);
      const response = await axios.get(
        "http://localhost:8080/trash/mypage/users/173dc2de-7076-40cf-a211-f3eca7aa9b4d/images"
      );
      setTrashList(response.data);
      console.log(response.data);
      console.log(trashList);
    } catch (e) {
      console.log("An error occured : ", e);
    }
    setLoading(false);
  };

  useEffect(() => {
    onLoadTrashList();
  }, []);
```

이렇게 했을 때 위에 console.log(trashlist)에서 안뜬다 근데 밑에서 async를 실행한 후에는 정상적으로 콘솔로그 작동 왜 ?

> > > useState의 흐름을 알아야한다. 그리고 useEffect도

usestate의 set함수는 발생한 즉시 리렌더링을 일으키는데 그래서 그 후에 state의 저장이 되는 방식이여서

useEffect가 끝나고 나서야 할당됨

그 후 콘솔에 찍힌다.
