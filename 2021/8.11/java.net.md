# java.net

- 자바에서 서버 통신을 위한 패키지

- ip

  - 컴퓨터마다 고유로 가지고 있는 식별번호
  - 형태는 10.5.6.100이고 각 자리수마다 8바이트 256x256x256x256의 경우의 수가 존재

- port

  - 컴퓨터안에 존재하는 프로그램마다마다 붙여져있는 식별번호
  - 컴퓨터안에서 식별번호이기때문에 다른 컴퓨터와는 중복
  - 0 ~ 65535까지 가능

- 결국 우리가 누군가의 컴퓨터의 프로그램의 접속하고 통신하기 위해서는 ip, port번호를 알아야함


- 기본 ip, port확인하는 클래스 - java.net.inetAddress

- 생성 방식

  - InetAddress myip = InetAddress.getLocalHost();
  - 메소드
    - gethostadress()
      - ip 주소 리턴
    - gethostname()
      - 컴퓨터 호스트이름 리턴

  

- 다른 컴퓨터, 서버 불러오는 방법

  - InetAddress[] otherip = InetAddress.getAllByName("www.naver.com");
    		for(InetAddress one : otherip) {
    			System.out.println(one.getHostAddress());
    		}

- 네이버와 같이 1대 다로 많은 클라이언트와 접속해야 하는 경우, 도메인을 이용함

- 도메인이란 고유한 문자형식으로 승인을 받아 도메인을 입력하면 네이버의 ip와 port번호를 해석해서 

  사이트에 접속함.

## 요청과정

- 정보를 주고 받을때는 reader, writer클래스를 사용못하고, outputstream, inputstream을 사용해야 함
  - 즉, 바이트 단위로 정보를 보내야 된다는 것이고, 정확히는 바이트 배열로 보냄.
  - string을 바이트 배열로 변환할때는 getbyte
  - **즉, writer,read를 할때 뒤에 매개변수가 바이트 배열로 오는 생성자를 사용해야 한다는 것

  - 일단 서버, 클라이언트가 존재함

    1. 서버가 먼저 프로그램의 port번호(소켓)를 부여하고 프로그램 동작

       - ServerSocket soc = new ServerSocket(9990);
         System.out.println("서버소켓 생성 완료");

    2. 클라이언트는  나의 ip주소를 통해 서버 소켓에 접속하여 나의 ip주소를 매개로 하는 클라이언트 소켓 생성

       - Socket s = new Socket("192.168.55.251", 9990);

    3. 서버는 들어온 ip를 제한하거나 받아들임

       - Socket s = soc.accept();

    4. 클라이언트는 접속이 성공했으면, 정보를 써서 보냄

       ```java
       			Scanner sc = new Scanner(System.in);
       			System.out.print("아이디 : ");
       			String id = sc.nextLine();
       			System.out.print("비밀번호 : ");
       			String pw = sc.nextLine();
       			
       			``OutputStream os = s.getOutputStream();``
       			byte[] client_id = id.getBytes();
       			byte[] client_pw = pw.getBytes();
       			
       			os.write(client_id);
       			os.write(13);
       			os.write(10);
       			os.write(client_pw);
       			os.write(13);
       			os.write(10);
       			os.flush();
       ```

    5. 서버는 다시 그 정보를 받아서 프로그램의 입력하고, 정보에 따른 내용이나 승인을 적용, 출력

       ```java
       			``InputStream is = s.getInputStream();``
       			Scanner sc = new Scanner(is);
       			
       			String server_id = sc.nextLine();
       			String server_pw = sc.nextLine();
       ```

    6. 4,5를 반복하다 클라이언트가 접속을 종료하면 자동 서버도 종료되고 클라이언트 소켓도 사라짐

       - 여기서 서버는 while문을 통해 프로그램 소켓을 유지할 수 있음
       - s.close();
         System.out.println("포트 접속해제됨");
         - 여기서 s는 소켓 클라이언트 소켓 객체
    
- 에러 사례

  - java.net.connection : connection refused : connect

    - 서버가 아직 포트를 지정하고 시작하지도  않았는데 클라이언트가 접속 하려할때
    - 해결  - 서버키고 클라이언트 기동

  - java.net.bindexception

    - 서버가 하나 실행중인데 또 다시 서버를 실행하려할때, 포트번호는 중복되지 않기에 에러뜸
    - 해결 - 기존 서버 정지시키기

  - **오고가는 정보 스트림중 하나를 close하면 그 자바 파일에 있는 모든 스트림과 소켓이 다 닫히므로

    주의가 필요

## TCP/UDP

- protocol은 통신 규칙으로서, TCP/UDP도 일종의 프로토콜

### TCP

- 1대 1방식의 통신으로, 하나의 서버와 클라이언트과 통신하다가 클라이언트가 끊으면 또다시 다른 클라이언트를 접속 시켜 통신하는 것
- 전화 방식이라고 한다.
- 신뢰성 높음
- 클래스 - serversocket, sockt클래스



### UDP

- 1대 다 방식의 통신으로 하나의 서버와 여러개의 클라이언트가 존재하며, 간단히 말하여 우편 방식이다.

- 보낼때, TCP와 달리 데이터, 누가, 누구한테를 다 입력해서 보내야됨,

- 신뢰성 떨어짐

- 대량 메시지를 한꺼번에 보낼 수 있고, 답변을 못받을 수도 있다. 즉, 이뜻은 연결, 연결해제라는 개념이 없다는

  것이다.

- 클래스 - datagramsocket, datagrampacket클래스
