## 터미널 설치하기

wsl --list --verbose

### wls 유저 확인

```
sudo whoiam
```

### wls 유저 확인

```
sudo whoiam
```

### wls zsh 설치

```
sudo apt install zsh
```

### wls 터미널 시작디렉토리 설정

1. Ctrl + F : "source": "Windows.Terminal.Wsl" 입력 - 관련 줄로 이동
2. 검색한 줄에 쉼표(,)표기 후 엔터
3. "startingDirectory": "%USERPROFILE%" 입력하기

```json
"source": "Windows.Terminal.Wsl",
"startingDirectory": "%USERPROFILE%"

```

## 터미널 테마 변경

- 마이크로소프트 https://aka.ms/terminal-color-schemes
- 터미널테마사이트 https://terminalsplash.com/
- zsh 터미널 테마 https://github.com/romkatv/powerlevel10k
- 폰트 이름 MesloLGS NF

---

### setting.json (터미널 기본설정)

터미널 설정 -> 좌측상단 햄버거메뉴 ->JSON 파일 열기

```json
//setting.json (터미널 기본설정)
"defaults" : {
  "colorScheme" : "테마이름",
  "fontFace":"MesloLGS NF"
}
```

### .zshrc

```
code ~/.zshrc
// 우분투 루트 폴더의 zsh 터미널 설정파일 vs코드로
```

```js
// .zshrc에 추가
ZSH_THEME="powerlevel10k/powerlevel10k"

[[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh

alias python=python3.8

LS_COLORS="ow=01;36;40" && export LS_COLORS //Zsh ls의 글자 색깔 바꾸기

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

---

### VSCode

- 폰트설정

  ```
  Terminal > Integrated: Font Family
  MesloLGS NF
  ```

---

- VSCode 기본 터미널 설정

  1. vscode 설정으로 이동
  2. integrated terminal shell 검색
  3. Terminal › Integrated › Default Profile:Windows

  | powershell            |
  | --------------------- |
  | powershell            |
  | Ubuntu-18.04 (WSL) ✅ |

## 폴더

1. 리눅스 콘솔에서 윈도우에 있는 파일을 건드릴 수 있다!
   : 리눅스에도 파일을 저장할 수 있지만, 윈도우에 파일 저장을 추천
   (윈도우에서는 리눅스 파일 건드리지 말기)

2. 커맨드

1) ls (list)
   : 디렉토리 내 존재하는 목록 리스트
2) cd (change directory)
   : 내가 위치한 디렉토리를 변경 (폴더 안으로 들어갈 때, 맨 앞에 cd 해주기)
   : cd 폴더명 + tab 누르면 갈 수 있는 선택 옵션이 뜸
3) cd .. (띄어쓰기 주의)
   : 상위 폴더로 이동
4) clear : 화면이 깨끗해짐
5) touch : 새 파일 생성
   : touch 파일이름.확장자명
   (예: touch new_file.js)

3. 현재 윈도우 위치에서 cd .. 로 계속 상위 폴더로 가다보면 리눅스의 root 디렉토리에 도착한다. (자물쇠 모양)
   → ls 로 확인해보면 리눅스의 다양한 친구들이 뜬다.

1) cd home
   : home으로 들어가서 ls 해보면, 지난번에 만든 리눅스 사용자가 뜬다
   : 나의 리눅스 시스템 home 디렉토리 (윈도우의 home이 아님)

2) cd mnt = 윈도우 세계로 들어가는 창
   : 리눅스에서 윈도우 파일 생성도 가능

## npm 설치

apt-get 패키지인스톨러
apt-get update : apt-get이 패키지들을 다운받을수 있게 DB를 업데이트하는 명령어
(이렇게 해주면 apt에게 우왕 새로운 패키지 저장소네 하고 알려줄수 있다 )

curl(client url) : 프로토콜들을 이용해 URL 로 데이터를 전송하여 서버에 데이터를 보내거나 가져올때 사용하기 위한 명령줄 도구 및 라이브러리이다. JS로 따지면 ajax, fetch 같은 것
https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-CURL-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%82%AC%EC%9A%A9%EB%B2%95-%EB%8B%A4%EC%96%91%ED%95%9C-%EC%98%88%EC%A0%9C%EB%A1%9C-%EC%A0%95%EB%A6%AC

```
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install nodejs
```

## 파이썬 설치

- PPA(Personal Package Archive)
  우분투의 공식 패키지 저장소에 없는 서드 파티 소프트웨어를 위한 개인용 소프트웨어 패키지 저장소이다.
- 데드스네이크라는 좋은 기관이 있다~ 우분투를 위한 파이썬을 제공해주는 곳
  11-1 ppa 패키저장소 설치 sudo add-apt-repository ppa:deadsnakes/ppa
  11-2 업데이트 리스트 sudo apt-get update
  11-3 파이선 설치 sudo apt-get install python 3.8
  11-4 alias 설정 ~/.zshrc 맨밑에 alias python=python3.8

## Prettier, Wsl 커맨드

vscode keybindings.json

```
// C: > Users > shiny > AppData > Roaming > Code > User> keybindings.json > ...
{
"key": "ctrl+f5",
"command": "workbench.action.reloadWindow",
"when": "editorTextFocus"
}
```

## Github Cli 설치

Debian, Ubuntu Linux (apt)
https://github.com/cli/cli/blob/trunk/docs/install_linux.md#debian-ubuntu-linux-apt

```
// 터미널에 입력
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

13-1 git설치 sudo apt-get install git
13-2 gh_1.1.0_linux_amd64.deb 다운로드
13-3 다운로드 폴더에서 sudo apt-install ./gh_1.1.0_linux_amd64.deb
13-4 git config --global user.name "이름"
13-4 git config --global user.email "이메일"
13-5 gh auth login "권한얻기"

## NVM

14-1 nvm설치

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.36.0/install.sh | bash
```

14-2 .zshrc에 추가
//zsh는 우리가 nvm을 설치했는지 몰라서 알려줘야함
//공식사이트에 아래같은 코드가 있을거다

```
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```

14-3 nvm ls-remote (모든 nvm 버전 확인)
14-3 nvm ls-remote --lts (nvm lts 버젼 확인)
14-4 node -v (현재 버젼 확인)
14-5 nvm install --lts=버전이름소문자로
14-6 nvm ls // 설치 되어있는 nodejs 버전 확인하기
14-7 nvm use v버전번호 // nodejs 버전 바꾸기

## sudo apt-get sl

멋진 프로그램
