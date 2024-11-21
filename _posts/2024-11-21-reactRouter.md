#### react에서 app.js 외에 추가적으로 reactRouter.js를 사용하는 이유
1. route 관리하기 위해서 사용한다. ; React에서는 SPA(Single Page Application)을 구현할 때, 페이지 전환을 javascript로 처리하기 위해 react-router-dom 같은 라이브러리를 사용하낟.
    - App.js의 역할 분리
        <br> App.js는 최상위 component로, route만 관리하는 것이 아니라 전역 상태 관리나 다른 설정도 처리할 수 있기에 AppRouter.js를 Routing logic만 담당하도록 하여 역할을 분리한다.
    - 코드 가독성 향상 
2. 역할 기반 파일 분리 - 유지보수에 용이
3. 개발 확장성
   - 동적 route 추가 : Lazy Loading(코드 스플리팅)이나 권한 기반 접근 제어 추가 가능
   - 테스트 가능성 향상 : AppRouter.js 별도로 두면 routing logic만 독립적으로 test 가능
  
#### React poject 주요 내용
1. structure 
    ```scss
       src/
   ├── components/        // 재사용 가능한 UI 컴포넌트
   ├── pages/             // 각 라우트에 해당하는 페이지 컴포넌트
   ├── routers/           // 라우터 관련 코드
   ├── services/          // API 호출이나 비즈니스 로직
   ├── assets/            // 이미지, CSS, 폰트 등 정적 파일
   ├── App.js             // 애플리케이션의 최상위 컴포넌트
   ├── index.js           // ReactDOM.render()로 루트에 렌더링
   ```
2. React 핵심 개념
   1. compenet 기반 구조 
   2. **Props**와 **State**
      - Props : 부모 컴포넌트에서 자식 컴포넌트로 데이터 전달
      - State : 컴포넌트 내부에서 관리하는 데이터 
3. React Router 사용
    - BrowserRouter : 라우팅을 위한 컨테이너
    - Routes : 라우트를 정의하는 컨테이너
    - Route : 각 경로와 컴포넌트를 매핑
    - Link : 페이지 이동을 위한 앵커 태그 대체
4. 성능 최적화
   1. 코드 스플리팅 : React.lazy, Suspense로 필요할 때만 컴포넌트 로드
   ```javascript
   const component = React.lazy(() => import('./Component'));
   ```
   2. 불필요한 렌더링 방지 : React.memo, useMemo로 최적화
   3. 상태 최소화(최소한 범위의 컴포넌트에서 state 관리)

#### AppRouter.js 작성 예제
```jsx
//AppRouter.js
import React from 'react';
import { BrowserReact, Routes, Route } from 'react-router-dom'; //dom에 대해서는 readingBookList의 '<DOM을 깨우치다>-코디 린들리'로 이동
import Home from './pages/Home';
import About from './pages/About';
import NotFound from './pages/NotFound';

const AppRouter = () => {
    return (
        <BrowserReact>
           <Routes>
               <Route path="/" element={<Home />} />
               <Route path="/about" element={<About />} />
               <Route path=*" element={<NotFound />}>
           </Routes>
        </BrowserReact>
    );
};

export default AppRouter;
```
App.js에서 AppRouter.js만 호출하도록 작성<br>
```jsx
//App.js
import React from 'react';
import AppRouter form './AppRouter';

function App() {
    return <AppRouter />;
}

export default App;
```
