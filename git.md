## 초기설정

| 명령어                                          | 분류            |
| ----------------------------------------------- | --------------- |
| git config --list                               | 설정 확인       |
| git config --user.name                          | 설정 확인       |
| git config --global -e                          | 1)글로벌 설정   |
| git config --global core.editor "code"          | 2)글로벌 설정   |
| git config --global core.editor "code --wait"   | 3)글로벌 설정   |
| git config --global alias.st status             | 별명 설정해주기 |
| git config --global core.autocrlf true OR input | 4)줄바꿈 설정   |

1. 글로벌 설정한 내용을 터미널 에디터로 확인
2. 글로벌 설정 : vscode를 실행
3. 글로벌 설정 : 터미널이 vscode를 기다리게 설정
4. 줄바꿈(window, mac간 차이가 있어 설정 필요)
   협업할때 충돌하는 것 방지

| WINDOW    | MAC    |
| --------- | ------ |
| text \r\n | text\n |
| true      | input  |

\r carriage-return
\n line-feed

---

## Git 생성, 삭제

| 명령어      | 분류          |
| ----------- | ------------- |
| git init    | 깃저장소 생성 |
| rm -rf .git | 깃저장소 삭제 |

---

## Git 명령어

| 명령어            | 분류                           |
| ----------------- | ------------------------------ |
| git checkout      | 원하는 버전으로 돌아갈수 있다  |
| SHA-1 hash        | 커밋아이디 40자 문자열로 구성  |
| git add \*.txt    | 해당 확장자 파일 add           |
| .gitignore        |                                |
| .status           | -s 짧은버전, M/A/??            |
| git diff          |                                |
| git diff --h      |                                |
| git diff --staged |                                |
| git diff --cached |                                |
| git commit -am    | 전부다 메시지와 함께 커밋 해줘 |

---

## Git WorkFlow

```
Git-flow
├── git-directory
├── staging-area
└── working-directory
    ├── tracked
    │   ├── modified
    │   └── unmodified
    └── untracked
```
