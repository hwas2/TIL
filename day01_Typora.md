# 마크다운

- 마크다운과 마크업
  - 마크업 : html -> 개발자 도구로 확인 (태그)
  - 마크다운 : 경량화된 마크업 언어

- 마크다운 역할
- 마크다운 문법


# 제목

- #을 이용하여 제목을 표현

- 수준 1#-6######까지

## 제목2

### 제목3

#### 제목4

---

# 목록
- 순서가 있는 목록

1. `1.` `2.` `3.`을 통해 작성
2. 숫자 뒤에는 꼭 `띄어쓰기` 포함되어 있어야 한다.
3. shift+tab을 통해 내어쓰기 가능


- 순서가 없는 목록
  - `-`, `+`, `*` 를 통해 작성
  - tab을 통해 들여쓰기 가능

---

# 강조

- 글자의 스타일링
  - 기울임 : `*글자* 혹은 _글자_`
  - **굵게 : **`** 글자**` 혹은 `__글자__`
  - ***기울이고 굵게*** : \*\*\*글자***
  - ~~취소선~~ : `~~글자~~`
  - <u>밑줄</u> : `<u>밑줄</u>`

---

# 코드(code)

- `인라인 코드` : '한줄 코드'를 백틱(\`)으로 묶어줍니다.
- 블록 코드 : 여러줄 코드 ``` 3개짜리 백틱 묶음으로 묶어줍니다. 

```python
#python
print("hello git!")
```

```markdown
markdown
# 제목1
- 목록
**굵게**
```

```bash
bash
touch a.txt
```

---

# 링크

- `[표시글자](이동할주소)`

[Git 특강 메인 페이지](https://hphk.notion.site/hphk/Git-5-_E-22-02-23-22-02-25-1b97e73779554044b56f15cd57693e9a)

---

# 이미지

- `![대체할 텍스트](이미지 주소)
  - 대체 택스트란? 이미지를 정상적으로 가져오지 못하였을 때 표시

![파이썬 로고](https://ncc-phinf.pstatic.net/20160921_117/1474417831859Oe6xy_PNG/01.png?type=w646)

---

# 인용

- 주석 혹은 인용문을 작성할때 사용
- `>`를 사용하여 인용

> 인용문을 작성1
>
> > 중첩1
> >
> > > 중첩2
>
> shift+tab

---

# 수평선

- `---`,`***`,`___`

  ---

  ***

  ___

---

# 표

- 테이블은 파이프(|), 하이픈(-)을 이용하여 행, 열 구분
  - 본문 > 표> 표삽입, ctrl+T

| 시간표 | 1일차     | 2일차 |
| ------ | --------- | ----- |
| 1교시  | git intro |       |
| 2교시  | CLI       |       |
| 3교시  | vscode    |       |

---