## 모듈이란?

간단한 프로그램이라면 파일 하나로도 가능하지만,
프로젝트가 커지면 기능에 맞게 코드를 분리하는 것이 중요하다.
모듈은 코드를 분리하기 위한 방법이다.
모듈의 모음을 패키지라고 한다.

## Node.js 기본 제공 모듈

Node.js는 다양한 모듈을 기본적으로 제공함.

기본 제공 모듈은 직접 작성하기 매우 어렵거나 복잡한 로직을 포함한 모듈이 있으므로 자주 사용되는 기본 제공 모듈을 학습해야 함.

1. console
2. process
3. fs
4. http
5. url
6. os
7. Path
8. Crypto

console
브라우저 콘솔과 유사한 디버깅 도구

| 메서드    | 설명          |
| --------- | ------------- |
| log()     | 로그레벨 표시 |
| warn()    | 로그레벨 표시 |
| error()   | 로그레벨 표시 |
| time()    | 시간추적      |
| timeLog() | 시간추적      |
| timeEnd() | 시간추적      |

process

| 명령어  | 설명                         |
| ------- | ---------------------------- |
| arch    | 실행환경 및 변수 관련값 제공 |
| argv    | 실행환경 및 변수 관련값 제공 |
| env     | 실행환경 및 변수 관련값 제공 |
| abort() | 프로세스 동작 관련 함수      |
| kill()  | 프로세스 동작 관련 함수      |
| exit()  | 프로세스 동작 관련 함수      |

abort - 중단하다.

fs
파일 입출력을 하기 위해 사용.

| 메서드      | 설명                           |
| ----------- | ------------------------------ |
| readFile()  | 파일 읽기                      |
| writeFile() | 파일 쓰기                      |
| -Sync()     | 동기 동작                      |
| watch       | 파일/디렉터리 변경 이벤트 감지 |

http

서버, 클라이언트에서 사용
| 메서드 | 설명 |
| --------- | ------------- |
| createServer() | 서버 객체 생성 |
| Request() | http 요청 생성 |

기타

| 메서드 | 설명                                                                         |
| ------ | ---------------------------------------------------------------------------- |
| url    | url 파싱                                                                     |
| os     | 운영체제 정보 가져옴(cpu, memory, type)                                      |
| Path   | 디렉터리 string 관련 작업, 서로 다른 운영 체제간 공통된 로직이 필요해서 사용 |
| crypto | 암호화, hash 관련 함수 제공                                                  |

## 모듈 작성법

1. 모듈이 load될 때 사용될 값을 module.exports로 내보냄.

```js
//elice.js
const 이름 = "엘리스";
const 나이 = 5;
const 국적 = "대한민국";

module.exports = { 이름, 나이, 국적 };

---

const 학생 = require('./elice')
```

2. 변수명으로 내보내기
   모듈을 기본적으로 object 로 만들고, 각 key -value를 지정해서 내보냄

```js
//elice.js

const 이름 = "엘리스";
const 나이 = 5;
const 국적 = "대한민국";

exports.이름 = 이름;
exports.나이 = 나이;
exports.국적 = 국적;

---

const 학생 = require('./elice')
```

3. 함수형 모듈
   모듈을 사용할 때 값을 정할 수 있어서 유용함.

```js
//elice.js

module.exports = (이름, 나이, 국적) => {
  return {
    이름,
    나이,
    국적
  };
}

---

const 학생 = require('./elice');
console.log(학생('엘리스', 5, '대한민국'));
```

## 모듈 사용법

require()

require 함수를 통해 모듈을 load 할 수 있음

첫번째 require 시 모듈코드를 실행 후 메모리에 cache로 저장한다. 그 이후 부턴 이미 저장된 코드를 가져다 쓰게 됨.(모듈이 두번 실행되지 않음)

그래서 다른 파일에서 또 require 한다고 해도 모듈이 두번 실행되지 않는다.

그래서 모듈 코드를 여러번 실행하고 싶다면, 함수 모듈로 작성해야 한다.

1. npm 의존성 패키지

```js
const dayjs = require("dayjs");
console.log(dayjs());
```

의존성 패키지들은 require('package-name')로 load 할 수 있음. 패키지를 사용하려면 node_modules 폴더에 내려받아져 있어야 함.(package.json 이나 package-lock.js에 있어도 폴더에 없으면 로드 못 함.)

2. 직접 작성한 모듈

```js
const myModule = require("./my-module");
console.log(myModule);
```

직접 작성한 모듈은 현재 파일과의 상대경로 이용해서 load

- my-module이 .js 파일인 경우
  해당 파일 load

- my-module이 폴더명인 경우
  my-module/index.js load

3. 함수형 모듈

```js
const myFunctionModule = require("./my-function-module");
console.log(myFunctionModule(name, age, nationality));
```

함수형 모듈은 load한 경우 모듈이 바로 실행되지 않음.
필요한 시점에 load된 함수를 실행하여 모듈을 사용할 수 있음.

4. json 파일

```js
const myData = require("./my-data.json");
const myData = require("./my-data");
```

js말고 json도 require 할 수 있다.
자동으로 javascript object로 파싱해줌.

json파일도 require시 확장자 생략 가능.
