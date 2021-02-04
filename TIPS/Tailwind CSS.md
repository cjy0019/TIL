# Tailwind CSS

<img src="https://github.com/cjy0019/TIL/blob/master/images/tailwindcss.jpg?raw=true" width="50%">

## 1. Tailwind CSS 란?

- 유틸리티 클래스로 구성된 CSS 프레임워크
- 사용자 커스터마이징이 가능한 저수준 CSS 프레임워크



## 2. 특징

- 기본 단위는 rem이다.
- 반응형에 최적화 되어있다.
- transition, transform은 현재 구현 되어있지 않다.



## 3. 사용법

먼저 현재 디렉토리를 노드 프로젝트로 만들어준다.

```bash
$ npm init -y
$ npm i tailwindcss postcss autoprefixer
```

루트폴더에 .postcssrc 파일이나 postcss.config.js 파일을 생성한다.

```js
// postcss.config.js
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer'),
  ]
}
```

`npx tailwindcss init`을 통해서 tailwind.config.js 파일을 생성한다.

```js
// tailwind.config.js
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [],
}
```

그 후 루트 디렉터리에 src와 public 디렉터리를 생성해준다.

```css
// src/styles.css

@import 'tailwindcss/base';
@import 'tailwindcss/components';
@import 'tailwindcss/utilities';
```

또는 다음과 같이 작성할 수도 있다.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

pacakge.json에서 scripts부분을 수정해준다.

```json
// package.json

{
  "name": "wowtest",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build-css": "tailwindcss build src/styles.css -o public/styles.css"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "tailwindcss": "^2.0.2"
  }
}
```

마지막으로 html 파일에 link태그로 styles.css파일을 연결해준다. 기본적으로 tailwindcss에는 normalize가 적용되어있기 때문에 링크로 연결시켜주면 어떤 스타일도 적용되지 않은 상태로 렌더링된다.

```html
<!-- public/index.html -->

<link rel="stylesheet" href="styles.css">
```

