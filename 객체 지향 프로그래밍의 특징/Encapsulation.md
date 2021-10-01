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

---

## 생성자

> 객체 생성에 관여( non - static member 초기화)하는 특별한 메소드

---

## Modifirer (지정자)

### Access Modifier (접근지정자)

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

---

### Usage Modifier (사용지정자 )

#### static

> 객체 생성 없이 사용

* class : inner class에서만 사용가능
* data : 공유하는 변수가 됨
* method : 공유하는 메소드가 됨 (안써도 이슈가 없음)

#### final

> 변경없이 사용

* class : 상속불가
* data : 상수 ex) Math.PI
* method : override 불가 

#### abstract

> 상속으로만 사용. 추상적.
>
> data는 없음.

* class : 객체 생성 불가,  상속으로만 사용 강제
* method : override 강제  

- abstract에서 `();`는 호출이 아니라 `선언`

* interface = 다중상속 : implement 

```java
package test1.abstract_;

public abstract class Animal {
	public abstract void eat();
}
```

```java
package test1.abstract_;

public class Human extends Animal {

	@Override
	public void eat() {
		System.out.println("밥을 먹고 산다");
	}
	public void walk() {
		System.out.println("직립보행");
	}
}
```

```java
package test1.abstract_;

public class Superman extends Human implements Flyer {
	@Override
	public void eat() {
		super.eat();
		System.out.println("빵을 먹고 산다");
	}
	public void fly() {
		System.out.println("하늘을 날아다님");
	}
}
```

```java
package test1.abstract_;

public class Test {

	public static void main(String[] args) {
		Superman s = new Superman();
		
		s.eat();
		s.fly();
		s.walk();
	}
}
```















