# GIT

GIT은 분산 버전 관리 시스템(Distributed Version Control System)입니다. 소프트웨어 개발에서 버전 관리는 개발자들이 소스 코드의 변경 이력을 관리하고 추적할 수 있도록 도와줍니다.

프로젝트(폴더) 기반 코드 관리 도구

* 코드 관리도구
* 코드 협업도구
* 코드 배포도구



## GIT 명령어

```git [명령어]```



### (1) ```git init```

GIT으로 특정 폴더(프로젝트) 관리 시작

```
$ git init
Initialized empty Git repository in C:/Users/daniela/intro/.git/
```

* 코드 관리 단위(기준): 폴더
* ```(master)``` : ~~현재 브랜치명~~
* ```.git``` 폴더 생성: git 관리와관련된 파일 
*  git으로 프로젝트 관리를 중단:  ```.git``` 디렉토리 삭제



### (2) ```git status ```

GIT의 현재 상태를 출력(GIT에게 현재 상태를 물어봄)

* ```git init``` 직후,

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

### 아직 commit 이 없고, commit 할 것도 없음
### commit이란 현재 상태를 스냅샷처럼 저장해놓는 기능. commit 별로 버전 관리가 가능. 이전 commit으로 돌아가기도 가능.
### $ git status를 치면 마지막 commit 이후 현재까지 바뀐 내용들을 출력해 줌.

```

* ```touch a.txt``` 파일 추가 후,

```
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        a.txt

nothing added to commit but untracked files present (use "git add" to track)

### commit 하기 위한 파일이 추가되지 않았음, 그러나 추적되지 않은 파일이 존재함.

```

* ```git add a.txt```직후,

```
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   a.txt

### a.txt를 git이 관리하기 시작.
### ```git rm --cached a.txt```라고 쓰면 git이 관리하는 파일 목록에서만 사라짐. 파일이 삭제되는 것은 아님.
```

* ```git commit``` 이후,

```
nothing to commit, working tree clean

### commit 할 게 없음.
```

* 파일 수정 후,

```
On branch master

Changes not staged for commit:

	(use "git add <file>..." to update what will be committed)
	(use "git restore <file>..." to discard changes in working directory) modified: test.txt

no changes added to commit (use "git add" and/or "git commit -a")

### commit하기 위해 stage 되지 않은 변경 사항이 있어요.
```



### (3) ```git add [파일/폴더]```

commit을 위한 stage

* ```git add .``` : 현재 폴더의 모든변경 사항 stage

 

### (4) ```git commit -m "커밋메시지"```

> commit == 버전을 생성 == 현재 상태의 스냅샷 촬영

* GIT 커밋은 '현재 시점'을 저장하는 것.  

```
$ git commit -m ["커밋명"]
[master (root-commit) ef6e3be] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```

* 만약 최초 commit 실행 시 이메일과 유저네임을 등록하지 않았다면 아래와 같은 오류. 이메일과 유저 네임 추가하고 다시 실행하면 됨.

```
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

```

* 아래와 같이 작성
  * git config --global user.email [나의 이메일 ]: global(전역으로) user의 email을 설정
  * git config --global user.name [나의 이름]

* ```git config``` 설정 후( ```vim``` 에디터 창),

```
# Please enter the commit message for your changes.
-> 변경사항에 대한 commit message를 입렵해주세요.
# Lines starting with '#' will be ignored, and an empty message aborts the
commit.
-> #로 시작하는 라인은 무시됩니다. 아무것도 없는 메시지는 종료됩니다.
# On branch master
#
# Initial commit
#
# Changes to be committed:
# new file: test.txt
```



### (5) ```git config```

Git에 관한 설정

* git config --global user.email "이메일" : global(전역으로) user의 email을 설정
* git config --global user.email : 설정값 확인



### (6) ```git log```

현재까지의 commit을 출력

* git log 출력화면

```
commit 1a7d9384d2f9a064e2ddb4719306defeb51ac3cf (HEAD -> master)
Author: John Kang <hphk.john@gmail.com>
-> 작성자
Date: Tue Mar 16 15:55:10 2021 +0900
-> 날짜
first commit
-> 커밋 메시지
```

* ```git log --oneline``` : 한줄로 출력

```
7c7abf0 (HEAD -> master) Add title
1a7d938 first commit
```



### (7) ```git remote```

* ```git remote add [저장소 이름] [저장소 주소]``` : git remote add origin https://github.com/hkeryfonttlxisdrlw/basic_git
  * git에게 원격저장소(remote) 추가(add)를 명령

* 저장소 이름: ```origin```
* 저장소 주소: https://github.com/hkeryfonttlxisdrlw/basic_git