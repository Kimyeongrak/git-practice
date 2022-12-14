Git Practice
============
Git 설정 & 프로젝트 관리 시작하기
-----------------------------
***

Git 전역으로 사용자 이름과 이메일 주소를 설정

- GitHub 계정과는 별개

터미널 프로그램 (Git Bash, iTerm2)에서 아래 명령어 실행

`git config --global user.name "(본인 이름)"`

`git config --global user.email "(본인 이메일)"`

아래 명령어들로 확인할 수 있다.

`git config --global user.name`

`git config --global user.email`
***
Git 에게 맡기지 않을 것들
----------------------
### 1. Git 의 관리에서 특정 파일/폴더를 배제해야 할 경우
#### a. 포함할 필요가 없을 때
- 자동으로 생성 또는 다운로드되는 파일들 (빌드 결과물, 라이브러리)
#### b. 포함하지 말아야 할 때
- 보안상 민감한 정보를 담은 파일

### **.gitignore** 파일을 사용해서 배제할 요소들을 지정할 수 있다.   
`example`   
   
**#모든 file.c**

- `file.c`

**#최상위 폴더의 file.c**

- `/file.c`

**#모든 .c 확장자 파일**

- `*.c`

**#.c 확장자지만 무시하지 않을 파일**

- `!not_ignore_this.c`

**#logs란 이름의 파일 또는 폴더와 그 내용들**

- `logs`

**#logs란 이름의 폴더와 그 내용들**

- `logs/`

**#logs 폴더 바로 안의 debug.log 와 .c 파일들**

- `logs/debug.log`

- `logs/*.c`

**#logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log**

- `logs/**/debug.log`
***
변화를 버전에 담아 묻기
----------------------
### 1.프로젝트의 변경사항들을 버전에 담기
**변경사항 확인**   

`git status`   
- 추적하지 않는(untracked) 파일 : Git 의 관리에 들어간 적 없는 파일

**파일 하나 담기**   

`git add tigers.yaml`   
- ###### `git status` 로 확인

**모든 파일 담기**

`git add .`
- ###### `git status` 로 확인

### 2. 버전 묻기   

`git commit`
- Vi 입력 모드로 진입
- 
  | 작업                |         Vi 명령어          | 상세                                         |
  | :------------------ | :------------------------: | -------------------------------------------- |
  | 입력 시작           |             i              | 명령어 입력 모드에서 텍스트 입력 모드로 전환 |
  | 입력 종료           | ctrl + space bar(intelliJ) | 텍스트 입력 모드에서 명령어 입력 모드로 전환 |
  | 저장 없이 종료      |             :q             |                                              |
  | 저장 없이 강제 종료 |            :q!             | 입력한 것이 있을때 사용                      |
  | 저장하고 종료       |            :wq             | 입력한 것이 있을때 사용                      |
  | 위로 스크롤         |             k              | `git log` 등에서 내역이 길 때 사용           |
  | 아래로 스크롤       |             j              | `git log` 등에서 내역이 길 때 사용           |
- FIRST COMMIT 입력한 뒤 저장하고 종료   

**커밋 메시지까지 함께 작성하기**   
- `git commit -m "FIRST COMMIT"`   

**아래 명령어로 확인**
- `git log`   
- 종료는`:q`

### 3. 다음 변경사항들 만들고 버전에 묻기

변경사항
- `lions.yaml` 파일 삭제
- `tigers.yaml` 의 manager 를 `Donald` 로 변경
- `leopards.yaml` 파일 추가
***
***
😅 알게된 내용
- 작업했던 내용을 github 에 push 하는법
  - intelliJ terminal 에서 $ git push 명령어 사용하면 원격저장소에 적용
- .gitignore 적용하기
  - 원격저장소에 올라가 노출되어 있는 `.idea folder`, `secrets.yaml`을 .gitignore 에 추가하여 노출하지 않도록 조치하려고함. 
    - 필요한 작업 : 이미 push 된 file .gitignore 적용
      - `.gitignore` 에 `/.idea/`, `secrets.yaml` 을 추가함
      - `$ git rm -r --cached .` // `$ git rm <fileName>`, `$ git rm --cached <fileName>`
        - `$ git rm` : 원격 저장소와 로컬 저장소에 있는 파일을 삭제한다.
        - `$ git rm --cached` : 원격 저장소에 있는 파일을 삭제한다. 로컬 X.
      - `$ git add .`
      - `$ git commit -m "Apply .gitignore"`
      - `$ git push`
      - 명령어 적용.
***
***
