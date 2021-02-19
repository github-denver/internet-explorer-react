# create-react-app@4.0.1에서 Internet Explorer 9, 10, 11 실행 방법

### 인스톨

```
npx create-react-app
```

그리고 실행해 주세요.

```
npm start
```

## Internet Explorer 11

SCRIPT1003: ':'가 필요합니다.

0.chunk.js

SCRIPT1002: 구문 오류

main.chunk.js

### 인스톨

react-scripts 버전을 3.4.4로 다운그레이드 해주시고 react-app-polyfill을 설치해 주세요.

```
npm install --save --save-exact react-scripts@3.4.4

npm install react-app-polyfill
```

### package.json

그리고 browserslist에서 "ie > 9"를 추가해 주세요.

```
...
"browserslist": {
  "production": [
    ">0.2%",
    "not dead",
    "not op_mini all",
    "ie >= 9", // 추가해 주세요.
  ],
  "development": [
    "last 1 chrome version",
    "last 1 firefox version",
    "last 1 safari version",
    "ie >= 9", // 추가해 주세요.
  ]
}
...
```

```
npx browserslist
```

### /src/index.js

```
import 'react-app-polyfill/ie9' // 추가해 주세요.
import 'react-app-polyfill/stable' // 추가해 주세요.
...
```

/node_modules 폴더를 삭제한 후 재 설치해 주세요.

```
npm install
```

그리고 실행해 주세요.

```
npm start
```

## Internet Explorer 9, 10

SCRIPT5009: 'Map'이(가) 정의되지 않았습니다.

index.js

### 인스톨

```
npm install core-js mutation-observer
```

### /src/index.js

```
import 'core-js/stable' // 추가해 주세요.
import 'mutation-observer' // 추가해 주세요.

import 'react-app-polyfill/ie9'
import 'react-app-polyfill/stable'
...
```

/node_modules/react-scripts/config/webpack.config.js 파일에서 paths.appIndexJs를 위로 이동해 주세요.

```
...
entry: [
  // Finally, this is your app's code:
  paths.appIndexJs, // 이동해 주세요.
  // We include the app code last so that if there is a runtime error during
  // initialization, it doesn't blow up the WebpackDevServer client, and
  // changing JS code would still trigger a refresh.

  // Include an alternative client for WebpackDevServer. A client's job is to
  // connect to WebpackDevServer by a socket and get notified about changes.
  // When you save a file, the client will either apply hot updates (in case
  // of CSS changes), or refresh the page (in case of JS changes). When you
  // make a syntax error, this client will display a syntax error overlay.
  // Note: instead of the default WebpackDevServer client, we use a custom one
  // to bring better experience for Create React App users. You can replace
  // the line below with these two lines if you prefer the stock client:
  // require.resolve('webpack-dev-server/client') + '?/',
  // require.resolve('webpack/hot/dev-server'),
  isEnvDevelopment &&
    require.resolve('react-dev-utils/webpackHotDevClient'),
].filter(Boolean),
...
```

/node_modules/.cache 폴더를 삭제한 후 실행해 주세요.

```
npm start
```

## Internet Explorer 9, 10

SCRIPT438: 개체가 'setPrototypeOf' 속성이나 메서드를 지원하지 않습니다.

0.chunk.js

### 인스톨

```
npm install setprototypeof
```

### /src/polyfill.js 파일 생성 및 내용 추가

```
const setPrototypeOf = require('setprototypeof')

Object.setPrototypeOf = setPrototypeOf
```

### /src/index.js
```
import './polyfill' // 추가해 주세요.

import 'core-js/stable'
import 'mutation-observer'

import 'react-app-polyfill/ie9'
import 'react-app-polyfill/stable'
...
```

/node_modules/.cache 폴더를 삭제한 후 실행해 주세요.

```
npm start
```

## Internet Explorer 9, 10, 11에서 변화가 없다면?

Internet Explorer 검색 기록을 삭제하신 후 새로 고침을 해보세요.

1. 도구 → 인터넷 옵션을 클릭해 주세요.
2. 검색 기록 → 삭제 버튼을 클릭해 주세요.
3. 임시 인터넷 파일 및 웹 사이트 파일, 쿠키 및 웹 사이트 데이터를 체크하신 후 삭제 버튼을 클릭해 주세요.


## 참고
[https://blog.csdn.net/It_rod/article/details/100574389](https://blog.csdn.net/It_rod/article/details/100574389)

[https://github.com/facebook/create-react-app/issues/5336](https://github.com/facebook/create-react-app/issues/5336)
