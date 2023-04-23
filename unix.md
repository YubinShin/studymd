man man 매뉴얼
man -clear

pwd (print working directory)
man pwd

ls (list)
ls -l (list long)
ls -a (list all)
ls -la(long all)

open . (터미널 현재경로를 파일탐색기로 열 수 있다)

cd (change directory)
cd . (현재 경로에서 현재경로로/ 아무효과가 없다)
cd .. (현재 경로에서 상위 경로로)
cd ~ (홈 디렉토리, 최상위 경로)
cd - (이전 경로로 왔다 갔다)

find(파일시스템에서 파일 검색)
find . -type file -name "_.txt" (현재경로에서 타입은 파일이고, 이름이 _ 인 txt 를 찾아줘)
find . -type directory -name "\*2" (현재경로에서 타입은 디렉토리이고, 이름이 2로 끝나는걸 찾아줘)

which node (노드의 설치 경로를 알려줘)
which code (vscode의 설치 경로를 알려줘)

touch
cat
echo

echo "Hello World" > new_file3.txt
echo "뒤에 메시지를 덧붙이려면 화살표 2개" >> new_file3.txt

mkdir
mkdir -p dir/dir2/dir3/dir4 (-path 옵션을 주면 경로대로 폴더를 자동으로 만들어줌)

cp 파일명 폴더명/
mv 파일명 폴더명/
mv 파일명1 파일명2 (파일 이름 바꾸기)

rm -r dir2 (reculsive 옵션)

---

grep (global regular expression print)
키워드로 검색하고 싶을때

grep "world" \*.txt

grep -n "world" \*.txt (몇번째 라인에 있나)

grep -ni "world" \*.txt (몇번째 라인에 있나)
-i 파일에서 텍스트를 찾을 때 대소문자를 구분하지 않고(case-insensitive)
"-r"은 현재 디렉토리와 그 하위 디렉토리에서 파일을 재귀적으로 검색하도록 하는 옵션입니다. "

---

환경 변수 설정하기

대문자, 스네이크 케이스로 생성한다
$변수명 을 쓰면 사용가능

cd $MY_DIR //환경변수 사용
unset MY_DIR //환경변수 삭제

ls env // 환경변수 리스트 확인하기

---

VIM

i

esc :wq
w(write changes)
q(quit)

---

```
sudo apt-get install unzip
unzip "*.zip"
```
