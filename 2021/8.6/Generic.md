# Generic

- 객체 생성할때 클래스뒤에 <>로 붙어서 그 객체로 들어오는 타입을 제한하는 것

  ex)

  Generic형태
  class Box<T>{
  	T contents;
  	void setContents(T contents) {
  		this.contents = contents;
  	}
  	
  	T getContents() {
  		return contents;
  	}
  }

  --> 이런 형태로서 기존 클래스에도 <>를 지정하고 T contents처럼 T타입을 받는 모든 멤버

  메소드 등은 Box<String> box = new Box<String>()처럼 string으로 제한된다.

- <>제네릭 타입은 int double처럼 기본타입이 아닌 object를 상속하는 Inteer, Double처럼

  클래스가 들어간다.

- <T, K, A>처럼 제네릭은 여러 타입으로 제한 시킬 수 있음

  - 이경우 T K A 3개 타입으로 제한한다는 뜻

## 기타

- ((Apple)o).origin 이 형태는
  o를 먼저 apple로 강제형변환하고 apple에 있는 origin변수를 수행한다는 뜻

