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
| SHA-1 hash        | HASH코드 40자 문자열로 구성    |
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

---

## 유용한 파일변경 명령어

| 명령어          |
| --------------- |
| git rm <파일명> |
| git mv <파일명> |

1. 파일 지우면서 stage에도 반영,rm <파일명> 했을때보다 더 편리
2. 이름 변경하면서 stage에도 반영,mv <파일명> 했을때보다 더 편리

---

## Git log

| 명령어                                |
| ------------------------------------- |
| git log                               |
| git log --p (git log --patch)         |
| git log --oneline                     |
| git log --oneline --reverse           |
| git chekout HASH코드                  |
| git log -3                            |
| git log --oneline -3                  |
| git log --author='ellie'              |
| git log --before='2020-10-29'         |
| git log --grep='project'              |
| git log -S '문자열'                   |
| git log -S '문자열' -p                |
| git log about.txt                     |
| git log about.txt -p                  |
| git log about.txt -s                  |
| git log HEAD                          |
| git log HEAD ~2                       |
| git show HASH코드                     |
| git show HASH코드:user_repository.txt |
| git diff HASH코드1 HASH코드2          |
| git diff HASH코드1 HASH코드2 <파일명> |

1. git log --p : diff 한것처럼 log를 볼 수 있음
2. git log --oneline : 간단하게 1줄로 볼 수 있음
3. HASH코드 : HASH 코드 7자
4. git log -3 : 최근 커밋 3개를 보여줘

```
// git log 예쁘게 만들기
git config --global alias.hist "log --graph --all --pretty=format:'%C(yellow)[%ad]%C(reset) %C(green)[%h]%C(reset) | %C(white)%s %C(bold red){{%an}}%C(reset) %C(blue)%d%C(reset)' --date=short"
```

---

## Git HEAD

헤드 : 지금 내가 바라보고 있는 이 시점의 커밋(버전)

```
        head~2    head~1    head

          a ------- b ------- c ------- d    master
```

---

## Git Tag

보통 릴리즈 버전을 태그로 꽂아둠
git log 볼 때 구분하고 싶어서

```ascii
┌────────────────────────────┐
│                            │
│    semantic versioning     │
│                            │
│                            │
│     major  minor   fix     │
│                            │
│   v   2  .   0   .  0      │
│                            │
└────────────────────────────┘
```

major : 특정 기능이 추가 되었을때, 전체적인 업데이트가 이뤄졌을때
minor : 커다란 기능 중에서 조금의 기능이 업데이트, 개선되었을때
fix : 기존에 존재하는 기능에서 오류 수정했을때, 성능이 개선되었을때

| 명령어                                      |
| ------------------------------------------- |
| git tag v1.0.0 <HASH코드>                   |
| git tag v1.0.0 <HASH코드> -am               |
| git show v1.0.0                             |
| git tag                                     |
| git tag -l " v1.0.0"                        |
| git tag -ls " v1.0.0"                       |
| git tag -d v1.0.0                           |
| git checkout v1.0.0                         |
| git checkout -b <브랜치명> <태그명(v1.0.0)> |
| git push origin --tags                      |
| git push origin --delete v1.0.0             |

태그를 달 수 있다.
-a (annotate) 주석을 달다
git show v1.0.0 : 누가 만들었는지, 언제 만들었는지, 메시지도 보여줌
git tag : 모든 태그 확인가능
git checkout v1.0.0 : 태그가 달린 커밋으로 헤드를 옮긴다
git checkout -b <브랜치명> <태그명(v1.0.0)> : 태그를 체크아웃하면서 브랜치 만들수 있다.
git push origin --tags : 모든 태그를 싱크할수 있다

## Git Branch

엘리는 branch를 직장에서 하루에 1~2개씩 만드는 듯

```
                          ┌────────g ──────────h ◄── featureA
                          │
                          │
                          │
                          │
a ────── b ───── c ────── d ◄───master
                          │
                          │
                          │
                          └────────e ──────────f ◄── featureB
```

### squash 방식 (e,f를 합쳐서 i로 만들어 합친다)

```
                          ┌────────g ───────h ◄── featureA
                          │
                          │
                          │
                          │
a ────── b ───── c ────── d ──────── i ◄── master

```
