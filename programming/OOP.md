## 객체지향 프로그래밍
프로그래밍에서 필요한 데이터를 추상화시켜 상태와 행위를 가진 객체를 만들고, 객체들 간의 상호작용을 통해 프로그램을 설계하고 개발하는 것
<br>

### 1. 추상화 (Abstraction)
**객체의 공통 속성이나 행위를 하나로 묶는 것**이다. 필요한 것만 남겨서 하나로 묶어야 한다.
자동차로 예를 들면 색, 종류 등은 공통 속성, 달린다, 멈춘다 등은 공통 기능이다.

### 2. 캡슐화 (Encapsulation)
캡슐화는 객체의 속성과 행위를 목적에 맞게 묶어 구성하고, **외부로부터 실제 구현 내용을 감추는 것**이다. 즉, 캡슐화의 목적은 **정보 은닉을 통해 높은 응집도, 낮은 결합도를 유지**할 수 있도록 하는 것이다. 객체의 속성과 행위를 묶어 응집도를 높이는데 이 때 정보 은닉을 하지 않으면 외부에서 객체를 변경할 수 있게되어 객체간 결합도가 높아지게 된다. 
정보 은닉이란 데이터를 접근 지정자(private)을 통해 보호하고 getter/setter를 통해서만 간접적으로 접근하도록 하는 것이다. 즉, 중요한 정보와 객체 내부가 어떻게 구현 되어있는지를 감추어 외부로부터 객체를 보호하고 결합도를 낮춤으로써 변경에 유연하게 하며 유지보수 효율을 높이는 것이다.

### 3. 상속
상속이란 **기존 클래스의 기능을 가져와 재사용할 수 있으면서 동시에 새로운 기능을 추가**할 수 있게 만들어 주는 것이다.

예를 들면, '달린다'라는 기능을 가진 자동차 부모클래스가 존재한다. 이 때, 지붕이 열리는 특수한 기능을 추가하고 싶다면 기존의 자동차를 상속받아 스포차카를 생성할 수 있다. 그러면 스포츠카는 기름도 먹고 달리면서 지붕뚜껑이 열리는 기능도 갖춘 자동차가 되는 것이다.

상속이 필요한 이유는 **코드의 중복을 없애기 위함**이다. 코드의 중복이 많아지면 개발하기에도 힘들지만 유지 보수에서도 많은 비용이 들게 된다. 하지만 상속을 코드 재사용의 개념으로만 이해해서 **지나치게 사용한다면 클래스간(부모클래스와 자식클래스) 결합도가 너무 높아질 수 있다.** 또한, 자식클래스가 상위클래스 메서드를 재정의하려면 **내부 구현을 알아야하므로 캡슐화를 깨뜨리게 될 수 있다.** 그러므로 상속은 클래스의 기능을 재사용해 확장하기보다는 **미완성인 기능을 완성시키위해 사용하는 것이 좋다(유연성 높임).** 즉 **추상 클래스나 인터페이스**로 구현해 이를 상속받아 재정의함으로써 기능을 완성시키는 것이다. 이를 위해서는 **IS-A 관계에서만 상속을 사용**해야 한다(구성X).

이렇게 상속은 사용하기 까다로우므로 **구성을 사용하는 것이 좋다.** 객체 구성은 **객체 내부 필드에서 다른 객체를 참조하는 방식**으로 구현한다(HAS-A 관계). 상속에 비해 런타임 구조가 복잡하고 구현이 어렵지만, **변경시 유연함을 확보할 수 있다**는 장점이 크다. 즉, 같은 종류가 아닌 클래스를 상속하고 싶을 땐, 객체 컴포지션을 먼저 적용해보는 것이 좋다. 그럼에도 불구하고 **상속을 사용하고 싶다면 미래에 변경될 확률이 적은지를 생각**해봐야 한다.

#### 상속 예시 코드
```java
class Car {
	String color;

	public void drive() {
		// 그냥 달림
	}

}

class 슈퍼카 extends Car {
	String color;

	public void open() {
		// 지붕 열림
	}

}
```


### 4. 다형성 (Polymorphism)
**같은 이름의 메소드를 수행했을 때, 다르게 동작하는 것**을 의미한다. 다형성을 통해 유연성을 높일 수 있다.
- 오버로딩 : 같은 이름의 메서드를 매개변수 타입이나 갯수에 따라 다른 용도로 사용하는 것
- 오버라이딩 : 부모클래스로부터 상속받은 메소드를 자식클래스에서 재정의해서 사용하는 것




<br>
<br>

#### Ref.
[1](https://lu-coding.tistory.com/99)
[2](https://velog.io/@cyranocoding/%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8DOOP-Object-Oriented-Programming-%EA%B0%9C%EB%85%90-%EB%B0%8F-%ED%99%9C%EC%9A%A9-%EC%A0%95%EB%A6%AC-igjyooyc6c#%EC%BA%A1%EC%8A%90%ED%99%94encapsulation)
[3](https://velog.io/@hkoo9329/OOPObject-Oriented-Programming-%EA%B0%9D%EC%B2%B4-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%9D%B4%EB%9E%80#%EC%83%81%EC%86%8D%EC%84%B1-%EC%9E%AC%EC%82%AC%EC%9A%A9inheritance)
[4](https://88240.tistory.com/228)
[5](https://wpaud16.tistory.com/94)
