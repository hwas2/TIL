# Today I Leraned
하루하루 배웠던 내용을 기록하는 repository


## git 기초
1. git 초기설정
- 처음 1번만 실행
`git config --global user.name "닉네임"`
`git config --global user.email "메일 주소"`
닉네임(user.name) 변경 시
`git config --global --unset user.name`
`git config --global user.name "새로운 닉네임"`
확인
`git config --global --list`

2. git init
- 파일 옆에 U라고 뜬다

3. git status
- git 관리 : Untracked
- git 관리X : Tracked
    - Unmodified 최신상태
    - Modified
    - Staged

4. git add
`git add a.txt 파일`
`git add my_folder/ 폴더`
`git add . 전부`

5. git commit
`git commit -m "first commit"`
- (root-commit): 최초의 커밋을 뜻한다

6. git log
- 커밋 내역을 조회한다