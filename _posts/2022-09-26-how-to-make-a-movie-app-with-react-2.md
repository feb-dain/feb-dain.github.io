---
title:  "리액트로 영화 앱 만들기(2)"
layout: post
tags: React
---

<a href="https://feb-dain.github.io/how-to-make-a-movie-app-with-react-1/">이어서...</a>
<p>🤗 Component를 나눠서 사용하는 법과 리액트를 이용해 새로고침 없이 페이지 전환하는 방법을 배웠다.</p>











```
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
```
return 이후가 페이지에 보여지는 코드인데, 보다시피 너무 복잡하다.
코드를 더 간결하게 작성할 수 있다면 당연히 그렇게 하는 게 좋다.
그렇다면 어떻게 더 간결하게 만들 수 있을까?<br>
🤓 리액트의 장점을 활용하자! **바로 여러 Component를 만들어 사용하면 된다.**
<br>
<br>

### React Router 사용하기

여러 Component를 만들어 페이지 이동을 할 수 있게 만들려면 `React Router`가 필요하다.<br>
```
npm i react-router-dom
```

<br>
리액트 라우터를 설치하고 "react-router-dom"에서 BrowserRouter, Routes, Route를 불러오면 끝!

```
import { BrowserRouter, Routes, Route } from "react-router-dom";

import Home from "./routes/Home";
import Detail from "./routes/Detail";

function MovieApp(){
    return ( 
        <BrowserRouter>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/movie" element={<Detail />} />
            </Routes>
        </BrowserRouter>
    );
}

export default MovieApp;
```

이제 각 컴포넌트에 원하는 코드를 작성해주면 된다.

Home.js 
```
import Movie from "../components/Movie";    // 경로 주의!
import { useEffect, useState } from "react";

function Home(){
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

    return <div>{loading ? (
        <h1>Loading...</h1>) : (
            <div>
                {movies.map((movie) => (
                    <Movie     // Movie 컴포넌트
                        // key는 react.js에서만, map 안에서 컴포넌트들을 render할 때 사용하는 것
                        key={movie.id}
                        coverImg = {movie.medium_cover_image}
                        title = {movie.title}
                        summary = {movie.summary}
                        year = {movie.year}
                        genres = {movie.genres}
                    /> 
                ))}
            </div>
        )}
    </div>;
}

export default Home;
```

<br>
Detail.js

```
function Detail(){
    return <h1>Detail</h1>;
}
export default Detail;
```

<br>
Movie.js

```
import PropTypes from "prop-types";
import {Link} from "react-router-dom"


// 아래 props(properties)는 부모 컴포넌트로부터 정보를 받아온다!
function Movie({ coverImg, title, year, summary, genres }){
    return (
        <div>
            {/* 모든 이미지는 대체 텍스트(alt)가 필요 */}
            <img src={coverImg} alt={title}></img>
            <h2>
                <Link to="/movie">{title} ({year})</Link>
            </h2>
            <p>{summary}</p>
            <ul>
                {genres == null ? "" : 
                    genres.map((g) => (
                        <li key={g}>{g}</li>))
                }
            </ul>
        </div>
    );
}

// 어떤 props 가지고 있는지 알기 위함
Movie.propTypes = {
    coverImg: PropTypes.string.isRequired,
    title: PropTypes.string.isRequired,
    year: PropTypes.number.isRequired,
    summary: PropTypes.string.isRequired,
    genres: PropTypes.arrayOf(PropTypes.string).isRequired,
};

export default Movie;
```

<br>
HTML과 마찬가지로 "a" 태그를 사용해 페이지 이동할 수는 있지만 재실행되는 단점이 있다.
재실행을 막기 위해서는 react router의 link를 이용하면 되는데,
link는 브라우저 새로고침 없이도 유저를 다른 페이지로 이동시켜주는 컴포넌트이다.
원하는 곳 어디에든 사용할 수 있다.

```
import {Link} from "react-router-dom"

<Link to="/movie"></Link>
```

<br>
새로운 페이지를 추가하고 싶으면 (Movie)App.js에 이렇게 route만 추가해주면 된다!

```
<Route path="/hello" element={<h1>Hello</h1>} />
```

