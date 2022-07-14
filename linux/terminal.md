# terminal

### 우분투에서 터미널 열기

- Ctrl + Option + T
- 바탕화면에서 오른쪽버튼 > Open in Terminal

### root user vs. Non-previleged Users

- root 유저: 새 프로그램 설치, 새 유저 생성 등 administrative task를 실행 가능. 일반적인 task 실행 시에는 root 유저를 사용하지 않는 것이 좋음.
- sudo : super-user-do의 약자
    - sudo su: 일시적으로 root 유저 계정 사용 (→ exit 명령으로 로그아웃)
    - sudo groupadd myadmin: 새 유저 그룹 생성
    - sudo useradd john: 새 유저 생성
    - sudo passwd root: 비밀번호 변경

### 터미널 주요 Shortcuts

- 명령문을 일부 작성한 뒤 TAB을 누르면 자동완성할 수 있다.
- Ctrl + a: 명령문 작성 중 커서를 맨 앞으로 이동시킨다
- Ctrl + e: 명령문 작성 중 커서를 맨 뒤로 이동시킨다
- Ctrl + u: 작성중인 명령문을 모두 삭제한다
- Ctrl + c: 진행 중인 명령문을 중단시킨다

### 주요 명령문들

- ls (list) : 폴더 및 파일 리스트 반환
- cat: 파일의 텍스트를 모두 출력
    - cat .bash_history: bash에서 작성한 명령문을 모두 출력
- history: 명령문 히스토리를 모두 출력
    - echo HISTTIMEFORMAT = ‘%d/%m/%y %T’ >> .bashrc : 명령문 히스토리의 시간 포맷을 정해줌 → 이후 history 명령문 실행하면 시간도 같이 출력
    

### 패키지 매니저

- 프로그램을 다운로드/설치/제거 등을 담당하는 게 패키지 매니저
- 대표적인 패키지 매니저: apt / yum
- 패키지에서 최신상태 소프트웨어 목록 다운로드
    - sudo apt-get update
- 소프트웨어 검색
    - sudo apt-cache search 검색어
- 소프트웨어 다운로드
    - sudo apt-get install 프로그램명
- 소프트웨어 업그레이드
    - sudo apt-get upgrade 프로그램명
    - 프로그램명을 입력하지 않으면 업그레이드 가능한 모든 프로그램에 대해 업그레이드 진행
- 소프트웨어 제거
    - sudo apt-get remove 프로그램명

## Shell

### Shell vs. Kernel

- 커널: 하드웨어를 직접 제어
- 쉘: 유저의 명령어를 해석해서 커널에게 전달
- 대표적인 쉘 프로그램: bash, zsh
- echo $0 : 현재 사용하고 있는 쉘 확인