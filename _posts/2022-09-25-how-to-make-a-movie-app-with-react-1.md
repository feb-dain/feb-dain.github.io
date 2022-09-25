---
title:  "리액트로 영화 앱 만들기(1)"
layout: post
tags: React
---

<p>🤗 리액트 기초를 복습하면서 map 메서드 사용과 api를 가져와서 필요한 정보를 사용하는 것에 좀 더 익숙해졌다. 그리고 then 대신  async-await를 사용하는 방법도 배웠다.</p>








```
const [movies, setMovies] = useState([]);
useEffect(()=> {
    fetch(`
        https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year`    // api 가져오기
    ).then((response) => response.json()
    ).then((json) => {
        setMovies(json.data.movies);
        setLoading(false);
    });
}, []);    // state가 변할 때마다 렌더링되지 않고, 딱 한 번만 실행
```
<br>
요즘에는 then 대신에 아래와 같이 async-await을 사용한다. Why? 코드가 간결해 가독성이 좋기 때문이다. 👇
<br>

```
const getMovies = async() => {
    const response = await fetch(
        `https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year`
    );
    const json = await response.json();
    setMovies(json.data.movies);
    setLoading(false);
};
useEffect(()=> {
    getMovies()
}, []);
```

<br>
더 짧게는 이런 식으로 코드를 작성할 수 있다.
<br>

```
const getMovies = async() => {
        const json = await (await fetch(
            `https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year`
        )).json();

        setMovies(json.data.movies);
        setLoading(false);
    };
    useEffect(()=> {
        getMovies()
    }, []);
```
한 번 자세히 비교해보자!<br>

1. getMovies 변수에 async 함수를 사용
2. json 변수를 만들어 await 연산자 사용<br>
2-1. 괄호를 열고 await연산자 또 사용 → fetch로 api(url) 호출 → json 데이터 호출 
3. getMovies 변수에 데이터 변경 함수 호출
4. useEffect에는 getMovies 변수만 하나 실행

<br>
그러면 이제 json 파일 리스트에 있는 것들을 어떻게 화면에 보이게 할까?<br>
**Map을 이용해 불러오면 된다!**
<br>
<br>

>Map? <br>
>기존 배열에 있는 각각의 item을 변형시키고, 변형된 item을 새로운 배열에 넣는다. ❗ 고유한 key를 꼭 써줘야 한다.
```
[1, 2, 3, 4, 5, 6].map(x => x*2)
[2, 4, 5, 6, 8, 10, 12]    // 결과
```

<br>

<details>
<summary>원하는 평점의 영화들만 보고 싶어!</summary>
<div markdown="3">

https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year
<br>
api 주소에서 `rating=9 → rating=8` 이렇게 평점을 바꾸면 된다!

</div>
</details>

<br>

```
function MovieApp(){
    const [loading, setLoading] = useState(true);
    const [movies, setMovies] = useState([]);
    const getMovies = async() => {
        const json = await (await fetch(
            `https://yts.mx/api/v2/list_movies.json?minimum_rating=9&sort_by=year`
        )
    ).json();
        setMovies(json.data.movies);
        setLoading(false);
    };
    useEffect(()=> {
        getMovies()
    }, []);
    console.log(movies);
    
    return <div>{loading ? <h1>Loading...</h1> :
        <div>
            {movies.map((movie) => (
                <div key={movie.id}>
                    <img src={movie.medium_cover_image}></img>
                    <h2>{movie.title} ({movie.year})</h2>
                    <p>{movie.summary}</p>
                    <ul>
                        {movie.genres == null ? "" : 
                            movie.genres.map((g) => (
                                <li key={g}>{g}</li>))
                        }
                    </ul>
                </div>))}
        </div>
    }</div>;
}
```

<br>

<img width="513" alt="image" src="https://user-images.githubusercontent.com/108778921/192147639-79af4e49-18bf-4940-af59-6c133e7693fd.png">

<br>
영화 api 불러오기 완료! 
<br>
<br>