아주 간편하다..!
<br>
<br>

### 다이나믹 url 얻기

1) 경로에 ":id"  추가

```
<Route path="/movie/:id" element={<Detail />} />
```

2) Home.js에서 id를 가져온 다음 

```
{movies.map((movie) => (
  <Movie 
      key={movie.id}
      id={movie.id}    // 여기 id 추가
```

3) 자식 컴포넌트(Movie.js)에서 부모 컴포넌트(Home.js)의 id값을 가져오면 된다.

```
function Movie({ id, coverImg, title, year, summary, genres })

<h2>
	<Link to={`/movie/${id}`}>{title} ({year})</Link>
</h2>
    
Movie.propTypes = {
    id: PropTypes.number.isRequired,
```

<br>

### url에서 id 값 알아내는 방법
React Router의 `useParams` 사용하면 된다!

```
import {useParams} from "react-router-dom"

const {id} = useParams();
console.log(id);
```

```
import {useParams} from "react-router-dom"


function Detail(){
    const {id} = useParams();
    const getMovie = async() => {
        const json = await (await fetch(
            `https://yts.mx/api/v2/movie_details.json?movie_id=${id}`)
        ).json();
        console.log(json);
    }
    useEffect(()=> {
        getMovie();
    },[]);
    return <h1>Detail</h1>;
}
export default Detail;
```

+summary가 너무 짧거나 너무 긴 경우 발생, 규칙성있게 만들어 주고 싶다면?<br>
→ **Slice 메서드를 이용**해 235 글자 이하로 설정하자! summary는 string이기 때문에 메서드 slice 사용 가능.

```
<p>{summary.length > 235 ? `${summary.slice(0, 235)}...` : summary}</p>
```

참고하기 (메서드)<br>
<a href="https://feb-dain.github.io/basic-javascript-04/">베이직 자바스크립트 4탄</a>

+추가 상식<br>
**Breaking Change란?** <br>
버전을 업데이트 하면서 코드가 깨졌으니 예전 방식을 지우고 새로운 방식으로 코드를 작성해야 한다는 뜻이다.
<br>
<br>

여기까지가 <a href="https://nomadcoders.co/react-for-beginners/lectures/3257">노마드 코더의 React 강의</a> 끝이다.<br>
  
---

<br>
<br>
❗ 완강 후, 혼자서 Detail 컴포넌트를 만들려고 하는데 문제가 발생했다. 위와 같은 방식으로, state.map으로
정보를 가져왔는데 계속 <span style="color:red">.map is not a function</span>이라는 오류가 발생했다.
문제를 알아내기 위해 콘솔에 state를 가져왔고, 콘솔에는 state가 { id: ... } 이런 식으로 나왔다.
혹시나 해서 state.id를 콘솔에 가져와보니 id값이 그대로 나왔다. **map을 사용할 필요가 없었던 것이다.** 😂
map을 사용하지 않고 그대로 JSX식으로 입력하니 오류 없이 성공!

```
import { useParams } from "react-router-dom"
import { useEffect, useState } from "react";


function Detail(){
    const [loading, setLoading] = useState(true);
    const [details, setDetail] = useState([]);
    const {id} = useParams();
    const getMovie = async() => {
        const json = await (await fetch(
            `https://yts.mx/api/v2/movie_details.json?movie_id=${id}`)
        ).json();
        setDetail(json.data.movie);
        setLoading(false);
    };
    useEffect(()=> {
        getMovie()
    },[]);
    return <div> 
        { loading ? (<h1>Loading...</h1>) : (
            <div>
                <img src={details.large_cover_image}></img>
                <h1>{details.title} ({details.year})</h1>
                <h2>Runtime: {details.runtime}분 &nbsp;&nbsp;&nbsp;&nbsp;⭐{details.rating}점</h2>
                <p>{details.description_full}</p>
            </div>
        )}
    </div>;
}
export default Detail;
```

❗ JSX식은 무조건 부모 하나가 필요하다.

<br>
<br>
💪 이제 나 혼자 리액트로 영화 앱을 만들어봐야겠다. 페이지(Route)를 수정/추가하고 CSS로 깔끔하게 디자인해야지!
