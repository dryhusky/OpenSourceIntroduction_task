# 오픈소스SW개론 과제
***

|학번|이름|
|----|---|
|20154320|김신영|

# 리눅스 명령어정리

### top

CPU, Memory, Process 같은 시스템의 상태를 파악이 가능한 명령어

***top 사용법)***
$ top [option]
```
top // 옵션없이 실행 시 interval 간격으로 3초마다 화면을 갱신하여 정보를 보여줍니다.

top -n // top 실행 주기 설정(반복 횟수)

top -b // batch모드로써 순간의 정보를 확인할 수 있음
```

***top 실행 후 명령어)***

|명령어|설명|
|-------|-------------------|
|shift + p| CPU 사용률 내림차순  |
|shit + m| 메모리 사용률 내림차순|
|shift + t| 프로세스가 돌아가고 있는 시간 순|
|k| kill. k 입력 후 PID 번호 작성. signal은 9|
|f| sort field 선택 화면 -> q 누르면 RES순으로 정렬|
|a| 메모리 사용량에 따라 정렬|
|b| Batch 모드로 작동|
|1| CPU Core별로 사용량 출력|


### ps 명령어

process status의 줄인말로
현재 실행중인 프로세스 목록과 상태를 보여줌


***ps 사용법)***
$ ps [option]
```
- A // 모든 프로세스를 출력한다

- e // every(모든) 프로세스

- f // ful(완전한) 포맷

- l // long(긴) 포맷
```

***ps 사용 예시)***


**ps -ef** : 모든 프로세스를 풀 포맷으로 출력

**ps -ef | grep '프로세스명'** : '프로세스명'의 프로세스 구동 확인

**ps auxf** : 실행 중인 프로세스를 트리구조로 보여줌

**ps aux** : 실행중인 모든 프로세스 확인



### ps와 top의 차이점)

ps는 ps한 시점에 proc에서 검색한 cpu 사용량

top은 proc에서 일정 주기로 합산해 cpu 사용율 출력



### jobs 명령어

작업의 상태를 표시하는 명령어

현재 쉘 세션에서 실행시킨 자식 백그라운드 작업의 목력이 출력

각 작업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용

![리눅스jobs명령어](https://user-images.githubusercontent.com/40632396/172054597-dd94049d-1026-48dd-8e21-63546bb924dd.jpg)


***jobs 사용법)***
$ jobs [option][작업번호]
```
-l // 프로세스 그룹 ID를 state 필드 앞에 출력

-n // 프로세스 그룹 중에 대표 프로세스 ID를 출력

-p // 각 프로세스 ID에 대해서 한 행씩 출력

command // 지정한 명령어를 실행
```

### kill 명령어

프로세스에 시그널(signal)을 보내는 명령어

어떤 시그널을 보내는 지 명시 하지 않으면 기본적으로 SIGTERM 시그널을 보내며 프로그램 종료

***kill 사용법)***
$ kill [option] PID
```
-l // 시그널 숫자와 이름이 출력된다. 뒤에 PID는 입력하지 않음

PID // ps나 jobs의 명령어를 통해 PID를 얻고 kill 명령어 파라미터로 넘겨 실행 시 종료

-s [signal][pid] // -s명령으로 종료 외의 다른 시그널을 보낼 수 있음

-s KILL [pid] // 기본 kill 시그널에 응답하지 않으면 강제로 KILL을 사용해 종료할 수 있음

```

kill -l 옵션 사용 시 아래와 같이 출력 됨

![kill_-l옵션](https://user-images.githubusercontent.com/40632396/172054660-6d24458a-f022-4216-b2ef-edd82dbbe724.jpg)


***

# VIM 에디터로 매크로 사용하기

### 커맨드 q, @

Normal/Command 모드에서 사용이 가능

같은 명령을 반복하는 매크로를 만들고 사용할 수 있음

***매크로 저장 과정***

```
1. q<저장할 매크로 문자> // q + a 를 하면 a키에 recording 시작

2. 그 후 반복을 위한 내가 원하는 동작을 입력

3. q // recording 종료

4. @a // 저장한 매크로 1회 실행

   @@ // 방금 실행한 매크로 실행
   10@a // a에 저장한 매크로 10회 실행
```