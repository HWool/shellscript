# Linux Shell (CentOS)

## <b> 1. grep  </b>
- 특정 문자열을 파일에서 찾아주는 명령어.   
- Syntax : `grep [옵션][정규표현식(문자열)][찾기 대상이 될 파일명]`

<br>

| 메타 문자 | 기능 | 사용 예 | 사용 예 설명 |
| :-----: | ---- | :-----: | ----------- |
|^|행의 시작 지시자|'^test'|test로 시작하는 모든 행과 대응함|
|$|행의 끝 지시자|'test$'|test로 끝나는 모든 행과 대응함|
|.|하나의 문자와 대응|'t.s.'|총 4개의 문자로 이루어진 문자열을 검색하는 데, 첫 번째는 't', 세 번째는 's'인 문자열을 모두 대응함|
| * |선행 문자와 같은 문자 0개 또는 임의 개수와 대응|'test*'|test를 기본으로 뒤에 아무 문자나 포함하여도 모두 대응|
|[ ] | [] 사이의 문자 집합 중, 하나의 대응|'[Tt]est'|'test'나'Test'를 대응함|
|[^]| 문자집합에 속하지 않는 한 문자와 대응|'[^A-T]est'|A와 T 사이 범위에 포함되지 않는 한 문자와 est가 붙은 문자열만 검색한다|
|\\<| 단어의 시작 지시자 | '\\<test' | test로 시작하는 단어를 포함하는 행과 대응|
| \\> | 단어의 끝 지시자 | 'test\\>' | test로 끝나는 단어를 포함하는 행과 대응 |
| \\(..\\) | 다음 사용을 위해서 태그를 붙임 | '\\(..\\)ing'| 지정된 부분을 태그 1에 저장한다. 나중에 태그 값을 참고 하려면 \1을 쓴다. 맨 왼쪽부터 시작하여 태그를 9개까지 쓸 수 있다. 왼쪽 예에서는 tes가 레지터스1에 저장되고, 나중에 \1로 참고할 수 있다.|
|x\\{m\\}|문자 x를 m번 반복한다.|'t\\{5\\}'|문자 t가 5회 연속으로 나오는 모든 행을 대응함|
|x\\{m,\\} | 적어도 m번 반복한다. | 't\\{5,\\}' |문자 t가 최소한 5회 반복되는 모든 행과 대응함.
|x\\{m,n\\} | m회 이상 n회 이하 반복한다. | 't\\{5,10}'| 문자 t가 5회에서 10회 사이의 횟수로 연속으로 나오는 문자열과 대응함.

<br>

[ 옵션 ]  
***
    -E      : PATTERN을 확장 정규 표현식(Extended RegEx)으로 해석.   
    -F      : PATTERN을 정규 표현식(RegEx)이 아닌 일반 문자열로 해석.   
    -G      : PATTERN을 기본 정규 표현식(Basic RegEx)으로 해석.    
    -P      : PATTERN을 Perl 정규 표현식(Perl RegEx)으로 해석.   
    -e      : 매칭을 위한 PATTERN 전달.   
    -f      : 파일에 기록된 내용을 PATTERN으로 사용.   
    -i      : 대/소문자 무시.   
    -v      : 매칭되는 PATTERN이 존재하지 않는 라인 선택.   
    -w      : 단어(word) 단위로 매칭.   
    -x      : 라인(line) 단위로 매칭.   
    -z      : 라인을 newline(\n)이 아닌 NULL(\0)로 구분.   
    -m      : 최대 검색 결과 갯수 제한.   
    -b      : 패턴이 매치된 각 라인(-o 사용 시 문자열)의 바이트 옵셋 출력.   
    -n      : 검색 결과 출력 라인 앞에 라인 번호 출력.   
    -H      : 검색 결과 출력 라인 앞에 파일 이름 표시.   
    -h      : 검색 결과 출력 시, 파일 이름 무시.   
    -o      : 매치되는 문자열만 표시.   
    -q      : 검색 결과 출력하지 않음.   
    -a      : 바이너리 파일을 텍스트 파일처럼 처리.   
    -I      : 바이너리 파일은 검사하지 않음.   
    -d      : 디렉토리 처리 방식 지정. (read, recurse, skip)    
    -D      : 장치 파일 처리 방식 지정. (read, skip)    
    -r      : 하위 디렉토리 탐색.    
    -R      : 심볼릭 링크를 따라가며 모든 하위 디렉토리 탐색.    
    -L      : PATTERN이 존재하지 않는 파일 이름만 표시.   
    -l      : 패턴이 존재하는 파일 이름만 표시.   
    -c      : 파일 당 패턴이 일치하는 라인의 갯수 출력.    

