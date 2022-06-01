# 과제2-조사내용 README파일로  정리하기
- 리눅스 명령어와 vim 에디터에서 매크로 관련하여 조사
1. 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기
2. vim 에디터에서 매크로 사용방법에 대하여 조사하기 (q , @)

## 1. 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기

### top
>요약 시스템 프로세스/메모리 사용 현황을 실시간으로 출력한다.
#### 사용법 및 옵션

    top [옵션]
    
- **-b** : 배치모드로 정보를 출력한다. 실시간 상화 대화형모드로 정보를 화면에 일렬로 출력한다.
- **-d delay** : 지정한 시간(**delay** 초)의 간격으로 정보를 업데이트하여 출력한다.
- **-i idle** : 토글값이 off일 때, **idle** 프로세스나 좀비 프로세스 정보를 출력하지 않는다.
- **-n num** : 지정한 시간(**num**)만큼 업데이트 정보를 출력한다.
- **-p pid** : 지정한 프로세스 ID(**pid**)의 정보만을 출력한다.
- **-q** : 시간의 간격 없이 계속하여 업데이트 정보를 출력한다.
- **-s** : 몇 개의 대화식 명령을 비활성화한다(시큐어 모드).
- **-S** : 누적된 정보를 출력한다(cumulative 모드).

#### 설명
>top 명령어는 시스템의 프로세스/메모리 사용 상태를 5초의 간격으로 업데이트하여 출력한다.\
>화면에 출력되는 기본값은 현재시간, 시스템 업데이트(1) 시간, 시스템에 로그인한 사용자 수,\
>지난 1분, 지난 5분, 지난 15분간의 시스템 평균 부하를 출력한다.\
>이 목록 아래에 프로세스 정보, CPU 상태, 메모리와 스왑 상태를 출력한다.\
>top 명령어를 실행한 후 초기 화면에서 **h** 키를 입력하면 사용할 수 있는 단축키 목록을 확인할 수 있다.

#### top 단축키 명령어

|명령어|설명|
|:----:|---|
|**space**|정보를 업데이트한다.|
|**^L**|스크린을 다시 초기화한다.|
|**F or f**|필드를 추가나 제거한다. 아래 ‘top 항목에 대한 설명’을 참조한다. 확인하고자 하는 항목의 알파벳을 누를 때마다 선택/취소가 반복된다.|
|**O or o**|출력하는 필드의 정렬 순서를 변경한다. 아래 ‘top 항목에 대한 설명’을 참조하자. 대문자로 선택한 항목을 누르면 왼쪽으로 이동하고 소문자를 누르면 오른쪽으로 이동한다.|
|**h or ?**|사용 가능한 명령어를 출력한다.|
|**k**|프로세스를 종료시킨다.|
|**n or #**|출력할 프로세스의 수를 지정한다.|
|**s**|출력할 정보의 업데이트 시간을 지정한다.|
|**W**|~/.toprc에 설정된 내용을 저장한다.|
|**q**|top을 종료한다.|

#### top 보기 수정 단축키
>출력되는 메인 정보 창 중에 상단의 정보를 수정한다.

|명령어|설명|
|:----:|---|
**S**|cumulative 모드(실시간 정보를 누적 데이터로 보여 줌)를 선택/해제한다.
**i**|dle 프로세스 정보를 출력한다/해제한다.
**I**|rix나 솔라리스 정보를 출력한다/해제한다.
**c**|령행에서 실행한 명령어 자체로 출력한다/해제한다.
**l**|로드 평균 정보를 출력한다/해제한다.
**m**|메모리 정보를 출력한다/해제한다.
**t**|요약된 정보만을 출력한다/해제한다.

#### top 정렬 단축키
>메인 창에서 실행하는 명령으로 현재 정보를 사용자의 요구대로 정렬한다.

|명령어|설명|
|:----:|---|
**r**|프로세스의 우선순위를 변경한다.
**N**|pid 정보를 기준으로 정렬한다.
**A**|age 정보를 기준으로 정렬한다.
**P**|CPU 사용량을 기준으로 정렬한다.
**M**|적재된 메모리 사용량을 기준으로 정렬한다
**T**|시간/누적시간을 기준으로 정렬한다.
**u**|지정한 사용자의 정보만을 출력한다.

