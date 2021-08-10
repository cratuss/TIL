# java.util.Collections

- 크게 컬렉션 클래스를 상속받은 List, Set, Map 인터페이스 존재

- 배열이라는 정적저장소(용량늘리지못함)을 보완한 클래스

- 즉, 동적으로 배열의 길이를 조절할 수 있고, 타입도 여러타입의 객체들이 들어갈수있음

- 타입은 기본 object타입으로 Integer,Double클래스등이 자동변환되는 개념이다.

- 그러나 제네릭<>을 붙으면 내부적으로 타입을 지정해서 jvm에서 통제하는것이 가능하다.

  ex) Set<E> set = new HashSet<E>();

___

## List

- 저장순서가 있으며, 중복도 허용한다.
- list도 배열처럼 향상된 for문으로 전 객체를 뽑아오는것이 가능하다.

### ArrayList

- List에서 가장 많이 쓰이는 자식객체(list를 상속받음)

- 생성할때 arraylist(5)는 최초 길이 5개에 10개씩추가
                arraylist(5,2)는 최초 길이 5개에 2개씩 추가

  ->생성자가 여러개라는 뜻

- 메소드에는

  - add("")

  - remove("")

    객체값, 인덱스번호 두개 다 지정가능

  - set(1, "a")

    1번 인덱스를 a로 수정

  - size()

  - get(1)

    1번 인덱스 위치 객체값 리턴

  - indexof("")

    반대로 ""데이터가 저장된 인덱스 리턴

    값이 없으면 -1 리턴

    거꾸로 해당 데이터가 2개이상일 경우 앞에 인덱스 하나만 리턴

  - clear()

    리스트의 객체를 전부 삭제

  - contains("")

    "" 데이터가 포함되있는지 확인하고 boolean타입으로 반환

### vector

- arraylist랑 동일 메소드를 갖음
- 하나의 스레드가 실행 완료해야만 다른 스레드를 실행할 수가있어서
  멀티스레드 환경에서 객체 추가 삭제에 있어서 안전성이 높다.

### linkedlist

- 인덱스 개념이아닌 참조 링크를 통한 체인형태로
  중간에 인덱스를 삭제하거나 추가할때 용이하며, 그 경우 그 인덱스를
  삭제하고 앞 뒤 인덱스를 합치기만 하기 때문에, 그대로 인덱스는 유지된다.
- 다시 말해서 여기서 인덱스는 그냥 리스트의 고유의 값이고, 
  **get으로 하나씩 출력할때 ()에 들어가는 인덱스는 그냥 안에 들어간 순서를
  출력하는 것이다.

## Set

- 저장 순서가 없고 중복 데이터 저장 불가능
- 로또 번호뽑기 등 순서, 중복 x인 상황에 대입한다.

- 인덱스가 없기에 안에 값을 .get()으로 출력할 수 없지만
  향상된 for문으로 출력하는 건 가능하다. 다만 그 순서는 랜덤이며
  한번 정해진 랜덤값은 다음에 또 출력하더라고 유지된다.

- set안에 객체들을 다 출력할때는 iterator 클래스를 사용한다.

- 즉, set안에 iterator클래스로 바꾸어주는 .iterator()메소드 존재

- iterator 메소드

  - hasnext()

    다음에 뽑아올 객체가 있는지 없는지 boolean 리턴

  - next()

    다음객체를 뽑아옴

  - remove

    next로 뽑아온 객체를 하나 리스트에서 완전 제거

  ex) iterator<E> ite = aa.iterator(); ->제네릭은 SET도 제네릭을 썼을경우 작성

  ​     while(ite.hasnext()){

  ​		sysout(ite.next())

  ​     }

## Hash

- hashset, map에서 중복값을 방지하기위한 공통점인 hash의 알고리즘 처리방식은

- 먼저 객체를 추가할때 .hascode()로 기존 객체들과의 주소값을 비교하여 같으면 추가x

  똑같으면 equals로 실제 문자열값을 비교하여 같으면 추가x 다르면 그 때 추가

## Map

- (key, value)값으로 객체 하나하나를 구성하며, key는 중복이 안되나, value값은 중복허용
- 즉 map은 안에 key,value로 구성된 Entry객체를 하나씩 put하는 것
- 생성 제네릭타입도 <>두개가 가능
- list, set이 쓰는 add대신 put("","")로 처리
- remove(), get() 메소드는 무조건 키값을 기준으로만 처리 가능
- contains에는 containskey, containsvalue 존재 boolean값 리턴

### key만 불러올때

- key들만을 한꺼번에 다 불러올때는 set클래스 사용

- key값 자체가 set형태로 저장되기에

  ex) Set<E> e = aa.Keyset();

  keyset메소드는 map클래스에 존재

  위 처럼 선언하고 향상된 for문이나 iterator클래스 이용

### value만 불러올때

- value값들만 한꺼번에 다 불러올때는 기존 list처럼

  get메소드가 있으니까 size값만큼 for문 돌리기 

### 둘다 불러올때

- map이 entry객체(key, value)를 저장하는 형식이니까 entry객체를 통채로 set으로 가져옴

  ex) Set<Map.Entry<E, E>> se = map.Entryset();

   그리고 entry통채로 iterator 적용, 향상된 for문x

  Iterator<Map.Entry<E,E>> ite = se.Iterator();

  for(ite.hasnext()){

  ​	Map.Entry<E,E> entry = entryIterator.next();

  ---> 결국 next로 뽑아오는 객체가 entry타입이니까 entry 객체를 생성해서 안에 넣음

  ​	sysout (entry.getkey());

  ​    sysout (entry.getvalue());

  }

- entry 클래스의 메소드는

  - getkey()

    현재 key값 리턴

  - getvalue()

    현재 value값 리턴

## 기타

- system.nanotime - 현재시각을 초 long단위로 리턴
  즉 start end 지정해놓고 걸린 시간 체크할때 씀

