# 깃허브 프로필 설정

1. github 이름으로 저장소 생성
   - Public / Add a README file 체크하기

2. 프로필 수정

   - Edit README - 간단한 인사말과 stat 추가 - Commit Changes

   - [이모지 링크](https://www.emojiengine.com/ko/keyboard/)



# Branch

- `브랜치`란 나뭇가지처럼 여러 갈래로 작업 공간을 나누어 **독립적으로 작업**할 수 있도록 도와주는 Git의 도구입니다.

- 장점

  1. 브랜치는 독립 공간을 형성하기 때문에 원본(master)에 대해 안전합니다.
  2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적인 개발이 가능합니다.
  3. 특히나 Git은 브랜치를 만드는 속도가 굉장히 빠르고, 용량도 적게 듭니다.

  ```bash
  # 브랜치 목록 확인
  $ git branch
  # 원격 저장소의 브랜치 목록 확인
  $ git branch -r
  
  # 새로운 브랜치 생성
  $ git branch <브랜치 이름>
  # 특정 커밋 기준으로 브랜치 생성
  $ git branch <브랜치 이름> <커밋 ID>
  
  # 특정 브랜치 삭제
  $ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
  $ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
  
  
  # 다른 브랜치로 이동
  $ git switch <다른 브랜치 이름>
  # 브랜치를 새로 생성과 동시에 이동
  $ git switch -c <브랜치 이름>
  # 특정 커밋 기준으로 브랜치 생성과 동시에 이동
  $ git switch -c <브랜치 이름> <커밋 ID>
  ```

- user폴더에 git-branch-practice 폴더 생성

```bash
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice
$ touch README.md
$ git init              #로컬 저장소 만들기
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (master)
$ git add .
$ git status            #파일 상태 확인
On branch master
$ git commit -m "initial README.md-master"
$ git log --oneline                #각 커밋들의 해쉬값 확인
bbf3881 (HEAD -> master) initial README.md-master
```

- 내용 추가

```bash
$ git add "README.md"
$ git commit -m "Update READM+ME.md-master"
$ git log --oneline
0aeff4c (HEAD -> master) Update READM+ME.md-master
bbf3881 initial README.md-master
$ git branch          #브랜치 목록 확인
* master
```

### branch 생성

```bash
$ git branch hotfix    #브랜치 생성
$ git branch
  hotfix
* master
```

### branch 이동(hotfix로)

```bash
$ git switch hotfix
Switched to branch 'hotfix'   #master에서 hotfix로 이동
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (hotfix)
$ git log --oneline           #switch 내역도 확인할 수 있음
0aeff4c (HEAD -> hotfix, master) Update READM+ME.md-master
bbf3881 initial README.md-master
$ git add "README.md"         #hotfix에 내용 추가
$ git status
$ git commit -m "update README-hotfix"
$ git log --oneline
```

### branch 이동(다시 master로)

```bash
$ git switch master
Switched to branch 'master'

장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (master)
```

- 브랜치로 독립적인 공간을 만들었기 때문에 master에서 확인 시, hotfix에서 작성한 건 사라진다.

### 새로운 branch 생성 후 이동, 삭제

```bash
$ git switch -c test               #branch 생성 후 이동
Switched to a new branch 'test'

장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (test)
$ git branch
  hotfix
  master
* test

$ git switch master               #master로 branch 이동
Switched to branch 'master'

장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (master)
$ git branch -d test           #test 삭제
Deleted branch test (was 0aeff4c).

장연화@LAPTOP-OH1IBBHQ MINGW64 ~/git-branch-practice (master)
$ git branch
  hotfix
* master
```

- $ git branch -D test  #병합 전 삭제

```bash
$ touch b.txt
$ git add .
$ git commit -m "add b.txt-master"
$ git log --oneline        #master 것만 나옴(hotfix는 나오지 않음)
17c8a8a (HEAD -> master) add b.txt-master
0aeff4c Update READM+ME.md-master
bbf3881 initial README.md-master
$ git log --oneline --all  #hotfix도 같이 나옴
17c8a8a (HEAD -> master) add b.txt-master
4c20784 (hotfix) update README-hotfix
0aeff4c Update READM+ME.md-master
bbf3881 initial README.md-master
$ git log --oneline --all --graph   #과정이 나옴
```

# Branch Merge

#### Merge의 세 종류

1. Fast-Forward
   - merge 과정 없이 브랜치의 포인터가 이동하는 것

2. 3-Way Merge
   - 브랜치를 병합할 때 `각 브랜치의 커밋 두개와 공통 조상 하나`를 사용하여 병합하는 것
   - 두 브랜치에서 `다른 파일` 혹은 `같은 파일의 다른 부분`을 수정했을 때 가능
3. Merge Conflict
   - 병합하는 두 브랜치에서 `같은 파일의 같은 부분`을 수정한 경우, Git이 어느 브랜치의 내용으로 작성해야 하는지 판단하지 못해서 발생하는 충돌(Conflict) 현상
   - 결국은 사용자가 직접 내용을 선택해 Conflict를 해결



#### ATTRACTION

```bash
$ touch README.md
$ git init
#놀이공원 어트렉션
바이킹
$ git add .
$ git commit -m "first commit"
아틀란티스
$ git add .
$ git commit -m "second commit"
$ git log --oneline --all --graph
* fc63f9f (HEAD -> master) second commit
* 55374dd first commit
$ git diff 55374dd fc63f9f          #git diff 해시값 해시값 - 변경 내용 확인
diff --git a/README.md b/README.md
index e69de29..430d045 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1,3 @@
+#놀이공원 어트렉션
+바이킹
+아틀란티스
\ No newline at end of file
```

user에서 git bash열기

```bash
$ git config --global core.editor "code --wait"
$ git config --global --list
```

```bash
티익스프레스
$ git add .
$ git commit            #edit 가능한 창이 생김
	third commit치고 cltr+s로 저장 후 창을 닫는다
[master a80ab99] third commit
git switch -c water
	물이 있는 놀이기구가 존재하는 water 브랜치를 만들어보자
$ git branch

후룸라이드
$ git add .
$ git commit            #edit 가능한 창이 생김
	first commit water치고 cltr+s로 저장 후 창을 닫는다
[master a80ab99] fist commit water
아마존익스프레스
[water 0966779] second commit water
정글탐험보트
[water 3780657] third commit water

$ git log --oneline --all
3780657 (HEAD -> water) third commit water
0966779 second commit water
5638a5b first commit water
a80ab99 (master) third commit
fc63f9f second commit
55374dd first commit

장연화@LAPTOP-OH1IBBHQ MINGW64 ~/attraction (water)
$ git switch master
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/attraction (master)
$ git log --oneline --all
3780657 (water) third commit water
0966779 second commit water
5638a5b first commit water
a80ab99 (HEAD -> master) third commit
fc63f9f second commit
55374dd first commit

$ git merge water      #water 내용 3개를 (master) 위치에서 병합
$ git branch -d water  #brach 삭제
$ git branch           #master만 남음
```

#### 실습

- merge_practice 폴더 생성


```bash
$ git init
$ touch README.md
	#merge confilct에서
	- 마스터에서 작성
	ctrl+s
$ git add README.md
$ git commit
	first commit-master 후 저장
	
$ git branch test       #test라는 branch 생성
$ git branch            #branch 목록 확인
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/merge_practice (master)
$ git switch test
Switched to branch 'test'
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/merge_practice (test)
	- 테스트에서 작성
	ctrl+s
$ git add .
$ git commit
[test c9457fd] first commit-test

$ git switch master
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/merge_practice (master)
	- 마스터에서 작성 2
$ git add .
$ git commit
[test c9457fd] second commit-master

$ git log --oneline --all --graph
* e883e09 (HEAD -> master) second commit-master
| * c9457fd (test) first commit-test
|/
* 0101d49 first commit-master

$ git merge test
#master와 test 둘다 3번째 줄에 작성된 글이 달라서 생기는 충돌
#compare changes 누르면 master, test commit을 동시에 보여줌
#Accept Both Changes 누르기 -> 병합됨
$ git add .
$ git commit -m "fix conflict"
```

# git workflow

### Feature Branch Workflow 저장소에 소유권이 있는 경우

- 원격 저장소 소유권이 있는 경우 (Shared repository model)

  - 원격 저장소가 자신의 소유이거나 collaborator로 등록되어 있는 경우에 가능합니다.

  - master에 직접 개발하는 것이 아니라, `기능별로 브랜치`를 따로 만들어서 개발합니다.

  - `Pull Request`를 같이 사용하여 팀원 간 변경 내용에 대한 소통을 진행합니다.

    


1. 소유권이 있는 원격 저장소를 로컬 저장소로 **clone** 받습니다.
    `$ git clone https://github.com/edukyle/django-project.git`
1. 사용자는 자신이 작업할 기능에 대한 **브랜치를 생성**하고, 그 안에서**기능을 구현**합니다.
    `$ git switch -c feature/login`
1. 기능 구현이 완료되면, 원격 저장소에 해당 브랜치를 **push** 합니다.
    `$ git push origin feature/login`
1. Pull Request를 통해 브랜치를 master에 반영해달라는 요청을 보냅니다.
(팀원들과 코드 리뷰를 통해 소통할 수 있습니다.)
2. 병합이 완료되면 원격 저장소에서 병합이 완료된 브랜치는 불필요하므로 삭제합니다.
1. master에 브랜치가 병합되면, 각 사용자는 로컬의 master 브랜치로 이동합니다.
    `$ git switch master`
1. 병합으로 인해 변경된 원격 저장소의 master 내용을 로컬에 받아옵니다.
    `$ git pull origin master`
1. 병합이 완료된 master의 내용을 받았으므로, 기존 로컬 브랜치는 삭제합니다. (한 사이클 종료)
    `$ git branch -d feature/login`
1. 새로운 기능 추가를 위해 새로운 브랜치를 생성하며 위 과정을 반복합니다.
    `$ git switch -c feature/pay`



### Froking Workflow 저장소에 소유권이 없는 경우

- 오픈 소스 프로젝트와 같이, 자신의 소유가 아닌 원격 저장소인 경우 사용합니다.

  - 원본 원격 저장소를 그대로 내 원격 저장소에 `복제`합니다. (이 행위를 `fork`라고 합니다.)
- 기능 완성 후 `Push는 복제한 내 원격 저장소에 진행`합니다.
  - 이후 `Pull Request`를 통해 원본 원격 저장소에 반영될 수 있도록 요청합니다.




1. 소유권이 없는 원격 저장소를 fork를 통해 내 원격 저장소로 복제합니다.

2. fork 후, 복제된 내 원격 저장소를 로컬 저장소에 clone 받습니다.

   `$ git clone https://github.com/edukyle/kakao_clone.git`

​	3.이후에 로컬 저장소와 원본 원격 저장소를 동기화 하기 위해서 연결합니다.

​		\# 원본 원격 저장소에 대한 이름은 upstream으로 붙이는 것이 일종의 관례

​		`$ git remote add upstream https://github.com/AlexKwonPro/kakao_clone.git`

4. 사용자는 자신이 작업할 기능에 대한 브랜치를 생성하고, 그 안에서 기능을 구현합니다.

​		`$ git switch -c feature/login`

5.  기능 구현이 완료되면, 복제 원격 저장소(origin)에 해당 브랜치를 push 합니다.

​		`$ git push origin feature/login`

 6. 복제 원격 저장소(origin)에는 master와 브랜치가 반영되었습니다.

 7. `Pull Request`를 통해 `복제 원격 저장소(origin)의 브랜치`를 `원본 원격 저장소(upstream)의 master`에 반영해달라는 요청을 보냅니다. (원본 원격 저장소의 관리자가 코드 리뷰를 진행하여 반영 여부를 결정합니다.)

 8. 원본 원격 저장소(upstream)의 master에 브랜치가 병합되면 복제 원격 저장소(origin)의 브랜치는 삭제합니다. 그리고 사용자는 로컬에서 master 브랜치로 이동합니다. 

     `$ git switch master`

 9. 병합으로 인해 변경된 `원본 원격 저장소(upstream)의 master` 내용을 로컬에 받아옵니다. 그리고 기존 로컬 브랜치는 삭제합니다. (한 사이클 종료)
    `$ git pull upstream master`
    `$ git branch -d feature/login`
    
 10. 새로운 기능 추가를 위해 새로운 브랜치를 생성하며 위 과정을 반복합니다.

​		`$ git switch -c feature/pay`



#### 실습

1.  원본(upstream) -fork-> 복제(origin) [hwas2/acrostic-poem](https://github.com/hwas2/acrostic-poem.git)

2. git bash에서 

```bash
장연화@LAPTOP-OH1IBBHQ MINGW64 ~
$ git clone https://github.com/hwas2/acrostic-poem.git
Cloning into 'acrostic-poem'...

$ cd acrostic-poem/
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/acrostic-poem (master)
code .           #vscode 오픈
```

- 원본 -pull -> user(master)

3. 수정 > 저장 
4. add 
5. commit 
6. git push origin 브랜치명

```bash
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/acrostic-poem (master)
$ git branch hwas2
$ git switch hwas2

	백일장 수정
장연화@LAPTOP-OH1IBBHQ MINGW64 ~/acrostic-poem (hwas2)
$ git add .
$ git commit
[hwas2 80cea4e] 백일장 추가 yeonhwa
$ git push origin hwas2
```

- github에서 Pull Request 버튼 2번 눌러 PR 보내기
  - compare & pull request -> Create pull request