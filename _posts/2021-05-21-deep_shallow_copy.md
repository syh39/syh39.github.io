---

title: "Shallow Copy vs Deep Copy"
excerpt: "코드를 짤 때 객체를 복사를 해야하는 경우가 자주 생기는데 이때 복사를 하는 방식에는 Shallow Copy와 Deep Copy 두가지 방식이 있다." 

categories:
  - OODP
tags:
  - OODP
last_modified_at: 2021-05-21 
toc: true
toc_label: "Contents"
toc_icon: "cog"
toc_sticky: true
---

### Shallow Copy vs Deep Copy

코드를 짤 때 객체를 복사를 해야하는 경우가 자주 생기는데 이때 복사를 하는 방식에는 Shallow Copy와 Deep Copy 두가지 방식이 있다. 둘의 차이를 요약하자면 Shallow Copy는 주소값을 복사하는 방식이고 Deep Copy는 새로운 메모리 공간에 값을 복사하는 방식이다. 코드상으로는 다음과 같다. 



### Shallow Copy

```java
public class YohanCoding {
	String name;
	long money;
	
	public YohanCoding(String name, long money) {
		this.name = name;
		this.money = money;
	}
	
	public void changeName(String name) {
		this.name = name;
	}
	
	public void spend(int money) {
		this.money -= money;
	}

	@Override
	public String toString() {
		return "YohanCoding [name=" + name + ", money=" + money + "]";
	}
}
```

YohanCoding이라는 클래스를 만든다.  YohanCoding이라는 클래스는 이름과 현재 가지고 있는 돈을 변수로 가지고 있다. 

```java
public class Main {

	public static void main(String[] args) {

		YohanCoding yohan = new YohanCoding("yohan", 10000); 
		// yohan이라는 이름의 객체 생성
		YohanCoding yohanCopy = yohan; 
		// yohanCopy라는 이름의 객체에 yohan 객체를 복사
		
		yohan.changeName("coding");
		yohan.spend(3000);
		
		System.out.println(yohan);
		System.out.println(yohanCopy);

	}
}

```

![image](https://user-images.githubusercontent.com/54565079/119037265-b846cc00-b9ec-11eb-8ae1-09c851311682.png)

Main에서 테스트해 보았다. yohan이라는 객체를 "yohan", 10000 이라는 값으로 먼저 생성후 yohanCopy라는 객체에 복사를 하였다. 그리고 나서 yohan객체를 수정하고 yohan과 yohanCopy를 동시에 출력해보니 yohan과 yohanCoding 모두 변경된 yohan의 값들을 출력하고 있었다. 복사를 하고 나서 yohan을 수정했는데 yohanCoding의 값도 같이 바뀐 이유는 값만 복사한게 아니라 주소값을 복사했기 때문이다. 메모리상으로 더 자세히 보면 다음과 같다. 

![image](https://user-images.githubusercontent.com/54565079/119039153-e3cab600-b9ee-11eb-90d5-0776091a94c0.png)

객체를 생성하는 순간 주소값은 stack에, 실제 값은 heap에 올라가게 된다. 객체를 바로 '=' 연산자로 복사하게 되면 객체는 별도의 메모리 공간에 값을 저장하는 것이 아닌 같은 메모리 공간을 가리키게 된다. 이 상태에서는 yohan을 수정하든, yohanCopy를 수정하든 두개의 객체를 출력했을 때에 같은 값이 나오게 된다. 만약에 이러한 결과가 아닌 아예 다른 메모리 공간을 사용하는 객체로 복사하길 원한다면 Deep Copy를 사용해야 한다. 

Deep Copy는 크게

1. 복사 생성자 or 복사 팩토리
2. 직접 객체를 생성
3. Clonable Interface를 구현하여 clone() 재 정의

이렇게 3가지 방식으로 구현할 수 있다. 



### Deep Copy

**1. 복사 생성자 / 복사 팩토리**

```java
public class YohanCoding {
	String name;
	long money;
	
	public YohanCoding(YohanCoding yohanCoding) {
        this.name = yohanCoding.name;        
        this.money = yohanCoding.money;
    } // 복사 생성자
    // Main에서는 YohanCoding yohanCopy = new YohanCoding(yohan);
    
    public static YohanCoding newInstance(YohanCoding yohanCoding) {
        YohanCoding y = new YohanCoding();
        y.name = yohanCoding.name;
        y.money = yohanCoding.money;
        return y;
    } // 복사 팩토리
    // Main에서는 YohanCoding yohanCopy = YohanCoding.newInstance(yohan);
}
```



**2. 직접 객체를 생성**

```java
public class Main {

	public static void main(String[] args) {

		YohanCoding yohan = new YohanCoding("yohan", 10000); 
		// yohan이라는 이름의 객체 생성
		YohanCoding yohanCopy = new YohanCoding(); 
		// yohanCopy라는 이름의 객체 생성(값 없는 상태 / 주소 다름)
		
		yohanCopy.setName(yohan.getName());
        yohanCopy.setMoney(yohan.getMoney());
        // 값만 복사

	}
}
```

객체를 생성하고 복사하고자 하는 객체의 값을 직접 가져와서 정직하게 세팅하는 방식이다.



**3. Clonable Interface를 구현하여 clone() 재 정의**

```java
public class YohanCoding2 implements Cloneable {
	String name;
	long money;
	
	public YohanCoding2(String name, long money) {
		this.name = name;
		this.money = money;
	}
	
	public void changeName(String name) {
		this.name = name;
	}
	
	public void spend(int money) {
		this.money -= money;
	}
	
	@Override
	public String toString() {
		return "YohanCoding [name=" + name + ", money=" + money + "]";
	}
	
	@Override
	protected YohanCoding2 clone() throws CloneNotSupportedException {
		// TODO Auto-generated method stub
		return (YohanCoding2) super.clone();
	} // 이클립스 기준 구현되지 않은 인터페이스 메서드를 자동으로 오버라이딩 하는 단축키는 alt + shift + s이다
	
}




public class Main {

	public static void main(String[] args) throws CloneNotSupportedException {

		YohanCoding2 yohan = new YohanCoding2("yohan", 10000);
		YohanCoding2 yohanCopy = yohan.clone();
		
		yohan.changeName("coding");
		yohan.spend(3000);
		
		System.out.println(yohan);
		System.out.println(yohanCopy);
		
	}
}

```

![image](https://user-images.githubusercontent.com/54565079/119042479-dca5a700-b9f2-11eb-9009-93f367d2e5ae.png)



Deep Copy의 메모리상의 결과는 다음과 같다.

![image](https://user-images.githubusercontent.com/54565079/119043154-b5030e80-b9f3-11eb-96ec-59cfd8dbb8d1.png)





### 출처

- <https://jackjeong.tistory.com/100>















