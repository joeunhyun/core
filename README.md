# Spring 핵심원리 기본편
- Spring 핵심 원리 정리 및 활용
  
## 프로젝트 생성
- java11, SpringBoot 2.5.5, JPA, gradle, Junit 등등  

## 스프링 핵심 원리
* 스프링 진짜 핵심
 스프링은 자바 언어 기반의 프레임워크
 자바 언어의 가장 큰 특징 : 객체 지햔 언어
 스프링은 객체 지향 언어가 가진 강력한 특징을 살려내는 프레임워크
 스프링은 좋은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크

* 좋은 객체 지향?
객체지향프로그래밍? "객체"들의 모임, 객체들이 메세지를 주고 받고 데이터를 처리한다.  
역할과 구현으로 구분하면 세상이 단순해지고, "유연"해지며 "변경"도 편리해진다.  
다형성 : 객체를 설계할 때 역할과 구현을 명확히 분리  
클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있음.  
-> 한계 : 역할(인터페이스) 자체가 변하면, 클라이언트, 서버 모두에 큰 변경이 발생  

* 스프링과 객체 지향
 스프링은 다형성을 극대화해서 이용할 수 있게 도와줌.
 스프링에서 IoC, DI는 다형성을 활용해서 역할과 구현을 편리하게 다룰 수 있도록 지원

 ### 좋은 객체 지향 설계의 5가지 원칙(SOLID)
1. SRP 단일 책임 원칙   
  한 클래스는 하나의 책임만 가져야한다.
  중요한 기준은 변경이다. 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것
2. OCP 개방-폐쇄 원칙 (***)  
  소프트웨어 요소는 확장에는 열려 있으나 (구현체) 변경에는 닫혀 (인터페이스) 있어야한다.
  다형성을 활용, 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현
  구현 객체를 변경하려면 클라이언트 코드를 변경해야한다. 분명 다형성을 사용했지만 OCP가 깨짐
   -> 해결방법? 객체를 생성하고, 연관관계를 맺어주는 별도의 조립, 설정자 필요 (스프링 컨테이너 역할)
3. LSP 리스코프 치환 원칙  
  프로그램의 객체는 프로그래밍의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야함
4. ISP 인터페이스 분리 원칙  
  특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다
5. DIP 의존관계 역전 원칙  
  역할에 의존하게 해야 한다는 것, 클라이언트가 인터페이스에 의존해야 유현하게 구현체를 변경할 수 있다.
  
## 비즈니스 요구사항과 설계
### 회원
* 회원을 가입하고 조회할 수 있다.  
* 회원은 일반과 VIP 두 가지 등급이 있다. 
* 회원 데이터는 자체 DB를 구축할 수 있고, 외부 시스템과 연동할 수 있다. (미확정)
### 주문과 할인 정책
* 회원은 상품을 주문할 수 있다.
* 회원 등급에 따라 할인 정책을 적용할 수 있다.
* 할인 정책은 모든 VIP는 1000원을 할인해주는 고정 금액 할인을 적용해달라. (나중에 변경 될 수 있다.)
* 할인 정책은 변경 가능성이 높다. 회사의 기본 할인 정책을 아직 정하지 못했고, 오픈 직전까지 고민을
  미루고 싶다. 최악의 경우 할인을 적용하지 않을 수 도 있다. (미확정)

![image](https://user-images.githubusercontent.com/83958409/137315081-e7c46c87-d21b-4cef-92e4-6dd55de75adc.png)
![img.png](img.png)


