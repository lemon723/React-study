# React 영화 웹서비스 만들기

---

**리액트를 처음 접해보고, 그날 떠오른 것을 Markdown 문법 연습도 겸해서 간단하게 정리해 보았습니다.**

### 1. JSX

---

- JSX(JavaScript XML)는 Javascript에 XML을 추가한 확장한 문법이다.

- Babel을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

### 2. useState

---

```javascript
const [value, setValue] = useState(0);
```

- `value`는 저장된 값. 즉 `useState(0)`에서 0의 값을 갖게 된다.

- `setValue`의 경우 `value`가 변경된 값을 저장할 수 있게 만들어 준다.

### 3. Props

---

- `props(property)`란 상위 컴포넌트에서 하위 컴포넌트로 값을 전달할 때 사용하는 속성이다.

- 상위 컴포넌트가 하위 컴포넌트에 값을 전달하기 때문에 단방향 데이터 흐름을 갖는다.

- 부모 컴포넌트는 수정 가능하지만, 자식 컴포넌트는 읽기만 가능하다.

##### prop-types

- `prop`의 타입을 명시해서 에러를 방지하는 역할을 한다.

```javascript
Btn.propTypes = {
  text: PropTypes.string,
  fontSize: PropTypes.number,
};
```

- _나중에 TypeScript로 대체 가능하지 않을까 생각해 보았다._

### 4. Create-React-App

---

- 초기 환경을 일일히 설정하지 않고, 리액트 프로젝트를 시작할 수 있도록 준비된 일종의 틀
- 터미널 창에서 `npm start`가 실행되지 않아서 좀 당황했지만, `cd` 몇번으로 쉽게 해결할 수 있었다.
- Create-React-App에서 터미널로 설치했을 때, 적용되지 않는 오류가 생겼다

### 5. useEffect(()=>{})

---

- state가 변할 때마다 리렌더링이 되는데, `useEffect`를 사용하면 이를 방지할 수 있다.

- 첫번째 인자는 제한 하고 싶은 내용. 두번째 인자인 `Deps`가 없을 경우 최초 1회 실행, 있을 경우 해당 값이 변할 경우 실행한다.

- `Deps`는 여러개 입력이 가능하다.

```javascript
console.log("Re-render");

useEffect(() => {
  console.log("CALL THE API");
}, []);

useEffect(() => {
  if (keyword !== "" && keyword.length > 5) {
    console.log("SEARCH FOR", keyword);
  }
}, [keyword]);
```

> 연습하면서 `console.log()`가 두번씩 찍혔는데, `<React.StrictMode>`가 `<App/>`을 감싸고 있어서 그랬다.
> 개발 단계의 오류를 잘 잡기 위해서 그렇다고 한다.
> https://velog.io/@hyes-y-tag/React-useEffect%EA%B0%80-%EB%91%90%EB%B2%88-%EC%8B%A4%ED%96%89%EB%90%9C%EB%8B%A4%EA%B3%A0
