# Encapsulation

> 데이터 보호장치
>
> private 데이터를 public 메소드를 이용해 핸들링(Setter/Getter)

* private Data + public Method 
* 완전한 데이터 보호 후 메소드를 통해 적절한 접근을 취함

```java
public class Member { //java bean
	private int age;
	private String name;
	
	public void setName(String newName) {
		if(newName == null) {
			System.out.println("이름을 정확히 입력해주세요");
		}
		else {
			name = newName;
		}
	}
	public void setAge(int newAge) { // setter
		// 유효성 검사
		if(newAge > 0) {
			age = newAge;
		}
		else {
			System.out.println("나이는 0보다 커야합니다.");
		}
	}
	public int getAge() { //getter
		return age;
	}
	public String getName() {
		return name;
	}
}
```

```java
public class Test {

	public static void main(String[] args) {
		Member m = new Member();
		m.setName("홍길동");
		m.setAge(25);
		System.out.println(m.getName());
		System.out.println(m.getAge());
	}

}

```

## Modifirer (지정자)

### 접근지정자

* private < default < protected < public

<위치> class

<위치> dataType 이름 (=값)

 <위치> 리턴타입 이름 ( [파라미터 리스트] ) { }

#### private

> 자신의 클래스 내에서만 접근 가능

* class 앞에는 private를 붙일 수 없음 default, public 만 가능

```java
package test1.encapsulation.p1;

public class A {
	private int i = 10;
}
```

```java
package test1.encapsulation.p1;

public class B {

	public static void main(String[] args) {
		A a= new A();
		System.out.println(a.i); //에러발생
	}
}
```

```java
package test1.encapsulation.p2;

import test1.encapsulation.p1.A;

public class C {
	public static void main (String [] args) {
		A a= new A();
		System.out.println(a.i); //에러발생
	}
}
```



#### defalut

> 같은 패키지 내에서만 접근 가능

```java
package test1.encapsulation.p1;

public class A {
	private int i = 10;
}
```

```java
package test1.encapsulation.p1;

public class B {

	public static void main(String[] args) {
		A a= new A();
		System.out.println(a.i); 
	}
}
```

```java
package test1.encapsulation.p2;

import test1.encapsulation.p1.A;

public class C {
	public static void main (String [] args) {
		A a= new A();
		System.out.println(a.i); //에러발생
	}
}
```





#### protected

> 다른 패키지라도 상속관계라면 접근가능
>
> class 앞에는 protected 를 못 붙임. 

```JAVA
package test1.encapsulation.p1;

public class A {
	protected int i = 10;
}
```

```java
package test1.encapsulation.p2;

import test1.encapsulation.p1.A;

public class C extends A {
	public static void main (String [] args) {
        //A a= new A(); 상속관계로 바뀌면 바꿔야 함.
		C a= new C();
		System.out.println(a.i);	
	}
}
```



#### public

> 어디서든 접근 가능



### 사용지정자 

abstract, static, final