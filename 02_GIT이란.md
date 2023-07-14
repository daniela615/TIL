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

### git 폴더로 만들려는 폴더 안에서 ```git init```만 쓰면 됨
### 잘 되었는지 보려면 ls -d .git을 쳐서 .git/이라는 숨김파일 생성되었으면 ok
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

* ```git remote add [저장소 이름] [저장소 주소]``` : git remote add origin https://github.com/daniela615/intro.git	
  * git에게 원격저장소(remote) 추가(add)를 명령

* 저장소 이름: ```origin```
* 저장소 주소: https://github.com/daniela615/intro.git

* 저장소 삭제: ```git remote remove [저장소 이름]```

  

### (8) ``` git push```

* ```git push [저장소 이름] [브랜치 이름]``` : git이 관리하는 디렉토리에 있는 파일들을 github에 올려 저장하기
* ```[브랜치 이름]``` 은 브랜치가 따로 없는 경우 그냥 master 쓰면 됨.  



### (9) ```git clone [저장소 주소]```

* 다른 사람의 git 폴더에서 같이 협업하기 위해 다른 사람의 폴더 연결하기. 어느 디렉토리 밑에 넣을건지 잘 보고 치기!
* 혹시 디렉토리 잘못 넣었다면 그냥 ```rm -rf  [저장소 이름]```으로 폴더 자체를 삭제하면 됨.
* ```git clone```으로 폴더를 가져왔을 때는 이미 remote 되어있으므로 ```remote add``` 할 필요 없음.
* ```git remote -v```로 확인해보면 주소에 이미 폴더 원 소유자 주소로 등록된 것을 볼 수 있음
* 원 소유자는 팀원한테 나눠준 폴더(repo)를 팀원이 쓸 수 있게 권한을 줘야 함. github - setting - (왼쪽) collaborators - 비밀번호 재입력 - 팀원 아이디나 이메일로 검색해서 추가하기 - 팀원한테 메세지나 이메일이 가는데, 혹시 팀원이 메세지를 놓쳤다면 내가 보낸 메시지에서 pending invite를 복사해서 링크를 줘도 됨. 수락하고 나면 초대한 사람 이름 밑의 상태가 'Collaborator'로 바뀜.



### (10) ```git pull```

* ```git pull [저장소 이름] [브랜치 이름]``` 으로 팀원이 github에 push했지만 아직 나에게는 없는 파일을 끌어와서 동기화시킬 수 있음.

​	