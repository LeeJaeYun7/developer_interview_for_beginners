# F-lab 멘토링
<br>


-----------------------

### @Transactional이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/annotation/Transactional.html] 
+ 개별적인 메소드 혹은 클래스의 트랜잭션 특성을 나타냅니다.
  이것이 클래스 레벨에서 선언되면, 선언된 클래스의 모든 메소드와 서브 클래스에 기본적으로 적용됩니다.
  이것은 클래스 계층 구조의 위쪽, 즉 조상 클래스에는 적용되지 않습니다.
  상속받은 메소드는 서브 클래스 어노테이션에 참여하기 위해서는 지역적으로 재선언되어야 합니다. 
  
</details>


-----------------------

### 트랜잭션 전파레벨이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: https://www.baeldung.com/spring-transactional-propagation-isolation] 
+ 전파레벨은 우리의 비즈니스 로직 트랜잭션의 경계를 정의합니다. 
  스프링은 우리의 전파레벨 세팅에 따라 트랜잭션을 시작하거나 멈춥니다. 
  스프링은 전파레벨에 따라 TransactionManager::getTransaction을 호출해서
  트랜잭션을 얻거나 생성합니다. 
  이것은 모든 타입의 TransactionManager에 대한 전파를 지원하지만,
  그 중에는 TransactionManager의 특정 구현에 의해서만 지원되는 것이 있습니다. 
  각각의 다른 Propagations와 각각이 어떻게 동작하는지 살펴봅시다.

  (1) Required 전파 레벨
  - Required는 기본 전파 레벨입니다. 스프링은 액티브 트랜잭션이 있는지 확인하고,
    아무것도 없다면, 새로운 것을 만듭니다.
    그렇지 않으면, 비즈니스 로직은 현재 액티브 트랜잭션에 종속됩니다.

  (2) Supports 전파 레벨
  - SUPPORTS는, 스프링이 먼저 액티브 트랜잭션이 있는지 확인하고,
    트랜잭션이 존재한다면, 존재하는 트랜잭션이 사용됩니다.
    트랜잭션이 없다면, 이것은 non-transactional로 실행됩니다.
    
  (3) Mandatory 전파 레벨
  - MANDATORY는, 스프링이 먼저 액티브 트랜잭션이 있는지 확인하고,
    트랜잭션이 존재한다면, 존재하는 트랜잭션이 사용됩니다.
    만약 트랜잭션이 없다면, 스프링은 Exception을 던집니다.
    
  (4) Never 전파 레벨
  - Never는, 스프링이 먼저 액티브 트랜잭션이 있는지 확인하고,
    트랜잭션이 존재한다면, 스프링은 Exception을 던집니다.

  (5) Not Supported 전파 레벨
  - Not Supported 전파 레벨은, 만약 현재 트랜잭션이 존재한다면,
    스프링이 그것을 멈추고, 비즈니스 로직이 트랜잭션 없이 실행됩니다.

  (6) Requires new 전파 레벨 
  - Required_new 전파 레벨은, 스프링은 현재 트랜잭션이 존재한다면 중지하고,
    새로운 것을 만듭니다. 
</details>


-----------------------

### 엔티티 매핑이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 자바 ORM 표준 JPA 프로그래밍 p.122] 
+ JPA를 사용하는데 가장 중요한 일은 엔티티와 테이블을 정확히 매핑하는 것입니다. 
  따라서 매핑 어노테이션을 숙지하고 사용해야 합니다. 
  JPA는 다양한 매핑 어노테이션을 지원하는데 크게 4가지로 분류할 수 있습니다. 
  오른쪽에는 대표 어노테이션들을 적어보았습니다. 

  (1) 객체와 테이블 매핑
  - @Entity, @Table
  (2) 기본 키 매핑
  - @Id
  (3) 필드와 컬럼 매핑
  - @Column  
  (4) 연관관계 매핑
  - @ManyToOne, @JoinColumn

(1) @Entity 
- JPA를 사용해서 테이블과 매핑할 클래스는 @Entity 어노테이션을 필수로 붙여야 합니다.
  @Entity가 붙은 클래스는 JPA가 관리하는 것으로, 엔티티라 부릅니다.

  @Entity 적용 시 주의사항은 다음과 같습니다.
  - 기본 생성자는 필수다(파라미터가 없는 public 또는 protected 생성자)
  - final 클래스, enum, interface, inner 클래스에는 사용할 수 없다
  - 저장할 필드에 final을 사용하면 안된다.
    
  JPA가 엔티티 객체를 생성할 때, 기본 생성자를 사용하므로 이 생성자는 반드시 있어야 한다
  자바는 생성자가 하나도 없으면 다음과 같은 기본 생성자를 자동으로 만든다.
  public Member(){} // 기본 생성자
  문제는 다음과 같이 생성자를 하나 이상 만들면 자바는 기본 생성자를 자동으로 만들지 않는다.
  이때는 기본 생성자를 직접 만들어야 한다.

(2) @Table
- @Table은 엔티티와 매핑할 테이블을 지정한다. 생략하면 매핑한 에닡티 이름을
  테이블 이름으로 사용한다.

(3) @Column
- @Column은 객체 필드를 테이블 칼럼에 매핑한다. 가장 많이 사용되고 기능도 많다.
  속성 중에 name, nullable이 주로 사용되고 나머지는 잘 사용되지 않는 편이다.
  
  
</details>


-----------------------
