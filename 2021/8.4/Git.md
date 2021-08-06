# Git

> - 분산버전관리시스템(DVCS)
> - 원격 저장소를 통하여 모든 버전 히스토리 받아옴
> - 공유를 통한 이식 용이
> - git bash툴로 조작

`workingdirectory --add--> staging area --commit-->`

- workingdirectory : 트래킹되고 있지 않은파일

- stating area : 커밋 대상파일들 모아두는 곳
  -> qa나 테스트하는 사람이 이서버에서 테스트함
  
- trakced : 이전부터 버전으로 관리되고 있는 파일

  - unmodified : git status로 안보임

  - modifeid : 수정된 파일
  - staged : staged로 넘어간 파일

- untracked : 버전으로 관리된적 없는 파일 (파일을 새로만드는 경우)

___

## 기본 커맨드

### ls
- list,  현재 경로 목록 출력
### touch ""
- 현재 경로에 해당 파일 생성 
### pwd
-  print working directory, 현재 위치 경로 출력
### mkdir ""
- make directory, 현재 경로에 해당이름 폴더 생성 
### cd ""
- change directory, 해당 경로로 이동

- ""대신 ..은 하나위 상위 폴더로 이동

- ""대신 .은 현재 디렉토리로 이동
___

## Git 관련 커맨드
### git init
- 현재 디렉토리에 git 저장소(repository)만듬 
- git으로 관리- 버전기록 -> 초기화
### git status
- 현재 디렉토리 정보 확인
### git add ""
- 현재 디렉토리 파일을 커밋할 폴더에 추가 (뒤에 연결해서
  여러개 커밋 가능)
- ""대신 .만 붙이면 현재 디렉토리 파일 전체를 한꺼번에 add
- 폴더째로 add 가능
### git commit -m ""
- ""이름 버전으로 커밋
- add 했던 것들이 ""이름으로 합쳐져 커밋됨, 즉 분류 기준
  -->관리 분류 중요
- 확장자 안붙여도됨
### git log
- 현재 저장소에 기록된 커밋버전들을 조회
___
### git config --global user.name ""
- ""에 git 아이디, 사용자 설정
- 처음 한번만 설정해놓으면 유지
### git config --global user.email ""
- ""에 git 이메일, 사용자 이메일 설정
- 처음 한번만 설정해놓으면 유지
### git config --unset --global user.name 
- 설정된 사용자 이름 제거
### git config --unset --global user.email
- 설정된 사용자 이메일 제거
### git config -l
- 사용자 확인
### git clone ""
- ""저장소의 주소에 내용을 클론해온다.
### git remote add origin ""
- ""원격저장소 주소와 연결
- 한번 origin으로 추가되면 다시 추가할 필요 없음. 
- add대신 rm넣으면 origin 설정 제거됨, 이때는 주소 작성x
### git remote -v
- 현재 연결된 원격저장소 주소 확인
### git remote set-url origin ""
- ""원격저장소 주소로 주소 변경
### git push origin ""
- ""branch에 커밋한 파일들을 push
- origin은 원격저장소 이름이나 보통 안바꿈
- ""에는 보통 master 아니면 main, 요즘은 main
___
## 기타

- git bash에 복붙할때는 마우스 오른쪽paste로
- 로컬 저장소마다 대응되는 원격저장소를 개별 마련
- 이름은 .이나 띄워쓰기 특수문자 자제
- GUI(그래픽 유저 인터페이스, 일반윈도우화면)
  오류는 팝업, 변경은 클릭으로 가능
- CLI (커맨드라인 인터페이스, cmd등)
  명령은 줄 단위, GUI처럼 그래픽 처럼 안내가 없음

