# React Router를 활용한 라우팅 구축 가이드

안녕하세요, 여러분! 이 가이드는 React Router를 사용하기 방법을 연습하기 위한 가이드라인입니다. 여기서 제시하는 예제와 단계들은 React Router의 기본 개념과 사용법을 이해하는 데 도움을 주기 위한 것입니다. 실제 프로젝트에 적용할 때는 여러분의 프로젝트 요구사항, 구조, 그리고 복잡성에 맞게 코드를 조정하고 확장해야 합니다. 이 과정을 통해 여러분은 페이지 간 이동이 자연스러운 사용자 친화적인 애플리케이션을 만드는 기본 원리를 배우게 될 것입니다. 그럼 시작해 볼까요?

## 1단계: React Router 설치하기

먼저, 프로젝트에 React Router를 설치해야 합니다.

```bash
npm install react-router-dom
```

## 2단계: 기본 라우팅 설정하기

이제 메인 페이지와 장바구니 페이지를 연결해 보겠습니다.

#### 1. `src` 폴더에 `pages` 폴더를 만들고, 그 안에 `Home.js`와 `Cart.js` 파일을 생성합니다.

#### 2. `Home.js`:

```jsx
import React from 'react';
import { Link } from 'react-router-dom';

function Home() {
  return (
    <div>
      <h1>메인 페이지</h1>
      <Link to="/cart">장바구니로 이동</Link>
    </div>
  );
}

export default Home;
```

#### 3. `Cart.js`:

```jsx
import React from 'react';
import { Link } from 'react-router-dom';

function Cart() {
  return (
    <div>
      <h1>장바구니</h1>
      <Link to="/">메인 페이지로 돌아가기</Link>
    </div>
  );
}

export default Cart;
```

#### 4. `App.js`를 수정하여 라우팅을 설정합니다:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './pages/Home';
import Cart from './pages/Cart';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/cart" element={<Cart />} />
      </Routes>
    </Router>
  );
}

export default App;
```

이제 기본적인 라우팅이 설정되었습니다. 메인 페이지에서 '장바구니로 이동' 링크를 클릭하면 장바구니 페이지로 이동하고, 장바구니 페이지에서 '메인 페이지로 돌아가기' 링크를 클릭하면 메인 페이지로 돌아갈 수 있습니다.

## 3단계: 동적 라우팅 - 상품 상세 페이지

이제 상품 목록에서 특정 상품을 클릭했을 때 해당 상품의 상세 페이지로 이동하는 기능을 만들어 보겠습니다.

#### 1. `pages` 폴더에 `ProductDetail.js` 파일을 생성합니다:

```jsx
import React from 'react';
import { useParams, Link } from 'react-router-dom';

function ProductDetail() {
  const { productId } = useParams();

  return (
    <div>
      <h1>상품 상세 정보</h1>
      <p>상품 ID: {productId}</p>
      <Link to="/">메인 페이지로 돌아가기</Link>
    </div>
  );
}

export default ProductDetail;
```

#### 2. `Home.js`를 수정하여 상품 목록과 링크를 추가합니다:

```jsx
import React from 'react';
import { Link } from 'react-router-dom';

function Home() {
  const products = [
    { id: 1, name: '상품 1' },
    { id: 2, name: '상품 2' },
    { id: 3, name: '상품 3' },
  ];

  return (
    <div>
      <h1>메인 페이지</h1>
      <Link to="/cart">장바구니로 이동</Link>
      <h2>상품 목록</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            <Link to={`/product/${product.id}`}>{product.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Home;
```

#### 3. `App.js`에 새로운 라우트를 추가합니다:

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import Home from './pages/Home';
import Cart from './pages/Cart';
import ProductDetail from './pages/ProductDetail';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/cart" element={<Cart />} />
        <Route path="/product/:productId" element={<ProductDetail />} />
      </Routes>
    </Router>
  );
}

export default App;
```

이제 동적 라우팅이 설정되었습니다. 메인 페이지의 상품 목록에서 상품을 클릭하면 해당 상품의 상세 페이지로 이동하게 됩니다.

## 마무리

축하합니다! 여러분은 이제 React Router를 사용하여 기본적인 라우팅과 동적 라우팅을 구현할 수 있게 되었습니다. 이 기술을 활용하면 사용자가 웹 애플리케이션을 더욱 편리하게 탐색할 수 있게 됩니다.

하지만 여기서 멈추지 마세요. React Router의 진정한 힘은 더 복잡한 시나리오에서 발휘됩니다. 다음 단계로 나아가기 위해, 몇 가지 추가 연습을 제안합니다.

1. 사용자가 존재하지 않는 페이지에 접근했을 때 표시할 404 Not Found 페이지를 추가해보세요. 이는 오류 처리의 중요한 부분입니다.
2. 중첩 라우팅을 사용해보세요. 예를 들어, 상품 카테고리 페이지 내에서 세부 카테고리로 이동하는 구조를 만들어볼 수 있습니다.

이러한 추가 기능들을 연습하면서 React Router의 더 깊은 이해를 얻을 수 있을 것입니다. 각 기능을 구현할 때마다 공식 문서를 참조하고, 다양한 시나리오를 실험해보세요.