<br>

## <b> 2. awk </b>
- 지정된 파일로부터 데이터를 분류한 다음 ,분륜된 텍스트 데이터를 바탕으로 패턴 매칭 여부를 검사하거나 데이터 조작 및 연산 등의 액션을 수행하고, 그 결과를 출력하는 기능을 수행함.   
- Syntax : `awk [옵션] [awk program] [ARGUMENT]`   

<br>

[ 옵션 ]
*** 
```  
-F      : 필드 구분 문자 지정.   
-f      : awk program 파일 경로 지정.    
-v      : awk program에서 사용될 특정 variable값 지정.
```
[ awk program ]
***
```   
-f 옵션이 사용되지 않은 경우, awk가 실행할 awk program 코드 지정.   
```
[ ARGUMENT ]
***
```
입력 파일 지정 또는 variable 값 지정.   
```

<br>

## <b> 3. tr </b>
- translate의 약어로써, 지정한 문자를 바꿔주거나 삭제하는 명령어이다.    특정한 문자를 다른 문자로 바꾸거나 또는 특정 문자를 제거하는데 쓰인다.   
- Syntax : `tr [옵션] [문자열1] [문자열2]`   

<br>

[ 옵션 ]
***
``` 
-d      : 문자열 1에서 지정한 문자를 삭제 후 출력한다.   
-s      : 문자열 2에서 반복되는 문자를 삭제한다.   
-t      : 문자열 1을 문자열 2의 길이로 자른다.
등등
```

<br>

## <b> 4. base64 </b>
- 8비트 이진 데이터를 문자 코드에 영향을 받지 않는 공통 ASCII 영역의 문자들로만 이루어진 일련의 문자열로 바꾸는 인코딩 방식을 가리키는 개념.   
- Syntax : `base64 [옵션] [파일명]`

<br>

[ 옵션 ]
***
```
-d    : base64 디코드(옵션이 없으면 인코드)
-i    : 디코딩할 때 알파벳 아닌 문자 무시.
-w    : COLS 문자 뒤에 줄 바꿈 (COLS는 문자를 나타내는게 아닌 어느 단어의 축약을 한 것임)
```

<br>

[ 예시 ]
***
```
head -c 76 /dev/urandom | base64 -w0 -> 한 줄로 출력(줄 바꿈이 없음)
head -c 76 /dev/urandom | base64 -w1 -> 한 문자씩 출력(문자 하나당 줄 바꿈)
```

<br>

## <b> 5. cut </b>
- 파일에서 필드를 뽑아낸다. 필드는 구분자로 구분할 수 있다.   
- Syntax : `cut [옵션] [파일]`

<br>

[ 옵션 ]
***
```
-c    : 잘라낼 곳의 글자 위치를 지정한다. "," 나 "-"을 사용하여 범위를 지정할 수도 있으며, 이런 표현들을 혼합하여 사용할 수도 있다.
-f    : 잘라낼 필드를 정한다.
-d    : 필드를 구분하는 문자를 지정한다. (default = tab)
-s    : 필드 구분자를 포함할 수 없다면 그 행은 하지 않는다.  
```

