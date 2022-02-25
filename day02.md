#2일차 정리
# TIL

`Today I Learned`: 하루하루 배웠던 내용을 기록하는 repository

# git 기초

- git의 3공간
  - 분장실, 무대, 사진 촬영본
  - working directory, staging area, commits



## git 명령어

1. git 초기설정
- 처음 1번만 실행

```bash
git config --global user.name "유저명"
git config --global user.email "유저 이메일" # 깃허브에서 사용
```

- `git config --global user.name "닉네임"`
  `git config --global user.email "메일 주소"`
  
  - 닉네임(user.name) 변경 시
    `git config --global --unset user.name`
    `git config --global user.name "새로운 닉네임"`
  
  확인
  `git config --global --list`

2. git init (U)
- 새롭게 로컬에서 시작하는 것 
- 맨처음 1회, 절대 홈폴더에서 하지 않는다.
- git init한 폴더의 하위 폴더에서 절대 git init하지 않는다.
   - 터미널에는 (master)라고 표기된다

2. git status 파일 상태 확인

- git 관리 : Untracked
- git 관리X : Tracked
    - Unmodified 최신상태
    - Modified
    - Staged

4. git add (A)

​	`git add a.txt 파일`
​	`git add my_folder/ 폴더`
​	`git add .`  :  전부

4. git commit -m "메세지"
    `git commit -m "first commit"`

- (root-commit): 최초의 커밋을 뜻한다

6. git log
- 커밋 내역(ID, 작성자, 시간, 메세지 등)을 조회한다



## github 가입

> https://github.com/ 

**Setting**

프로필 - Repositories - main을 master로 수정 - Update

**원격 저장소(Remote Repository)**

*원격 저장소 이용해 다른 사람과 공유, 궁극적으로 협업을 위해*

- TIL repository 생성(remote)

  - New repositoty - 이름, 설명, Public

- 로컬 저장소와 원격 저장소 연결

  - 저장소 주소 복사 후 TIL 폴더에서 vscode 열기

    `kyle@KYLE MINGW64 ~/TIL`

    `$ git init`

    `Initialized empty Git repository in C:/Users/kyle/TIL/.git/`

- git remote

  - 로컬 저장소에 원격 저장소를 등록, 조회, 삭제할 수 있는 명령어
  - 등록 - `git remote add <이름> <주소>`
  - 조회 - `git remote -v`
  - 연결 삭제 - `git remote rm <이름>` 혹은 `git remote remove <이름>`

- TIL 파일을 Github 원격 저장소에 업로드(커밋 업로드)

  `$ git status`

  `$ git commit -m "Upload TIL"`

  `$ git log --oneline`

  `$ git push origin master`

<u>반드시 git add → git commit → git push 의 단계로 업로드!! (로컬 저장소에서 변경 후, 변경 사항을 원격 저장소에 반영하는 형태)</u>



## github 업로드
#### init부터 push까지

- 저장/touch > add > commit > push

1. 파일 생성 touch README.md
2. 파일 저장 ctrl+s
3. add 
    `$ git add README.md` 
4. commit 
    `$ git commit -m "add README.md"` 
5. push
    $ git log --oneline                                    한줄 출력
    `$ git push origin master` 

- (오류 시) `git pull origin master`

**github에서 파일 업로드(push) 했을 경우**
파일 업로드 이후 -> Add -> commit -> git push -f origin master 

1. `$ git add "README.md"`
2. `$ git status`
3. `$ git commit -m "fix conflict"`    충돌 고친 기록 남김
4. `$ git push -f origin master` 



##  .gitignore

- 민감한 개인 정보가 담긴 파일 (전화번호, 계좌번호, 각종 비밀번호, API KEY 등) / OS(운영체제)에서 활용되는 파일 / IDE(통합 개발 환경 - pycharm) 혹은 Text editor(vscode) 등에서 활용되는 파일 등 작성하는 목록

[python, jupyternotebook 관련 gitignore](https://www.toptal.com/developers/gitignore) 

1. 파일 생성
   `$ touch .gitignore` .은 숨김 파일을 뜻한다
2. 내용 복붙 후 저장
3. $ git add .
4. $ git commit -m "add .gitignore"
5. $ git log --oneline                            commit 내역 확인
6. $ git push origin master                 github master에 올라감
   - github에 .gitignore이 업로드 된 것을 확인할 수 있음



# 원격 저장소 가져오기

- push는 상향식인 반면, clone/pull은 하향식

### 1. clone

- 원격 저장소를 복제하여 로컬 저장소를 생성
- ex) 팀프로젝트 시, 조장이 원격저장소를 만들어 공유하게 되면 조원들은 원격저장소를 clone을 해서 사용

**clone은 init된 상태에서  사용하지 않기**, **홈 폴더에서 git clone 사용할 것 **

`git clone <원격 저장소 주소>`

`$ git clone https://github.com/hwas2/TIL.git TIL-class` 사용자 폴더에 TIL-class 폴더 생성

vs code에서 TIL 상태 확인 `~/TIL (master)`
`$ git clone github주소입력.git TIL-class`
`$ cd TIL-class/` 로 확인
`$ git remote -v`  버전 확인 및 연결 가능

### 2. pull

- 원격 저장소의 변경 사항을 가져와 로컬 저장소를 업데이트

`git pull <저장소 이름> <브랜치 이름>`

`git pull origin master`