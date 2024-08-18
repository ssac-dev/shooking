# SW040701 전체 페이지 연결 가이드라인

이 가이드라인은 React Router를 사용한 전체 페이지 연결 과정에 대한 개념과 사용법을 이해하는 데 도움을 주기 위한 것입니다. 실제 프로젝트에 적용할 때는 여러분의 프로젝트 요구사항, 구조, 그리고 복잡성에 맞게 코드를 조정하고 확장해야 합니다.

## 1. 제품 상세 페이지 구현

### 피그마 디자인 확인

- 피그마에서 제공된 제품 상세 페이지 디자인을 꼼꼼히 살펴보세요.
- 레이아웃, 컴포넌트 구조, 사용된 이미지 등을 파악합니다.

### ProductDetailPage 컴포넌트 작성

```jsx
import React, { useState } from 'react';
import { useParams, Link } from 'react-router-dom';

function ProductDetailPage() {
  const { productId } = useParams();
  const [quantity, setQuantity] = useState(1);

// 실제 구현에서는 productId를 사용하여 상품 정보를 가져오는 로직이 필요합니다
  const product = {
    id: productId,
    name: "브랜드A",
    description: "편안하고 착용감이 좋은 신발",
    price: 35000,
    imageUrl: "/path-to-shoe-image.jpg"
  };

  const handleIncrement = () => setQuantity(prev => prev + 1);
  const handleDecrement = () => setQuantity(prev => Math.max(1, prev - 1));

  const handleAddToCart = () => {
    console.log(`${product.name} 상품 ${quantity}개 장바구니에 추가됨!`);
// 여기에 실제 장바구니 추가 로직 구현
  };

  return (
    <div className="product-detail">
      <header>
        <Link to="/">← </Link>
        <Link to="/cart">장바구니</Link>
      </header>
      <img src={product.imageUrl} alt={product.name} className="product-image"/>
      <h1>{product.name}</h1>
      <p>{product.description}</p>
      <p className="price">{product.price.toLocaleString()}원</p>
      <div className="quantity-selector">
        <button onClick={handleDecrement}>-</button>
        <span>{quantity.toString().padStart(2, '0')}</span>
        <button onClick={handleIncrement}>+</button>
      </div>
      <button className="add-to-cart" onClick={handleAddToCart}>장바구니 담기</button>
      <section className="related-products">
        <h2>관련 상품</h2>
        <div className="related-products-grid">
          {/* 여기에 관련 상품 이미지들을 넣습니다 */}
        </div>
      </section>
    </div>
  );
}

export default ProductDetailPage;
```

## 2. 라우팅 설정

App.js에서 라우팅을 설정합니다:

```jsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import ProductDetailPage from './pages/ProductDetailPage';
import CartPage from './pages/CartPage';
import OrderCompletePage from './pages/OrderCompletePage';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<ProductListPage />} />
        <Route path="/product/:productId" element={<ProductDetailPage />} />
        <Route path="/cart" element={<CartPage />} />
        <Route path="/order-complete" element={<OrderCompletePage />} />
      </Routes>
    </Router>
  );
}
```

## 3. 결제 완료 페이지 구현

```jsx
import React from 'react';
import { Link } from 'react-router-dom';

function OrderCompletePage() {
  return (
    <div className="order-complete">
      <h1>결제 완료!</h1>
      <p>총 3개의 상품을 구매하셨습니다.</p>
      <div className="total-amount">
        <h2>총 결제 금액</h2>
        <p className="amount">98,000원</p>
      </div>
      <Link to="/products">
        <button className="view-products">상품 목록 보기</button>
      </Link>
    </div>
  );
}

export default OrderCompletePage;
```

## 마무리

이 가이드라인을 통해 React Router를 사용하여 페이지 연결과 기능 구현을 연습하고, 실제 프로젝트에 적용해 보세요. 그리고 작업을 해나가는 과정에서 어려움이 있다면, 주저하지 말고 생성형 AI의 도움을 받아보세요. 여러분의 현재 코드를 분석하고 개선하는 과정에서 AI는 훌륭한 조력자가 될 수 있습니다.

**AI와 협업하여 코드 개선하기**

1. **문제 정의:** 먼저, 어떤 문제를 해결하고 싶은지 명확하게 정의하세요. 에러 메시지, 예상과 다른 동작, 성능 문제 등 구체적인 문제를 설명할수록 AI가 더 정확한 도움을 줄 수 있습니다.
2. **코드 제공:** 문제가 발생하는 코드 부분을 AI에게 제공하세요. 전체 코드를 제공할 필요는 없지만, 문제와 관련된 핵심 부분을 포함해야 합니다.
3. **질문 또는 요청:** AI에게 코드 분석을 요청하거나, 문제 해결을 위한 제안을 요청하세요. 예를 들어, "이 코드에서 왜 에러가 발생하는지 분석해주세요." 또는 "이 부분의 코드를 개선할 방법을 제안해주세요."와 같이 구체적으로 질문하세요.

AI를 활용하여 코드를 분석하고 개선하는 과정은 여러분의 문제 해결 능력과 코딩 실력을 향상시키는 데 큰 도움이 될 것입니다. 또한, AI와 협업하는 경험을 통해 미래 개발 환경에 대한 적응력을 키울 수 있습니다.