<br>

[ 예시 ]
***
``` bash
cat << EOF > test.txt 
aaa:bbb:Ccc:ddd:gdef
efef:aab:wef:bgb:azc
EOF
```
1. `cut -c 3`
> output
``` 
a
e
```

2. `cut -c 1-5`
> output
```
aaa:b
efef:
```

3. `cut -d":" -f3`
> output
```
Ccc
wef
```

4. `cut -d"K" -f3`　(구분자가 없을 때)
> output

``` 
aaa:bbb:Ccc:ddd:gdef
efef:aab:wef:bgb:azc
```


5. `cut -d"K" -f3 -s`　(구분자가 없을 때)
> output 
```
출력없음
```

<br>

## <b> 6. sed </b>
- vi 편집기처럼 편집에 특화된 명령어로 수정, 치환, 삭제, 글 추가 등 편집기 기능 왠만한 거는 다 가지고 있다.   
vi와 다른 점은 편집을 하더라도 원본에 손해가 없다라는 특징이 있다.   
- Syntax : `sed [옵션] '[subcommand]///(flag)'` 주로 이런 식이지만 여러가지 방법이 있으니 찾아서 쓰자.

<br>

[ 옵션 ]
***
<img src=./image/sed1.png width="600px">
<img src=./image/sed2.png width="600px">
<img src=./image/sed3.png width="600px">   

<사진 출처: https://webstone.tistory.com/83>

<br>

[ subcommand ]
***
|subcommand|의미|
|:--------:|---|
|a\\ |현재 행에 하나 이상의 새로운 행을 추가한다.|
|c\\ |현재 행의 내용을 새로운 내용으로 교체한다.|
|d   |행을 삭제한다|
|i\\ |현재 행의 위에 텍스트를 삽입한다.|
|h| 패턴 스페이스의 내용을 홀드 스페이스에 복사한다. |
|H| 패턴 스페이스의 내용을 홀드 스페이스에 추가한다. |
|g| 홀드 스페이스의 내용을 패턴 스페이스에 복사한다. |
|G| 홀드 스페이스의 내용르 패턴 스페이스에 추가한다.|
|l| 출력되지 않는 특수문자를 명확하게 출력한다. |
|p| 행을 출력한다. |
|n| 다음 입력 행을 첫 번재 명령어가 아닌 다음 명령어에서 처리하게 한다. |
|q| sed를 종료한다. |
|r| 파일로부터 행을 읽어온다.|
|!| 선택된 행을 제외한 나머지 전체 행에 명령어를 적용한다.|
|s| 문자열을 치환한다. |

<br>

subcommand `s`와 같이 쓰는 치환 플래그
***
| flag | 의미 |
| :--: | ----- | 
| g | 치환이 행 전체에 대해 이뤄진다.|
|p  | 행을 출력한다. |
|w  | 파일에 쓴다. |
|x  | 홀드 버퍼와 패턴 스페이스의 내용을 서로 맞바꾼다.|
|y  | 한 문자를 다른 문자로 변환한다.|

<br>

## <b> 7. curl </b>
- 서버와 통신할 수 있는 커맨드 명령어 툴
- 커맨드 라인이나 소스코드로 손 쉽게 웹 브라우저 처럼 활동할 수 있도록 해주는 기술.
- 다양한 프로토콜을 지원한다
    - DICT,FILE,FTP,FTPS,HTTP,HTTPS,IMAP,IMAPS,POP 등 많음.
- SSL 인증 방식도 가능하다.
<b> url을 가지고 할 수 있는 것들은 다할 수 있다고 보면 된다. </b>
- Syntax : `crul [옵션] [주소]`

<br>

