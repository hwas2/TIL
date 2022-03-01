# Git 설치

**Windows (윈도우)**

- Git 설치 후 윈도우 탐색기를 엽니다. (`윈도우키 + e`)
- `C:/사용자(Users)/현재 사용자 계정` 로 이동합니다.
- 폴더 내 빈 공간에서 마우스 우클릭 후 `Git Bash Here`를 클릭합니다.
- Git Bash 창에 HOME 폴더를 의미하는 `~` 표시만 있다면 정상입니다.



# CLI

- CLI VS. GUI
  - `GUI (Graphic User Interface)` : 그래픽을 통해 사용자와 컴퓨터가 상호 작용하는 방식
  - `CLI (Command Line Interface)` : 터미널을 통해 사용자와 컴퓨터가 상호 작용하는 방식

- CLI를 사용하는 이유

  `new` 라는 이름으로 새 폴더를 생성해 봅시다.

  1. GUI를 사용하는 경우 (4단계) : `마우스 우클릭 → 새로 만들기 → 폴더 → new 작성`
  2. CLI를 사용하는 경우 (1단계) : `mkdir new`

  GUI는 CLI에 비해 사용하기 쉽지만 단계가 많고 컴퓨터의 성능을 더 많이 소모합니다.

  그리고 CLI는 GUI로는 불가능한, 많은 세부적인 기능을 사용할 수 있습니다.

- Git Bash 사용 이유?

  - **명령어의 통일을 위해.**  `Git Bash`라고 하는 일종의 번역기를 통해 Windows에서도 UNIX 계열 운영체제의 터미널 명령어를 사용하기 위함입니다.

  - **UNIX 계열 운영체제의 명령어를 더 많이 쓰기 때문입니다.**



# 경로

## 디렉토리

1. **루트 디렉토리 (Root Directory, `/`)**
   - 모든 파일과 폴더를 담고 있는 최상위 폴더
   - Windows의 경우 보통은 `C 드라이브`를 의미
2. **홈 디렉토리 (Home Directory, `~`)**
   - `Tilde(틸드)`라고도 부르며, 현재 로그인 된 사용자의 홈 폴더를 의미
   - Windows의 경우 `C:/사용자(Users)/현재 사용자 계정`을 의미

## 절대/상대 경로

1. 절대 경로

    : 루트 디렉토리부터 목적 지점까지 거치는 모든 경로를 전부 작성한 것

   - 윈도우 바탕 화면의 절대 경로 `C:/Users/kyle/Desktop`

2. 상대 경로

    : 현재 작업하고 있는 디렉토리를 기준으로 계산된 상대적 위치를 작성한 것

   - 현재 작업하고 있는 디렉토리가 `C:/Users` 라고 한다면
   - 윈도우 바탕 화면으로의 상대 경로는 `kyle/Desktop` 이 됩니다.
   - 간결해서 좋지만, 현재 작업하고 있는 디렉토리가 변경 되면 상대 경로도 변경됩니다.
   - `./` : 현재 작업하고 있는 폴더를 의미합니다.
   - `../` : 현재 작업하고 있는 폴더의 부모 폴더를 의미합니다.


# 커맨드라인 명령어(터미널 명령어)
```bash
# make directory 폴더 생성
mkdir 폴더명

# change directory 디렉토리 이동
cd folder # 현재 작업 중인 디렉토리에 있는 folder 폴더로 이동
cd C:/Users/kyle/Desktop # 절대 경로를 통한 디렉토리 변경
cd ../parent/child # 상대 경로를 통한 디렉토리 변경
`cd ~` 홈 디렉토리로 이동
`cd ..` 부모 디렉토리로 이동 (위로 가기)
`cd -` 바로 전 디렉토리로 이동 (뒤로 가기)

# list segments 디렉토리 안에 있는 리스트 확인
ls : 기본
ls -a : all 옵션
ls -a -l : all, long 옵션(용량, 수정 날짜 등 파일 정보를 자세히)
ls -al : 여러 옵션 축약 가능

# 파일 생성
touch 파일명

# remove 폴더/파일 제거
rm 폴더/파일
되도록 gui 환경을 이용
-r 옵션 : 재귀적으로 폴더 하단 내역도 삭제
-rf 옵션 : 강제삭제 옵션

# move 이동/이름변경
mv
	1)파일을 해당 위치로 이동
	 mv 대상파일 이동위치
	2) 이동위치가 없을 때, 파일의 이름 변경
	 mv 대상파일 변경이름

# present working directory 현재 경로 확인
pwd

# 화면 깨끗이/스크롤 올리기
(window) ctrl + l
(mac) clear

#복사
ctrl + insert
#붙여넣기
shift + insert

# 커서가 맨 앞으로 이동
ctrl + a
#커서가 맨 뒤로 이동
ctrl + e
#커서가 앞 단어를 삭제
ctrl + w

#폴더/파일을 여는 명령어
(window) start
(mac) open
```