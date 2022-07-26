# 기본 명령어

### 디렉터리 만들기: mkdir

- mkdir 이름 : 해당 이름의 디렉터리 생성
- 중첩된 디렉터리 한번에 만들기: -p 옵션

```jsx
mkdir -p report/2021/05
```

### 파일 만들기 : touch

- touch 파일이름1 파일이름2 … : 파일 이름들에 해당하는 파일 생성. 빈파일들.
    - 이미 존재하는 파일을 지정해도 내용이 지워지지는 않음.
    - 파일의 타임스탬프를 갱신하는 명령어인데 파일이 존재하지 않는 경우 새 파일을 생성.
    

### 파일 또는 디렉터리 삭제 : rm, rmdir

- rm 파일이름1 파일이름2 … : 해당 파일들을 삭제
- rm -r 디렉터리이름 : 디렉터리 삭제. 이때 디렉터리 내부 파일도 모두 삭제됨.
- 주의: 리눅스에서는 파일이 휴지통으로 이동하지 않고 곧바로 삭제됨.
- rm -i 파일이름 : 파일 삭제 확인 메시지 출력
- rmdir 디렉터리이름 : 빈 디렉터리 삭제하기

### 파일 내용 출력하기 : cat

- 호스트 이름 설정 파일 출력하기

```bash
$ cat /etc/hostname
```

- 인자로 여러 파일 지정하면 순차적으로 내용 출력함

```bash
$ cat /etc/hostname /etc/crontab
```

- -n 옵션: 행 번호 표시하는 옵션

```bash
$ cat -n /etc/crontab
```

- 아무것도 인자로 지정하지 않으면 이후 작성한 내용을 출력
    - Ctrl + d 입력 시 cat 명령어 종료됨.

```bash
$ cat
Hello
```

### 스크롤 표시하기: less

- 파일을 화면 단위로 출력하며 위아래로 스크롤 하면서 파일을 볼 수 있게 해 주는 명령어

```bash
$ less /etc/bash.bashrc
```

- 단축키
    - space, f, ctrl+v: 한 화면 아래로 이동
    - b, Meta + v: 한 화면 위로 이동
    - j, ctrl+n, enter: 한 행 아래 이동
    - k, ctrl+p : 한 행 위로 이동
    - q : 명령어 종료
- 문자열 검색하기
    - less로 파일 출력한 상황에서 입력란에 ‘/검색문자열'을 입력하면 파일에서 검색 실행
    - ?문자열은 위 방향으로 검색, /문자열은 아래 방향으로 검색
    - n: 다음 검색 결과로 이동
    - N: 이전 검색 결과로 이동
    

### 파일, 디렉터리 복사하기: cp

```bash
$ touch file1
$ cp file1 file2 <- 파일 다른 이름으로 복사
$ cp file1 dir1 <- 파일을 특정 디렉터리 안에 복사
$ cp file1 file2 file3 dir2 <- dir2 디렉터리 안에 파일1, 파일2, 파일3 복사
$ cp -r dir2 dir3 <- 디렉터리 복사 시 -r 옵션 필요
```

- cp file이름1 filed이름2: 이름1 파일을 복사하고 복사된 파일의 이름은 이름2로 지정
- 복사 시 이미 같은 이름의 파일이 있으면 덮어씀

### 파일 이동하기 or 이름 변경: mv

```bash
mv <이동할 파일> <이동할 위치>
```

- 파일 이름 바꾸기: 이동할 파일과 이동할 위치에 모두 파일명을 지정하면 파일 이름이 변경됨!!

```bash
$ mkdir mvtest <- 테스트용 디렉터리 만들기
$ cd mvtest
$ touch file1 <- 테스트용 파일 생성
$ mv file1 file2 <- 파일 이름 바꾸기
$ ls 
file2
```

- 파일을 디렉터리 안으로 옮기기

```bash
$ mkdir dir1
$ mv file1 dir1
$ ls dir1
file1
$ touch file1 file2 file3
$ mv file1 file2 file3 dir1 <- 3개 파일을 모두 dir1 디렉터리로 옮김
```

- 디렉터리 옮기기: 별도의 옵션 필요 없음

```bash
$ mkdir dir2
$ mv dir1 dir2 <- dir1을 dir2 디렉터리 안으로 옮김
```

### 링크 만들기: ln

