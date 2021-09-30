# Inheritance

> extends Only One SuperClass
>
> `Super` member를 물려받는 것 (extends `Super`-단일상속)
>
> 상속이 많아지면 뿌리가 되는 데이터,메소드를 찾기 모호해지기 때문에 단일 상속을 함

* 단일상속
  * Super의 모든 멤버(data, method)를 물려 받는 것
  * private member, 생성자 --> 상속 불가능 

```JAVA
package test1.encapsulation.p2;

import test1.encapsulation.p1.A, *B*; //안됨!!!!!

public class C extends A {
	public static void main (String [] args) {
		C a= new C();
		System.out.println(a.i);	
	}
}
```



상속의 관계를 잘 설정해야함 Person -> Member ->(VipMember/BlackListMember)

```java
package test2.inheritance;

public class Person {
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

```



다른 패키지의 Person을 받아서 사용하겠다는 의미

```java
package test1.encapsulation;

import test2.inheritance.Person; //import 받아서 사용하겠다

public class Member extends Person{
}
```



다른패키지의 Member를 받아서 사용하겠다는 의미

```java
package test2.inheritance;

import test1.encapsulation.Member; //import 받아서 사용하겠다

public class VipMember extends Member {
    private int point = 1000;
    	public int getPoint() {
		return point;
	}

	public void setPoint(int point) {
        //유효성 검사
		if(point>1000) {
		this.point = point;
		}
		else {
			System.out.println("1000보다만 큰 값만 입력되어야 합니다.");
		}
	}
}
```



다른패키지의 VipMember를 받아서 사용하겠다는 의미

```java
package test1.encapsulation;

import test2.inheritance.VipMember; //import 받아서 사용하겠다

public class Test {

	public static void main(String[] args) {
		Member m = new Member();
		m.setName("홍길동");
		m.setAge(25);
		System.out.println(m.getName());
		System.out.println(m.getAge());
		
		
		VipMember vm = new VipMember();
		vm.setPoint(0);
		System.out.println(vm.getPoint());
	}
}
```



상단 source -> generate setter and getter -> point 체크 -> 실행

자동적으로 setter & getter 코딩

* 유효성 검사 (If / else)를 넣어서 좋은 코드를 만들어야 합니다.

public 과 private를 잘 구분해서 사용해야 합니다.