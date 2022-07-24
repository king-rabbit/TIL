# file system

- 리눅스 시스템에서는 디렉토리 등 모든 것이 파일임. 파일이 아니라면 프로세스.
- root : / 모든 디렉토리와 파일이 포함된 최상위 디렉토리.

### Filesystem Hierarchy Standard

- /bin : binaries, user executable files. 명령어의 실행 파일. 특히 시스템과 관련된 중요도가 높은 명령어 포함.
- /sbins : 슈퍼유저만 접근가능한 applications
- /boot : 시스템을 부팅하는 데 필요한 파일들
- /home : 각 유저의 home 디렉토리가 모아져 있는 곳. (root 유저의 홈 디렉토리는 /root)
    - ‘~’는 로그인한 유저의 home 디렉토리와 같음.
- /dev : 디바이스 파일들.
- /etc : 대부분의 설정 파일들.
- /lib : 여러 어플리케이션들의 라이브러리 파일들
- /media : 자동으로 mount된 외부 저장소(usb 등)
- /mnt : /media처럼 외부 저장소 폴더이나 최근 잘 사용되지 않음.
- /proc : 메모리나 cpu에 대한 데이터 저장
- /sys : 디바이스와 케널 등에 대한 정보
- /srv : 서버 데이터
- /run : RAM용 임시 데이터
- /usr : 바이너리 파일, shared libraries 등. 우분투나 CentOS에서는 /bin과 /sbin 대신 /usr/bin 과 /usr/sbin에 많은 명령어가 저장되어 있음.
- /var : 로그 파일.

### Absolute path vs. Relative path

- cd : 해당 디렉토리로 이동
- pwd : 현재 디렉토리를 표시
- absolute path : 절대 주소. 항상 / 로 시작함.
- . : 현재 디렉토리
- .. : 부모 디렉토리

### ls command

- 폴더에 있는 파일 리스트 출력
- ls 폴더 경로
- ls -1 : 파일을 한줄로 출력
- ls -l : 파일 상세 정보 함께 출력
    - 첫 컬럼으로 파일의 종류 확인: -면 일반 파일, d면 폴더, l이면 symbolic link
    - 3,4번째 컬럼은 소유자
    - 5번째 컬럼은 파일 크기
    - 6번째 컬럼부터는 파일 수정 일자 및 시각
- ls -lh : 파일 사이즈의 단위와 함께 출력
- ls -d : 폴더 정도만 출력
- ls -la : 숨긴 파일도 모두 출력
- ls -lhS: 파일을 크기 순으로 출력
- sudo du -sh 폴더 경로 : 폴더 사이즈 출력
- ls -l -X : extention 순으로 정렬
- ls —hide=*.conf 폴더 경로 : .conf로 끝나는 파일은 출력 제외
- ls -lR: reculsively하게 출력. 즉, 해당 폴더 아래에 있는 서브 폴더에 있는 파일도 모두 출력.

### File Timestamps

- atime : access timestamp. 파일이 읽힌 마지막 시각.(ls -lu)
- mtime: 파일 내용이 변경된 마지막 시각.(ls -l, ls -lt)
- ctime: 파일의 메타 데이터가 변경된 마지막 시각.(ls -lc)
- 리눅스 파일 시스템은 1970년 1월 1일 자정을 기점으로 시간을 계산
- stat 파일 경로 : 파일에 대한 통계 제공
- touch 명령어: 파일 시간을 바꾸거나 해당 이름의 파일이 없으면 그 이름을 가진 empty 파일을 만듬