# java.lang

## object 클래스

- object클래스에는 필드변수나 생성자가 존재하지않는다.

### tostring()

- 기본 형 : 패키지명.클래스명 + @ + 16진수(객체주소값)
- 오버라이딩해서 출력값을 바꿀수도 있음
- 숫자를 문자로 변경할때도씀
  - ex)String aa = Integer.toString(a3);

### hascode()

- 객체 주소값 리턴

### equals()

- 주소값이 아닌 객체끼리의 실제 문자열값을 비교

## 기타

### a instanceof B

- A에 대입된 객체타입이 B인지를
  보는 것 즉, A  a = new B();이건지를 보는것 

### length()가 아닌 length는 단순 문자열 길이 리턴

- ex) 문자열.length()

### requireNonNull(a, "b") 

- a가 not null이면 a를 리턴하고 null이면 
  nullpointexception 발생시켜 b메시지를 message
  변수에 보냄 

### split("/")

- /를 기준으로 문자열 나눔
  /를 기준으로 그 앞까지 배열1,2,3...
  으로 해서 배열에 넣음
- ex)String[] array = str.split(",");

### concat()

- 문자열을 합침 ex) a.concat(b)
- +로 합치는 것과 차이는 concat은 바로 string 으로 
  되어지고 +는 stringbuilder로 변환한후 append로
  문자열 더해서 다시 tostring함수로 변환
- ex)sb.append("")가 동일 기능
  -->append는 stringbuffer나 stringbuilder로 치환된 문자열만 
  사용 가능

### Stringbuffer, Stringbuilder

- String 클래스의 인스턴스는 값변경이 안되나 값 변경 추가가 가능케함
- 즉, 값변경이 많을경우 쓰임, 무겁고 용량이크기에
- 기본 16개문자 저장가능, 이 크기는 사용자가 생성자로 조절 가능
- ex)  StringBuffer sb = **new** StringBuffer();
- sb.append("") 
  - sb와 ""합치기
- insert(0, "")
  - 해당 인덱스(0)에 ""문자열 추가
- substring(0, 4)
  - 기존 string 메소드와 같은 역할, 인덱스 0에서 4까지를 리턴
- Stringbuilder는 멀티스레드 환경이 적용이 안되기에 보통 안정적으로 Stringbuffer를씀

### Integer.parseInt(int이외타입)

- parse는 타입별로 다 존재하며 parsexxx의 xxx로 타입을 변환하는 것
- 주로 string변환에 쓰임

### 변수.charAt(index)

- index번호를 매개변수로 지정해서 그 위치 문자 1개 리턴

### 변수.indexOf("")

- ""문자열이 변수에 포함되있는지 확인하고 그 문자열 첫번째 문자가 있는 인덱스를 리턴
- lastindexof는 뒤에서부터 찾고 문자열에 첫번째가 아닌 마지막 문자 인덱스를 리턴

### Stringtokenizer

- split()처럼 쪼갤때 쓰는 클래스로, split과 달리 따로 객체를 생성해야 한다.
- 또한 split과는 다르게 배열로 바로 넣는게 아니라 nexttoken메소드로 뽑아와야함
- 생성자에는 
- tokenizer(String)
  - String값을 디폴트(공백)기준으로 자르기
- tokenizer(String, delim)
  - String값을 delim기준으로 자르기, 여러개 가능
  - ex) "-=" 이 중에 하나라도 들어가면 자름
- hasmoretoken()
  - 다음에 뽑아올 토큰이 있는지 없는지 boolean값
- nexttoken()
  - 다음 값을 뽑아옴

### String 클래스

- 생성자가 다양하게 존재해서 단순 문자열부터 배열(char, byte배열)도 받을수 있음

  ex) String aa = new String(new byte[] {65,66,67,68});

### 변수.replace("", "")

- 변수의 첫번째매개변수문자열이 존재할경우, 두번째 매개변수로 모두 바꾼다.
- replaceall은 정규식으로 설정이 가능

## java.util.Date / Calendar

### Date클래스

- Date date = new Date()
  - 이러한 선언만으로 date를 출력하면 시각 리턴

### Calendar클래스

- 선언방식은 
- Calendar cal = Calendar.getinstnce();
- calendar클래스는 추상클래스이기에 바로 객체 생성 불가
- int xxx = cal.get(Calendar.xxx)

  뒤에 xxx는 년, 월, 일 ,시간 , 초를 불러오는 메소드들

  예를 들어 day of week는 주중에 오늘에 몇번째일인지를 리턴

## java.text.simpledateformat / decimalformat

### simpledateformat

- date를 객체를 받아와서 날짜 포멧을 정하는 클래스

- 객체 생성해야 하며 생성자가 다양하기에, 객체 생성할때 매개변수로 포멧 정해줌

  ex) SimpleDateFormat sf = new SimpleDateFormat("yyyy -MM -dd -HH : mm : ss E");

  - jvm이 컴파일 과정에서 포맷을 설정하는 개념

- 이 후 실제로 이 포맷으로 객체를 대입하는 메소드 실행

- sf.format(date타입이나 메소드 혹은 cal.gettime())

- gettime()은 date타입

### decimalformat

- simpledateformat의 숫자버전

- '#' :1자리의 숫자. 의미없는 0표시 x

- '0' : 1자리의 숫자. 의미없는 0표시 o

  ex) 44.123의 ##.####는 44.123

  ​      00.0000은 44.1230

- 또한 정수부분은 무조건 항상 다 출력함

- #이 중간에 껴있을 경우 에러가 남. 왜냐면 4같은 경우 #.#0을 해버리면

  소수 두번째자리에 무조건 0을 채워야하는데 첫째자리가 안채우는 #이기에 오류

- \u00A4를 앞에 추가하면 w통화표시를 붙임

- 뒤에 %붙이면 앞에 숫자 100곱하고 %문자를 뒤에 붙임

## 기타2

 ### ** sysout과 tostring

- sysout을할때 ()안에가 변수나 클래스이면 자동으로
tostring()이 붙는다. 즉 sysout(pay)는
pay.tostring()이 된다는 것이다.

### ** valueof와 tostring의 차이
- 다른 타입을 string으로 변환할때는 tostirng valueof
두가지가 있는데 변환할 값이 null이면 tostring은
npe가 나지만 valueof는 null을 출력하기에 오류
발생을 없애려면 안정적으로 valueof를 쓰는게 낫다.

### 익명 클래스 

- 생성자안의 오버로딩된 다른 생성자를 부르는 this()
  가 존재할 경우 맨 위에 super()를 못쓴다. 
  this()도 맨 위에 존재하려는 성질을 갖고 있기에

### **같은 패키지 안에서는 import 안해도됨

### 중첩 클래스 

- 중첩 클래스에서 내부클래스가 static이면 바깥클래스
  인스턴스 생성 안해도됨
  ex) Car.Tire tire = mycar.new Tire() 
       Car.Tire tire = new Car.Tire(); -> static
- 익명 객체는 상속받거나 인터페이스를 구현해야 생성가능
  ->왜냐면 안에 오버라이딩을 통한 초기화가 목적이기에

### **

- byte,char배열은 string으로 자동형변환되면서 숫자에맞는 문자
  가 합쳐져서 들어감

  ex)String aa = new String(new byte[] {65,66,67,68});

