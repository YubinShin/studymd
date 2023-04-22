### package.json

파일 직접수정 & npm 명령어로 수정가능

| key             | value                                                          |
| --------------- | -------------------------------------------------------------- |
| version         | 프로젝트 버전                                                  |
| name            | 프로젝트 이름                                                  |
| description     | 프로젝트 설명                                                  |
| scripts         | npm run [scripts name]으로 실행할 수 있는 사용자 작성 스크립트 |
| dependencies    | 의존성 패키지들                                                |
| devDependencies | 개발환경에서만 사용하는 의존성 패키지들                        |

- 의존성 dependency
  프로젝트가 실행될때 의존하는 라이브러리들을 말함.
  dependencies를 이용해 프로젝트 내에서 사용하는 라이브러리를 관리한다.

- 라이브러리
  특정 기능을 수행하는 코드의 묶음, node.js에서는 패키지라고 부름.

### package-lock.json

프로젝트에 의존성을 추가하면 package-lock.json이라는 파일이 생성됨.
프로젝트에 의존성을 추가하면 자동으로 ‘^최신버전’으로 추가되는데,의존성 버전이 갑자기 변경되지 않도록, 설치된 버전을 고정하는 역할을함

1. 박과장이 npm으로 프로젝트를 만들어서 git에 소스코드를 push 합니다.
2. 이 때 node_modules 폴더를 제외하고 package.json 파일과 package-lock.json 파일을 같이 커밋합니다.
3. 김대리는 소스 코드를 pull 하고 npm install을 실행합니다.
4. 의존성 트리가 박대리가 셋팅한 환경과 동일하게 설치됩니다.
5. 프로그램이 정상적으로 실행됩니다.
6. 김대리는 정시 퇴근을 합니다.

예시 출처 : https://hyunjun19.github.io/2018/03/23/package-lock-why-need/

### npm init

package.json 파일을 만들어주고, 작업 폴더를 node.js 프로젝트로 만들어줌

### npm install

(축약형 npm i)<br>
기본적으로 node_modules 디렉터리는 코드관리(깃허브)나 배포시에 업로드하지 않음.

1. 의존성이 많아지면 용량이 너무 커지기도 하고
2. 운영체제별로 실행되는 코드가 다른 경우가 존재하기 때문

npm install 명령어를 아무 옵션 없이 사용하면 package.json에 정의된 dependencies와 devDependencies의 의존성을 node_modules 디렉터리에 내려받음.

### npm install [package-name]@[version]

패키지버전을 지정 가능

0. 의존성 버전 표기법
1. ~1.13.0-1.13.x 버전설치
2. ^1.13.0-1.x.x 버전설치, 가장 왼쪽이 0이 아닌 버전을 고정.
3. 0.13.0–0.13.0 버전만 설치

### npm install [package-name]

package.json의 dependencies에 추가됨.<br>
node_module 디렉토리에 저장됨

### npm install [package-name] --save-dev

개발용 의존성이란 배포전까지만 사용하는 의존성(ex. 유닛테스트라이브러리)<br>
--save-dev 옵션을 이용하면 개발용 의존성을 추가할 수 있음.
개발용 의존성은 package.json의devDependencies에 추가됨.

### npm install [package-name]@[version]

패키지 버전을 지정해 설치 가능

### npm install --production

프로젝트를 배포할 때는 개발용 의존성을 함께 포함할 필요가 없음.<br>
package.json 의 의존성만 node_modules에 내려 받음.

### npm install [package-name] --global

전역 패키지 추가<br>
패키지를 전역 패키지 디렉터리에 내려받음<br>
주로 프로젝트에 종속되지 않는 커맨드라인 도구들을 전역 패키지로 추가해서 사용<br>
예시- express-generator, pm2

- 로컬 패키지
  package.json 에 선언되어 있고, node_modules에 저장된 패키지
- 전역 패키지
  npm install -g 를 통해 내려받아, 전역 패키지 저장소에 저장된 패키지
  전역 패키지도 프로젝트에서 사용할 수 있으나, 프로젝트의 의존성이 package.json 내에 명시적으로 선언되어 있는 것이 프로젝트 관리의 좋은 방향

### npm remove [package-name]

의존성 패키지를 삭제할 수 있음<br>
package.json의 dependencies와 devDependencies에서 삭제하고
node_modules에서도 삭제

### npm 스크립트 명령어

| 명령어                | 설명                                          |
| --------------------- | --------------------------------------------- |
| npm run [script-name] | package.json의 scripts에 선언된 스크립트 실행 |
| npm start             | 프로젝트 실행                                 |
| npm run test          | 코드 유닛 테스트 등에 사용                    |
| npm run stop          | 프로젝트 종료                                 |

run을 제외하고 사용할 수 있을 뿐, npm 내부적으로 코드를 제공해 주는 것은 아님

#### npm run [script-name]

스크립트란 간단한 동작을 수행하는 코드
package.json의 scripts에 선언된 스크립트를
npm run [script-name] 명령어로 실행할 수 있음

```
{
  "scripts": {
  "say-hi": "echo \"hi"\"
  },
}
```

```
$ npm run say-hi
"hi"
```

npm script 내에선 의존성 패키지를 사용할 수 있음

```
"scripts":{"test": "node_modules/bin/tap test/\*.js"}
```

```
"scripts":{"test": "tap test/\*.js"}
```

## npx

1. 패키지 설치하지 않고 이용 가능
2. 특정 node.js 버전으로 코드 실행 가능
3. gist 코드를 다운 없이 바로 실행 가능

```
$ npm i cowsay -g
$ cowsay hi
```

```
$ npx cowsay hi
```

npx란 npm 패키지를 설치하지 않고 사용할 수 있게 해주는 도구이다.<br>
프로젝트에 추가하거나 전역 패키지로 추가하지 않고, npx를 이용하여 바로 실행할 수 있음<br>

---

```
$ npx node@12 index.js
$ npx node@14 index.js
```

npx 를 사용하면 <b>Node.js의 특정 버전을 사용하여 </b> js 파일을 실행할 수 있음.<br>
프로젝트의 Node.js 버전 별 실행환경을 확인할 때 유용

---

```
$ npx https://gist.github.com/zkat/4bc19503fe9e9309e2bfaa2c58074d32
```

gist는 github에 등록된 간단한 코드를 말한다.
(사람들이 예제코드를 깃허브에 많이 올려둡니다.)

npx를 이용하면 gist 코드를 다운받지 않고 바로 실행 가능하다.

git이 설치되어 있어야 함.

온라인상의 코드는 어떤 위험이 있을지 모르므로 코드를 잘 확인하고 실행해야 함.

## nvm

npm 버전 매니저, 공식은 아님. 노드 버전을 교체하기 쉽게 사용한당