[ 옵션 ]
***
|short|long|설명|
|:---:|----|---|
|-k|--insecure|https 사이트를 SSL certificate 검증없이 연결|
|-I|--head|HTTP 헤더만 보여주고 content는 표시하지 않음|
|-D|--dump-header \<file>|\<file>에 HTTP 헤더를 기록한다.|
|-L|--location|서버에서 HTTP 301이나 302 응답이 왔을 경우 redirection URL로 따라간다.   --max-redirs 뒤에 숫자로 redirection을 몇 번 따라갈지 지정할 수 있는데 기본 값은 50이다.|
|-d|--data|HTTP Post data|
|-v|--verbose|동작하면서 자세한 옵션을 출력한다|
|-J|--remote-header-name|어떤 웹 서비스는 파일 다운로드 시 Content-Disposition Header를 파싱해야 정확한 파일이름을 알 수 있을 경우가 있다. -J 옵션을 주면 헤더에 있는 파일 이름으로 저장한다. |
|-o|--output FILE| curl은 remote에서 받아온 데이터를 기본적으로는 콘솔에 출력한다. -o 옵션 뒤에 FILE을 적어주면 해당 FILE로 저장한다.|
|-O|--remote-name|file 저장 시 remote의 file 이름으로 저장한다. -o 옵션보다 편리하다.|
|-s|--silent| 정숙 모드로, 진행 내역이나 메시지 등을 출력하지 않는다.|
|-X|--request|Request시 사용할 method 종류를 기술한다.|
|-i|--include|응답에 Content만 출력하지 않고 서버의 Response도 포함해서 출력한다/|
|-f|--fail|HTTP 오류 시 자동으로 실패(출력 없음)|
|-S|--show-error|-s를 사용해도 오류 표시|

<br>

## <b> 8. gpg  </b>
- GunPG : GNU Privacy Guard. GPG라고도 한다.   
통신상에서 혹은 데이터를 저장할 때 보안을 지키는 Tool이고, 데이터를 암호화하고 전자 서명을 만들 수 있으며 암호화 도구로 유명한 PGP를 완벽하게 대신할 수 있다. 공개키 기반 암호화 기법.   
- Syntax : `gpg [옵션]`

<br>

[ 옵션 ]
***
```
--gen-key       : key-pair 생성하기.
--list-keys     : key 확인하기.
--import        : key import
--export        : key export
--encrypt       : key 암호화
--decrypt       : key 복호화
```
자세한건 사이트에서 참조.   
[참조] (https://www.gnupg.org/documentation/manuals/gnupg/Operational-GPG-Commands.html).

## <b> 9. tee</b>
- 표준 입력에서 읽어서 표준 출력과 파일에 쓰는 명령어.
- Syntax : `tee [옵션] [파일]`

<br>

[ 옵션 ]
***
```
-a       : 덮어쓰기 말고 해당 파일에 추가해서 입력합니다.
-i       : interrupt를 무시하는 옵션
```

<br>

### <b>Why Use tee</b>
***
echo나 cat 등과 같은 IO redirection 연산자랄 사용하면 될텐데 왜 tee를 사용하는지.

``` bash
echo "hello world" >> OUTFILE
```
``` bash
echo "hello world" | tee -a OUTFILE
```

위 두 문장 모두 OUTFILE에 "hello world"를 append 하는 것은 동일하다. 다음 문장을 보자

``` bash
sudo echo "validate_password.policy=LOW" >> /etc/mysql/mysql.conf.d/mysqld.cnf 
```

echo 앞에 sudo를 command를 써서 root 권한을 사용할 수 있지만, shell에서 출력을 redirection 할 경우 일반 사용자로 전환되어 제대로 동작하지 않아 `permission denied`에러가 날 것이다.

``` bash
echo "validate_password.policy=LOW" | sudo tee -a /etc/mysql/mysql.conf.d/mysqld.cnf 
```
echo를 받아서 sudo tee를 하면 정상적으로 동작할 것이다.

이러한 이유로 tee는 shell script에서 root 권한으로 특정 파일을 쓰거나 append 할 때 주로 활용한다.




