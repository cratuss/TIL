# java.io

- input,outputstream은 바이트 단위로 읽거나 쓸때 사용하는 클래스

- read나 write나 읽어올때 기본은 아스키 코드로 읽고 알파벳이나 숫자이외에 값은

  유니코드로 표현

## Reader

- filereader, bufferreader, inputstream
- 파일이나 정보를 읽어와서 입력시키는 클래스
- 메소드에는
  - read()
    - 안에 다양한 형태의 매개변수를 가진 생성자 존재하며, 바이트 배열도 들어갈 수 있음
    - char단위 10진수로 하나씩 리턴, inputstream은 byte단위로 하나씩 리턴
    - 읽어올게 없으면 -1리턴
  - close()
    - 읽어온 파일을 닫아서 마무리하는것. 반드시 마지막에 메소드 적용해야함
    - 마지막 툴에서 refresh

## Writer

- filewriter, bufferwriter, outputsream
- 파일이나 정보에 내용을 적고, 출력시키는 클래스
- 메소드에는
  - write()
    - 위에 read처럼 안에 문자열이나 바이트 배열이나 다양하게 넣고 파일에 입력시키는것
    
    - 즉 이역시 다양한 매개변수를 가진 생성자들이 존재
    
    - 여기서 매개변수가 두개일 경우 뒤에는 boolean값으로 true이면 기존 내용에 추가해서
    
      쓰고 false면 기존내용을 다 삭제하고 씀
  - flush()
    - write로 파일에 입력시키려하는 정보를 확실하게 마무리해서 넣는 것. 중요. write가 끝나면 반드시 적용
  - close()
    - Reader의 close와 마찬가지로 열은 파일을 닫는 것. 반드시 마지막에 적용.
    - 마지막 툴에서 refresh

## Scanner

- 원초적인 system.in.read클래스와 같은 아스키코드 값밖에 불러올 수 없는 메소드의 한계를 극복하여 유니코드 문자까지 적용가능하게 해주는, 메소드로 자바에서 유용

- 객체 생성 형태는

  - Scanner scan = new Scanner();
    - 뒤에 ()안에는 system.in 또는 file클래스(filewriter,filereader) 객체가 들어갈수도 있음

- 메소드에는

  - nextline()

    - enter를 기준으로 친다음의 전에 줄 전체를 읽어오는 것. enter기준인게 중요하다.

      파일을 작성할때도 \r\n 설정

  - next()
    - 공백기준으로 전에 문장을 읽어오는 것
  - nextint()
    - 공백기준으로 문장을 인트값으로 읽어오는 것.
  - nextdouble()
    - 공백기준으로 문장을 더블값으로 읽어오는것, 이외 여러 타입 메소드 존재
  - hasnextxxx()
    - 다음에 불러올 문장이 있는지 없는지를 boolean값으로 리턴

## File

- 그냥 file 클래스 자체는 입출력 기능이 없고 크기나 경로 목록 표시를 위한 클래스

- 객체 생성형태는

  - File f = new File('"경로");

    - 상대경로는 현재 workspace가 있는 폴더 기준으로 경로를 짠다.

    - 절대경로는 기본대로
  
- 메소드는

  - length()
    - byte단위로 파일 크기 리턴
  
  - lastmodified()
  
    - 마지막 수정 날짜 리턴
  
  - getxxxpath()
  
    - 경로 리턴,  xxx는 상대경로인지 절대경로인지에 따라 달라짐
  
  - list();
  
    - 폴더라면 안에 목록 리턴
  
  - exists()
  
    - file 객체로 생성한 객체가 진짜로 존재하는지 안하는지를 boolean으로 리턴
  
  - isdirectory()
  
    - 객체가 폴더인지 아닌지 boolean으로 리턴
  
  - isfile()
  
    - 객체가 파일인지 아닌지 boolean으로 리턴
## InputstreamReader / outputstreamreader

- inputstream 타입의 1바이트 정보를 reader타입의
  2바이트 변환하는 것/ outputstream은 역으로 writer로 변경하는 것

## bufferdReader / bufferedwriter

- 외부 메모리 있는 정보들을 자바 내부메모리에 저장 시켜서
  불러올때 내부에서 불러와 입력속도를 향상시킨다.

## datainputstream

- 자바 데이터 타입으로 변환 입력, 정수와 실수 타입 가져올때 편함

## 위에 3 클래스는 scanner가 다 역할 가능







