---

title: "Prototype Pattern"
excerpt: "프로토타입 패턴은 객체를 생성하는게 비용이 많이 들고 이미 유사한 객체가 존재하는 경우에(더 나아가 기존의 객체와 거의 유사한 객체를 만들고자 할 때) 사용하는 패턴이다." 

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

### Prototype Pattern

프로토타입 패턴은 객체를 생성하는게 비용이 많이 들고 이미 유사한 객체가 존재하는 경우에(더 나아가 기존의 객체와 거의 유사한 객체를 만들고자 할 때) 사용하는 패턴이다. 구현 방식은 clone()메소드를 사용하여 복제하는데 이 방식은 subclass로 상속받거나 new 키워드를 사용하는 방식과 다른 방식이다. 코드로 보면 다음과 같다. 

```java
public class Employees implements Cloneable{
 
    private List<String> empList;
	
    public Employees(){
        empList = new ArrayList<String>();
    }
	
    public Employees(List<String> list){
        this.empList=list;
    }
    
    public void loadData(){
        //read all employees from database and put into the list
        empList.add("Pankaj");
        empList.add("Raj");
        empList.add("David");
        empList.add("Lisa");
    }
	
    public List<String> getEmpList() {
        return empList;
    }
 
    @Override
    public Object clone() throws CloneNotSupportedException{
        List<String> temp = new ArrayList<String>();
        for(String s : this.empList){
            temp.add(s);
        }
        return new Employees(temp);
    }
	
}
```

위의 코드는 clone() method를 재정의하기 위해 Cloneable 인터페이스를 구현한 것이다. 이렇게 clone() 메서드를 사용하게 되면 내부적으로 원래의 객체와 같은 크기의 메모리를  확보하고 그 객체의 필드 내용을 복사하는 방식으로 deep copy가 이루어진다. CloneNotSupportedException이 발생하는 경우는 Cloneable인터페이스를 구현하지 않는 클래스의 객체가 clone() 메서드를 호출하는 경우이다. 

```java
public class PrototypePatternTest {
 
    public static void main(String[] args) throws CloneNotSupportedException {
        Employees emps = new Employees();
        emps.loadData();
		
        //Use the clone method to get the Employee object
        Employees empsNew = (Employees) emps.clone();
        Employees empsNew1 = (Employees) emps.clone();
        List<String> list = empsNew.getEmpList();
        list.add("John");
        List<String> list1 = empsNew1.getEmpList();
        list1.remove("Pankaj");
		
        System.out.println("emps List: "+emps.getEmpList());
        System.out.println("empsNew List: "+list);
        System.out.println("empsNew1 List: "+list1);
    }
 
}
```

![image](https://user-images.githubusercontent.com/54565079/119046800-188f3b00-b9f8-11eb-8490-1bfe77057a85.png)

Main에서 테스트해 보았다. clone() 메서드를 통해 deep copy가 이루어지고 있는 것을 확인할 수 있다. 예시에서 알 수 있듯이 프로토타입 패턴을 사용하면 큰 틀은 유지한 채 사소한 부분만 변경한 객체를 deep copy로 생성할 수 있다. 만약에 위의 예시에서 프로토타입 패턴을 사용하지 않았다면 매번 employee 리스트를 가져와야 했을 것이다. 하지만 clone() 메서드를 사용함으로서 적은 비용으로 기존 정보들을 유지한 채 객체를 생성할 수 있었다. 



### 응용

~~~java
abstract class Prototype implements Cloneable {
        @Override
        public Prototype clone() throws CloneNotSupportedException {
                return (Prototype)super.clone();
        }

        public abstract void setX(int x);

        public abstract void printX();

        public abstract int getX();
}
~~~

~~~java
class PrototypeImpl extends Prototype {
        int x;

        public PrototypeImpl(int x) {
                this.x = x;
        }

        public void setX(int x) {
                this.x = x;
        }

        public void printX() {
                System.out.println("Value :" + x);
        }

        public int getX() {
                return x;
        }
}
~~~

~~~java
public class PrototypeTest {
        public static void main(String args[]) throws CloneNotSupportedException {
                Prototype prototype = new PrototypeImpl(1000);

                for (int i = 1; i < 10; i++) {
                        Prototype tempotype =  prototype.clone();

                        tempotype.setX( tempotype.getX() * i);
                        tempotype.printX();
                }
        }
}
~~~

![image](https://user-images.githubusercontent.com/54565079/119048426-2940b080-b9fa-11eb-8588-9440690874d6.png)

![image](https://user-images.githubusercontent.com/54565079/119048917-dc110e80-b9fa-11eb-943d-3e2a33987e69.png)

clone()메서드를 구현한 클래스를 추상 클래스로 만들어서 subclass(PrototypeImpl)에서 구체적으로 자잘한 메서드를 구현할 수 있도록 할 수 있다. 이때 추상클래스를 원형(Prototype), 추상클래스를 구현하는 클래스를 구체적인 원형(Concrete Prototype), 그리고 구체적인 원형에 정의된 메서드를 이용해 새로운 객체를 생성하는 곳을 이용자(Client)라고 한다. clone() 메서드는 원형 타입의 객체를 clone하는 객체가 기존의 객체를 clone하도록 (원형타입)super.clone()로 구현해주면 된다. 

프로토타입 패턴과 비교되는 패턴은 싱글톤 패턴인데 무조건 하나의(같은) 객체만 리턴해주는 방식이다. 



### 출처

- <https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85_%ED%8C%A8%ED%84%B4>
- <https://readystory.tistory.com/122>
- <https://yssa.tistory.com/entry/Design-Pattern-%EC%8B%B1%EA%B8%80%ED%86%A4Singleton-%ED%8C%A8%ED%84%B4%EA%B3%BC-%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85Prototype-%ED%8C%A8%ED%84%B4>















