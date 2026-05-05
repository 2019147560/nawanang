# 하하쓰리 — Next.js 버전

`나와나망` 고립·은둔청년 통합 정보 플랫폼 디자인 목업의 Next.js (App Router) 포팅 버전.

## 구조

```
hahathree-next/
├── app/
│   ├── layout.jsx        # 루트 레이아웃 (Pretendard 폰트, 글로벌 CSS)
│   ├── page.jsx          # 지원사업 검색/상세 (단일 페이지 라우터)
│   └── globals.css       # 디자인 토큰 + 베이스 스타일
├── package.json
├── next.config.js
└── jsconfig.json
```

App Router 기반이므로 모든 인터랙션은 `'use client';` 디렉티브가 붙은 `app/page.jsx`에서 처리합니다.

## 실행

```bash
cd hahathree-next
npm install
npm run dev
```

기본 포트: `http://localhost:3000`

## 라우팅 메모

목록 ↔ 상세 전환은 단일 페이지 내부 `route` state로 처리되어 있습니다.
실제 URL 기반 라우팅으로 분리하려면:

- `app/page.jsx` → 목록(ListPage)만 남기고 default export
- `app/programs/[id]/page.jsx` 추가 → ProgramDetailPage 렌더
- `next/link`, `useParams` 등으로 교체

## 의존성

- `next@14.2.5`
- `react@18.3.1`, `react-dom@18.3.1`
- 외부 폰트: Pretendard (jsDelivr CDN), Noto Sans KR (Google Fonts) — `app/layout.jsx`에서 `<link>` 로 로드
