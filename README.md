# 리액트 타입스크립트 설치

1. 기본적으로 타스와 리액트는 호환이 안되기때문에 아래와 같이 설치한다

```bash
npm i

npm i @types/react -D
npm i @types/react-dom -D

npm i -D @types/react @types/react-dom

```

2. 폴더명 main.ts -> main.tsx 로 변경해주기

3. tsconfig.json 안에 아래 내용 추가

```jsx
{
  "compilerOptions": {
    "jsx": "react-jsx",
    }}

```

<!-- ----------------------------------------------------------------------- -->

# 1. React 프로젝트에서 타입스크립트를 사용하려면 타입 정의 파일이 필요하다

main.tsx 로 이동해서 import 구문 위에 마우스를 올려 봅시다.

아래와 같은 에러가 보입니다.

```tsx
'react' 모듈 또는 해당 형식 선언을 찾을 수 없습니다.ts(2307)
'react-dom/client' 모듈 또는 해당 형식 선언을 찾을 수 없습니다.ts(2307)
```

React 는 한때 타입스크립트와 경쟁했던 flow 라는 타입체커로 만들어진 프로젝트입니다.

그래서 빌드 결과물에 타입스크립트의 타입 정의 파일을 덧대는 방식으로 타입스크립트와 연동합니다.

이 에러를 해결하려면 아래의 커맨드를 입력해서 타입 정의 파일을 인스톨 해야 합니다.

```tsx
npm i -D @types/react @types/react-dom
```

타입스크립트는 `node_modules/@types` 디렉토리 아래에 타입을 정의한 파일이 있으면 js 파일도 타입스크립트로 대우를 해 줍니다.

# 2. 리액트 + 타입스크립트 파일의 확장자는 반드시 tsx 여야 한다.

div 태그 위에 마우스를 올려보면 div 이름을 알 수 없습니다. 라는 에러가 표시됩니다.

이것은 jsx 를 인식하지 못하는 에러이므로 파일 확장자를 ts 에서 tsx 로 바꾸면 해결됩니다.

# 3. 타입스크립트 설정 파일에 jsx 지원을 활성화 해야 한다.

이제 `'--jsx' 플래그를 제공하지 않으면 JSX를 사용할 수 없습니다.ts(17004)` 라는 에러가 표시됩니다.

타입스크립트 설정 파일 `tsconfig.json` 에 적절한 옵션을 제공해야 합니ㅏ.

타입스크립트는 플러그인 시스템을 사용하지 않는 대신에 모든 옵션을 설정 파일에 적는 시스템을 도입했습니다.

그래서 타입스크립트에는 tsx 문법만을 위한 전용 옵션이 있습니다.

[Documentation - JSX](https://www.typescriptlang.org/ko/docs/handbook/jsx.html)

이 옵션은 메타 프레임워크나 스케폴딩 도구가 설정해 둔 것을 그대로 놔 두는것이 좋습니다.

vite 의 경우는 아래와 같은 옵션을 채택하고 있습니다.

`tsconfig.json`

```tsx
{
  "compilerOptions": {
		"jsx": "react-jsx",
	}
}
```

참고로 위 설정 덕분에 react18 버전의 타입스크립트 프로젝트에서는 아래의 코드가 필요하지 않습니다.

```tsx
import React from "react";
```
