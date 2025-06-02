## 바닐라 JS 프로젝트 성능 개선
- url : https://dcrpqw4gqr0ey.cloudfront.net/index.html

## 성능 개선 보고서
- 성능 개선 전 pageSpeed Insights를 사용한 성능 측정
![image](https://github.com/user-attachments/assets/3d4a9f3c-4935-4501-aa56-632cd7442ec8)

<img width="627" alt="스크린샷 2025-06-02 오후 5 59 01" src="https://github.com/user-attachments/assets/cfa09ef7-2825-4e9c-8b0f-a644a59854ed" />


성능 개선 전을 보면 `FCP`,`LCP`의 개선이 필요했다.

### LCP 개선 방법
`Largest Contentful Paint (LCP)` : LCP는 페이지에서 가장 큰 콘텐츠 요소가 로드되는 시간을 측정한다.
1. **이미지 최적화** : jpg이미지를 webp로 변환하여 이미지의 크기를 줄였다.
2. **렌더링 차단 리소스 최소화**
-  중요하지 않은 JS`(cookie-consent.js)`는 비동기 로딩(defer)을 추가하여 필요시에 로드되게 했다.
 - Google Tag Manager 코드를 `window.addEventListener('load')`로 감싸서 페이지의 모든 리소스가 로드된 완료 시점에 GTM 삽입이 되게 했다.
3. **이미지 preload 태그 사용하기** : head태그 안에 큰 이미지들을 preload시켰다.


### CLS 개선 방법
`Cumulative Layout Shift (CLS)`: CLS는 페이지 로딩 중 예상치 못한 레이아웃 이동을 측정한다.

**이미지 요소에 크기 지정**: width,height속성을 명시하여 크기를 지정해주었다.

### 접근성 개선 방법

이 부분은 이미지 속성에 `alt`만 추가해도 점수가 많이 오른 것을 볼 수 있었다.

### 결론
LCP와 FCP,CLS는 서로 연관되어있는 것 같다고 느꼈다.
이미지 최적화만해도 세 지표가 모두 동시에 개선되는 것을 볼 수 있었다.
