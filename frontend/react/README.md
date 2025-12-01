# React 기초 교육

## 환경 구성

- [node.js 설치](https://nodejs.org/ko/download)
- [npm 프로젝트 생성](https://github.com/ESG-EDU/Docs/tree/main/react)

### 프로젝트 생성 완료 후 확인

- 프로젝트 폴더 구조 (`vite` 기준)

```pgsql
/root
 └────node_modules
 └────public
 └────src
   └────main.jsx
   └────App.jsx
 └────index.html
 └────package.json
 └────vite.config.js
 └────eslint.config.js
```

- `node_modules`: npm 외부 모듈
- `public`: 정적 파일
- `src`: 소스코드 폴더
- `main.jsx`: 프로젝트 실행 파일
- `App.jsx`: 첫화면 파일
- `index.html`: 기본 페이지 파일
- `package.json`: npm 설정 파일
- `vite.config.js`: vite 설정 파일
- `eslint.config.js`: es lint 설정 파일

### 프로젝트 명령어

- 개발자 모드

```bash
npm run dev
```

- 배포

```bash
npm run build
```

- 미리보기

```bash
npm run preview
```