- 링크: 파일에 별명을 붙이는 것. 별명 붙이기 = 링크 생성
    - 하드 링크
        
        ```bash
        $ cp /etc/crontab file1 <- crontab 파일을 file1에 복사
        $ ln file1 f1 <- 하드링크 f1 만들기
        ```
        
        - 한 파일의 원본에 이름을 여러개 붙이는 기능
        - 하드 링크에 접근하면 원래 파일에 접근하는 것과 동일.
        - 원본과 하드 링크로 만든 파일 모두 원본임!!
        - 하드링크를 삭제하면 해당 하드 링크만 삭제되고 나머지는 남아있음.
        - 디렉터리는 하드 링크할 수 없음.
        - 서로 다른 디스크에 걸쳐 하드 링크를 만들 수 없음.
    - 심볼릭 링크: 주로 쓰이는 링크는 심볼릭 링크. -s 옵션으로 만든다.
        
        ```bash
        $ cp /etc/crontab file1
        $ ln -s file1 f1 <- 심볼릭 링크 생성.
        $ ls -l <- -l 옵션으로 심볼릭 링크 여부 확인
        $ rm f1 <- 심볼릭 링크 삭제
        ```
        
        - 심볼릭 링크란 원본 파일에 대한 정보가 담긴 작은 특수 파일
        - 원본과 구별됨.
        - 심볼릭 링크를 삭제해도 원본에는 영향 없음.
        - 심볼릭 링크를 지우지 않은 채 원본을 지우면 심볼릭 링크가 깨진 상태가 됨.
    

### 파일 찾기: find, locate

### find

- 디렉터리 트리에서 파일을 찾는 명령어

```bash
find <검색할 디렉터리> <검색 조건> <액션>

$ find . -name file-1.txt print <- file-1.txt 파일명으로 검색
```

- 지정한 디렉터리 트리를 내려가면서 검색 조건에 일치하는 파일을 검색 ㄹ
- 검색 조건
    - 이름으로 검색
        - -name(대소문자 구별), -iname(대소문자 구별 없음)
        - 이름 지정 시 *나 ?를 사용할 때는 ‘*.txt’처럼 작은 따옴표로 감싸줘야 함.
    - 파일 형식으로 검색
        - -type f : 보통 파일
        - -type d : 디렉터리
        - -type l : 심볼릭 링크
    
    ```bash
    $ find . -type d -print
    ```
    
    - 검색 조건 여러개 지정하기: -a 옵션 사용
    
    ```bash
    $ find . -type f -a -name '*.txt' -print <- 파일 형식이 일반 파일이고 이름이 .txt로 끝나는 파일 검색
    ```
    

### locate

- 경로의 일부를 지정해 파일 찾기. 전용 데이터베이스에서 검색하므로 훨씬 빠름.
- 하루에 한번 데이터베이스 만듬.
- 별도로 명령어 설치 필요

```bash
$ locate --version <- locate 설치 확인
$ sudo apt-get install mlocate <- 우분투에서 locate 설치
$ sudo updatedb <- 파일 경로 목록을 데이터베이스에 등록
$ locate bash <- bash 라는 문자열이 포함된 경로 겸색
$ locate -i notes <- i 옵션을 사용하면 대소문자 구분없이 검색
$ locate -b python <- b 옵션을 사용해 파일 이름만으로 검색 (그렇지 않으면 해당 문자열을 포함한 디렉터리와 그 아래에 있는 파일을 모두 출력)
$ locate docs document <- 여러개의 문자열을 지졍하면 OR 조건으로 검색.
$ locate -A bash doc <- A 옵션을 사용하면 AND 조건으로 검색함.

```

## 명령어 확인하기

### —help 옵션: 명령어 도움말 제공

```bash
$ cat --help <- cat 명령어의 도움말 출력
```

### man: 매뉴얼 출력

- 명령어 + 리눅스 설정파일, 라이브러리에 대한 매뉴얼도 출력.

```bash
$ man cat <- cat 명령어의 매뉴얼 출력
```

- -k 옵션을 사용하면 키워드로 매뉴얼 검색 가능
    - man -k <키워드>
- 매뉴얼의 섹션은 총 9가지.
    - 1: 명령어
    - 2: 시스템콜
    - 3: 라이브러리 함수
    - 4: 디바이스 파일
    - 5: 파일 서식
    - 6: 게임
    - 7: 기타
    - 8: 시스템 관리 명령어
    - 9: 커널 루틴

```bash
$ man 1 crontab <- 섹션 1(명령어) crontab 매뉴얼 표시
```

- -wa 옵션으로 명령어가 어느 섹션에 있는지 검색 가능

```bash
$ man -wa crontab
```

## 명령어 검색

### which: 명령어 전체 경로 표시

- 명령어를 사용할 때 전체 경로를 입력하지 않아도 되는 건 셸이 $PATH라는 환경변수에 저장된 장소에서 명령어를 찾기 때문

```bash
$ echo $PATH <- 셸이 명령어를 찾는 환경변수
```

- $PATH에 설정된 디렉터리 = 패스(path). 패스를 설정해두면 명령어 이름만으로 실행 가능.
- 명령어 파일의 실제 위치는 which 명령어를 사용해 확인

```bash
$ which cat 
$ which -a lsmod <- 같은 이름의 파일을 전부 출력
```