#### top 항목에 대한 설명
>필드의 구성을 변경할 때 출력되는 내용을 정리하였다.

|부호|기호|명칭|설명|
|:-:|:--:|----|----|
\*(2)|**A**|PID|프로세스 ID
||**B**|PPID|부모 프로세스 ID
||**C**|UID|사용자 ID(User ID)
\*|**D**|USER|사용자 이름
\*|**E**|%CPU|CPU 사용량
\*|**F**|%MEM|메모리 사용량
||**G**|TTY|사용중인 tty를 출력한다.
\*|**H**|PRI|우선순위
\*|**I**|NI|nice 우선순위 값
||**J**|PAGEIN|페이지 오류 수
||**K**|TSIZE|코드 크기(KB)
||**L**|DSIZE|데이터 + 스택 크기(KB)
\*|**M**|SIZE|가상 이미지 크기(KB)
||**N**|TRS|현재 문자 크기(KB)
||**O**|SWAP|스왑 크기(KB)
\*|**P**|SHARE|분할된 페이지(KB)
||**Q**|A|접근한 페이지 수(KB)
||**R**|WP|쓰기 보호된 페이지 수(KB)
||**S**|D|쓰레기 페이지
\*|**T**|RSS|메모리에 상주하고 있는 현재 페이지의 크기
||**U**|WCHAN|유휴 상태로 있는 함수
\*|**V**|STAT|프로세스 상태
\*|**W**|TIME|CPU 시간
\*|**X**|COMMAND|명령어
||**Y**|LC|마지막으로 사용한 CPU
||**Z**|FLAGS|테스크 플래그
>\*는 현재 사용하고 있다는 뜻이다.

---
### ps
>프로세스의 현재 상태를 출력한다.
#### 사용법 및 옵션

    ps [옵션]

##### 주요 명령어
- **-e** : 커널 프로세스를 제외한 모든 프로세스를 출력한다.\
![e](https://user-images.githubusercontent.com/106523894/171360633-07e805d9-5e70-4ca9-9a6e-323f4b13833d.png)
- **-f** : UID, PID, PPID, C, STIME, TTY, TIME, CMD 등의 필드를 CMD 필드의 전체 명령어 형태로 출력한다.\
![f](https://user-images.githubusercontent.com/106523894/171361490-2a3cb169-5c00-4663-86a8-938cc9626a3e.png)
- **-u [사용자]** : 특정 **사용자**의 프로세스 정보를 출력, **사용자**를 지정하지 않는다면 현재 **사용자** 기준으로 출력\
![u](https://user-images.githubusercontent.com/106523894/171363157-3afc0c3a-7774-435c-9dcd-7033c987dfa0.png)
>ps 명령어는 보통 아래와 같이 grep와 연동해서 사용한다.\
>![그랩](https://user-images.githubusercontent.com/106523894/171359664-78214d2a-d0af-4a18-a57d-1f775700f0ee.png)

##### 설명
>ps 명령어는 프로세스의 현재 상태를 출력한다.
>>**ps와 top의 차이점**
>>- ps는 ps한 시점에 proc에서 검색한 cpu 사용량을 출력한다.
>>- top은 proc에서 일정 주기로 합산해 cpu 사용율을 출력한다
###### 자주 사용하는 ps 옵션의 조합
>표준 문장으로 시스템의 모든 프로세스를 출력한다.
>```
>$ ps -e
>$ ps -ef
>$ ps -eF
>$ ps -ely
>```

>BSD 문장으로 시스템의 모든 프로세스를 출력한다.
>```
>$ ps ax
>$ ps aux
>```

>프로세스 트리를 출력할 수 있다.
>```
>$ ps -ejH
>$ ps axjf
>```

>스레드 정보를 출력한다.
>```
>$ ps -eLf
>$ ps axms
>```

>아래 옵션은 보안 정보를 확인할 수 있다.
>```
>$ ps -eo euser, ruser, suser, fuser, f, comm., lable
>$ ps axZ
>```
---
### jobs
---
### kill

## 2. vim 에디터에서 매크로 사용방법에 대하여 조사하기 (q , @)

### 매크로
