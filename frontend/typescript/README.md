# TypeScript 기초 교육

## 환경 설정

### 1. [node.js 설치](https://nodejs.org/ko/download)

```bash
node -v
npm -v
```

### 2. 프로젝트 구성

- npm 초기화: `package.json` 파일이 생성

```bash
npm init -y
```

### 3. TypeScript + ts-node 설치

```bash
npm install --save-dev typescript ts-node @types/node
```
- **typescript** → TS 컴파일러
- **ts-node** → TS 파일을 바로 실행할 수 있게 도와줌
- **@types/node** → Node.js 타입 정의

### 4. TypeScript 설정 파일(tsconfig.json) 생성

```bash
npx tsc --init
```

- `tsconfig.json` 구성 (기본)

```jsonc
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "commonjs",
    "outDir": "./dist",
    "rootDir": "./src",
    "strict": true,
    "esModuleInterop": true
  }
}
```

### 5. TypeScript 코드 작성

```
ts-practice/
 ├─ src/
 │   └─ index.ts
 ├─ dist/
 ├─ package.json
 ├─ tsconfig.json
```

- `src/index.ts` 예시:

```ts
const message: string = "Hello TypeScript!";
console.log(message);
```

### 6. TypeScript 실행

> 방법 A: ts-node로 바로 실행

```bash
npx ts-node src/index.ts
```

> 방법 B: ts → js 컴파일 후 Node로 실행

1. 컴파일:

```bash
npx tsc
```

→ `dist/index.js` 생성됨

2. Node.js로 실행:

```bash
node dist/index.js
```

> 방법 C: 자동 빌드(watch 모드)

```bash
npx tsc --watch
```

