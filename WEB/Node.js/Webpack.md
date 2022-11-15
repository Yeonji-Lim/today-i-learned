# Webpack

## 필요성

index.html에서 lodash와 연관성이 보이는데, index.js은 lodash의 필요성을 명시적으로 선언하지 않았음 이로인한 문제점

- 해당 스크립트가 외부 라이브러리에 의존한다는 것이 명확하지 않음
- 의존성을 잃어버렸거나 잘못된 순서로 포함된 경우 애플리케이션이 제대로 동작하지 않음
- 의존성이 포함되었는데 사용되지 않는 경우, 브라우저는 필요없는 코드를 강제로 다운로드

webpack을 사용해서 이런 스크립트를 관리할 수 있다.

## 시작

webpack은 기본적으로 src/index.js를 entry point로 한다.

그리고 dist라는 폴더에 빌드한 파일을 추출한다.

npm run dev로 실행 할 수 있다.

## 번들 만들기

다음과 같이 분리된 디렉터리 구조를 가진다.

~~~
./src : 소스코드
./dist : 배포코드
~~~

lodash의 의존성을 index.js와 함께 번들링

~~~
npm install --save lodash
~~~

참고 : 최종 제품에 번들로 제공될 패키지를 설치할 때는 npm install --save를 사용해야 함, 개발 목적으로 패키지를 설치한다면 npm install --save-dev 사용

~~~
npx webpack
~~~

src/index.js를 엔트리포인트로 사용, output으로 dist/main.js 생성

빌드 후 index.html을 열면 Hello webpack 문구가 출력됨

### 용어

- Entry point : 모든 의존 객체들이 모인 웹팩의 시작점
- Output : 어느 곳의 빌드 과정에서 JS와 정적 파일들을 모을지 정의
- Loaders : 웹팩이 다양한 확장자를 다룰 수 있도록 도와주는 서드파티 확장 프로그램들 JS가 아닌 파일들을 모듈로 바꿔줌
- Plugins : 웹팩의 동작 방식을 바꿔주는 서드파티 확장 프로그램
- Mode : 개발과 생산 두 모드를 정의함. 기본은 생산

## 모듈

import, export 문은 ES2015에서 표준화되어있다. 그런데 이는 명명 브라우저에서 인식하지 못하는데, webpack은 이와 상관없이 바로 사용할 수 있도록 지원한다. 

보이지 않는 곳에서 트랜스파일해서 어떤 브라우저든 실행가능하게 하는 것!
dist/main.js를 통해 어떻게 트랜스파일하는지 볼 수 있음

import, export 이외에도 다양한 모듈 구문을 지원하는데, 자세한 내용은 Module API에서 볼 수 있다.

webpack은 import와 export문 이외에는 코드를 변경하지 않는다.

다른 ES2015 기능을 사용한다면 webpack의 로더 시스템인 babel을 트랜스파일러로 사용해야 함

## 설정

원래 webpack은 버전4 부터 설정이 필요없음

그런데 대부분의 프로젝트는 좀 더 복잡한 설정이 필요하므로 설정파일을 제공한다. 

root 폴더에 webpack.config.js 라는 파일을 만들어야 함

~~~
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
~~~

이 파일에서 환경설정 객체를 추출해야 함

-> webpack은 node.js 같은 브라우저 창이 없는 자바스크립트 환경에서 동작하기 때문

새로운 설정 파일을 이용하여 다시 빌드

~~~
npx webpack --config webpack.config.js
~~~

기본이 webpack.config.js이기 때문에 그냥 해도 되지만 --config로 어떤 이름의 설정 파일이든 선택가능

이 설정 파일로 로더의 규칙, 플러그인, 해석 옵션 등 기타 여러 향상된 기능을 지정할 수 있다.

## NPM Script

CLI에서 webpack의 로컬 사본을 실행하기 위해 단축 명령어 설정 가능

package.json의 script에 build 추가

~~~
    "build": "webpack"
~~~

이렇게 하면 npx 대신에 npm run build를 사용가능함

모든 컨트리뷰터가 동일한 공통의 스크립트 세트를 사용할 수 있도록 하는 거임!