# Polymorphism

## 다형적 변수

> 슈퍼 타입으로 선언된 변수는 모든 자식 객체를 가리킬 수 있음 Object o;



## 오버라이딩

> Shadow effect를 없애서 성능과 확장성을 향상 : 슈퍼의 메소드를 서브에서 재정의

```java
package test3.polymorphism;

public class Triangle extends Shape {
	int width = 5, height =6;
	
	public void area() {
		System.out.println("삼각형의 넓이 : " + (width * height/2));
	}
}	
```

```java
package test3.polymorphism;

public class Rectangle extends Shape {
	int width = 5, height =6;
	
	public void area() {
		System.out.println("사각형의 넓이 : " + (width * height));
	}
}
```

```java
package test3.polymorphism;

public class Circle extends Shape {
	int radius = 4;
	
	public void area() {
		System.out.println("원의 넓이 :" + (3.14 * radius * radius));
	}
}
```

Entity - Data 위주

---



```java
package test3.polymorphism;

public class Shape {
	public void area() { 
		//본래는 데이터, 메소드가 없는 클래스였지만,
		//타입 문제를 해결하기위해 뒤늦게 메소드 추가
	}
}
```

Service/Utility - Method 위주

---



```java
package test3.polymorphism;

public class Printer {
	public void print(Shape s) { // Object o 는 슈퍼타입 원하는 도형을 제외하고도 전부 다 받기 때문에 서브 메소드를 따로 만들어서 원하는 값만 받게 만듦.
		/*절차 중심적 = if else, type checking, type casting은 성능이 떨어짐
		
		if(s instanceof Circle) {   -type checking
			Circle c = (Circle)s;   -type casting
			c.areaCircle();  
		}
		else if (s instanceof Rectangle) {
			Rectangle r = (Rectangle)s;
			r.areaRec();
		}
		else if (s instanceof Triangle) {
			Triangle t = (Triangle)s;
			t.areaTri();
		}*/
		
		//***** 객체 지향적 - 성능과 확장성을 다 잡음
		s.area();
	}
}
```

```java
package test3.polymorphism;

public class Test {

	public static void main(String[] args) {
		Circle c = new Circle();
		Rectangle r = new Rectangle();
		Triangle t = new Triangle();

		Printer out = new Printer();
		out.print(c);
		out.print(r);
		out.print(t);
	}
}
```



## 오버로딩

> 한 클래스내에서 같은 이름의 메소드가 다수 존재하는 것

* Method 이름은 같아야 하고, args의 내용은 달라야함

```java
package test6.constructor;

public class Member {
	private String name, adress, phone;
	private int age;
	
	public Member() {
		super(); // 모든 생성자는 자동으로 super가 생성됨, 명시적으로 표현하면 무조건 첫 번째 줄에 적어야함 다른 줄에 넣으면 에러발생
	}
	
	public Member (String name,String address,String phone,int age) {
		super();
		setName(name);
		setPhone(phone);
		setAdress(address);
		setAge(age);
	}
	// Set method는 유효성 검사를 해야함 !!!!!!!!!
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getAdress() {
		return adress;
	}
	public void setAdress(String adress) {
		this.adress = adress;
	}
	public String getPhone() {
		return phone;
	}
	public void setPhone(String phone) {
		this.phone = phone;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
}
```

```java
package test6.constructor;

public class Test {
	
	public static void main(String [] args) {
		Member m1 = new Member("홍길동","010-1111-1111","경산",25);
		
		Member m2 = new Member("카지노","010-2222-2222","서울",22);

		Member m3 = new Member();
	}
}
```





