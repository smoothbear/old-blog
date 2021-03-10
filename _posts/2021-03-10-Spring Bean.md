---
title: "Bean?"
date: "2021-3-10 21:55:00"
categories:
  - spring boot
---
## Spring Bean

나는 Spring Boot를 시작하면서 Bean이라는 녀석을 처음 접하게 되었다.

생소하기도 하였고, 개념에 쉽게 접근하기 어려웠다.
Bean에 대해 설명하기에 앞서, 먼저 알아야 하는 녀석들이 있다.

## IOC(Inversion Of Control)

Inversion of Control : 제어권 역전(의존관계)
즉, 어떤 객체가 사용할 객체를 직접 선언하는 것이 아닌, 외부에서 사용할 객체를 주입받아
객체간의 의존도를 낮추어 준다.

아래의 예시를 보자.

<일반적인 제어권>
```java
@Service
public class UserService {
  private UserRepository userRepository = new UserRepository();
}
```
<제어권 역전>
```java
@Service
public class UserService {
  private final UserRepository userRepository;

  public UserService(UserRepository userRepostiory) {
     this.userRepository = userRepostiory
  }
}
```
위와 같이 외부에서 생성자를 통해 객체를 주입받고 있다.
* 이를 의존성 주입(DI : Dependency Injection)이라고 한다.

그럼, 의존성 주입을 어떤 것이 해주는 것일까?


## Spring IOC Container
Spring IOC Container란 IOC 기능을 제공해주는 컨테이너이며
Bean을 생성하고, 엮고, 제공해주는 역할을 한다.
BeanFactory나 BeanFactory를 상속받는 클래스가 이 역할을 수행한다.

### BeanFactory??
Bean의 생성과 설정, 관리를 맡고 있는 클래스

## Bean
컨테이너 안에 들어가있는 객체들, 자바 객체들이라고 생각하면 된다.
컨테이너에 담겨있기 때문에, 사용하려면 컨테이너에서 가져와야 한다.

여러 어노테이션들을 사용하면 손쉽게 객체들을 빈으로 등록할 수 있으며,
편리하게 의존성을 주입받을 수 있게 된다.
