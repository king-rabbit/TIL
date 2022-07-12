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