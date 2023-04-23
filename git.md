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

```
빠진 기본 설정 (제가 유용하게 쓰는것들) 몇가지 더 추가해 볼께요 ️❤️

여러분 터미널에서 아래와 같이 입력하시고 엔터를 누르셔서 깃 설정 파일을 여시구요

사용자 설정 [user] 밑에 push와 pull친구들을 추가해 주세요 :)

push와 pull은 뒤에서 다루지만 간단하게 알려 드리면

push를 할때 default를 current으로 설정하므로서 로컬에 있는 브랜치 이름이 항상 리무트와 동일하다고 설정해줘서 push를 할때 일일이 'git push --set-upstream origin master' 옵션을 작성하지 않아도 되어요 :)

pull 명령어는 merge와 rebase 옵션을 선택해서 동작할 수 있는데 우리는 rebase를 이용해 볼거예요.

이 용어들은 아직 잘 모르셔도 괜찮아요 :)

깃 강의를 다 끝내시면 다 이해할 수 있답니다 🙌
```

---

## Git 생성, 삭제

| 명령어      | 분류          |
| ----------- | ------------- |
| git init    | 깃저장소 생성 |
| rm -rf .git | 깃저장소 삭제 |

---

## Git status

| 명령어        | 분류            |
| ------------- | --------------- |
| git status    | 깃 status       |
| git status -h | 깃 status help  |
| git status -s | 깃 status short |

---

## Git 명령어

| 명령어            | 분류                           |
| ----------------- | ------------------------------ |
| git checkout      | 원하는 버전으로 돌아갈수 있다  |
| SHA-1 hash        | 커밋아이디 40자 문자열로 구성  |
| git add \*.txt    | 해당 확장자 파일 add           |
| .gitignore        |                                |
| .git status       | -s 짧은버전, M/A/??            |
| git diff          |                                |
| git diff --h      |                                |
| git diff --staged | 둘이 비슷하다                  |
| git diff --cached | 둘이 비슷하다                  |
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

---

## Git config

```.gitconfig
  GNU nano 6.2         /home/yubin/.gitconfig                   [user]
        name = yubin
        email = shin.yubin18@gmail.com
[credential "https://github.com"]
        helper =
        helper = !/usr/bin/gh auth git-credential
[credential "https://gist.github.com"]
        helper =
        helper = !/usr/bin/gh auth git-credential
[core]
        autocrlf = true
[diff]
        tool = vscode
[difftool "vscoe"]
        cmd = code --wait --diff $LOCAL $REMOTE
[push]
        default = current
[pull]
        rebase = true

```

push를 할때 default를 current으로 설정하므로서 로컬에 있는 브랜치 이름이 항상 리무트와 동일하다고 설정해줘서 push를 할때 일일이 'git push --set-upstream origin master' 옵션을 작성하지 않아도 되어요 :)

pull 명령어는 merge와 rebase 옵션을 선택해서 동작할 수 있는데 우리는 rebase를 이용해 볼거예요.
