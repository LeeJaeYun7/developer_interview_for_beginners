# F-lab 멘토링
<br>

-----------------------

### DispatcherServlet이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/transaction/annotation/Transactional.html] 
+ 
  
</details>


-----------------------

### Spring Bean이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 토비의 스프링 p.101] 
+ 빈 또는 빈 오브젝트는 스프링이 IoC 방식으로 관리하는 오브젝트라는 뜻이다. 
  주의할 점은 스프링을 사용하는 애플리케이션에서 만들어지는 모든 오브젝트가 다 빈은 아니라는 사실이다.
  그 중에서 스프링이 직접 그 생성과 제어를 담당하는 오브젝트만을 빈이라고 부른다. 
  
</details>


-----------------------

### Bean을 만드는 방법은?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: ] 
+ 개발자가 @Bean 어노테이션을 통해 직접 만드는 방법과 
  스프링 컨테이너가 @ComponentScan을 통해 만드는 방법이 있다. 
  
</details>

-----------------------
### 같은 타입으로 Bean이 두 개 이상 등록된 경우, 원하는 Bean을 주입받는 방법은?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 김영한 스프링 기본] 
+ @Autowired 필드 명 매칭
  @Qualifier -> @Qualifier끼리 매칭 -> 빈 이름 매칭
  @Primary 사용 
  이렇게 3가지 방법이 있다.
  
</details>

-----------------------

### `@Transactional`, `@Async` 등의 어노테이션을 사용할 때, Bean의 메서드는 어떻게 추가적인 동작을 할까 ?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: ChatGPT ] 
+ @Transactional과 @Async는 Spring 프레임워크에서 제공하는 어노테이션으로, Bean의 메서드에 추가적인 동작을 할 수 있도록 도와줍니다.

@Transactional:
@Transactional 어노테이션은 메서드 실행을 트랜잭션 내에서 수행하도록 지정합니다. 이 어노테이션을 메서드에 추가하면, 메서드가 호출될 때 Spring은 자동으로 트랜잭션을 시작하고, 메서드가 정상적으로 실행되면 트랜잭션을 커밋(commit)하며, 예외가 발생하면 롤백(rollback)합니다. 따라서 메서드가 여러 개의 데이터베이스 작업 또는 다른 트랜잭션 작업을 수행해야 할 때 유용합니다. @Transactional은 메서드 레벨과 클래스 레벨에서 사용할 수 있습니다. 클래스 레벨에 사용할 경우 해당 클래스의 모든 메서드에 트랜잭션을 적용합니다.

@Async:
@Async 어노테이션은 메서드를 비동기적으로 실행하도록 지정합니다. 즉, 메서드를 호출하면 Spring은 해당 메서드를 별도의 스레드에서 실행하며, 호출자는 메서드의 완료를 기다리지 않고 다음 코드를 실행합니다. 이를 통해 비동기적인 작업을 처리할 수 있으며, 주로 시간이 오래 걸리는 작업이나 외부 서비스 호출 등에 유용합니다. 메서드가 void 형태이거나 Future<T>를 반환하는 경우 사용할 수 있습니다.

이러한 어노테이션을 사용하려면 Spring 애플리케이션에서 다음과 같은 설정이 필요합니다:

@Transactional:

Spring의 트랜잭션 매니저가 적절히 구성되어 있어야 합니다. 일반적으로 @EnableTransactionManagement 어노테이션을 구성 클래스에 추가하여 활성화합니다.
@Async:

Spring의 비동기 실행을 위해 @EnableAsync 어노테이션을 구성 클래스에 추가하여 활성화합니다. 또한, 비동기 작업을 처리할 ThreadPoolTaskExecutor 빈을 구성해야 합니다.
간단한 예시로 @Transactional과 @Async를 함께 사용하는 메서드를 보겠습니다:

java
Copy code
@Service
public class MyService {

    @Autowired
    private MyRepository myRepository;

    @Transactional
    public void doTransactionalMethod() {
        // 여러 데이터베이스 작업을 수행하는 메서드
        // 이 메서드가 예외를 발생시키면 트랜잭션이 롤백됩니다.
        // 그렇지 않으면 커밋됩니다.
    }

    @Async
    public void doAsyncMethod() {
        // 비동기적으로 실행되는 메서드
        // 메서드 호출자는 이 메서드의 실행을 기다리지 않고 다음 코드를 실행합니다.
    }
}
이렇게 하면 Spring은 doTransactionalMethod를 트랜잭션 내에서 실행하고, doAsyncMethod를 비동기적으로 실행합니다.
  
</details>

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

### 연관관계 매핑이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 자바 ORM 표준 JPA 프로그래밍 p.122] 
+ 엔티티들은 대부분 다른 엔티티와 연관관계가 있다. 
  예를 들어, 주문 엔티티는 어떤 상품을 주문했는지 알기 위해 상품 엔티티와 연관관계가 있고,
  상품 엔티티는 카테고리, 재고 등 또 다른 엔티티와 관계가 있다. 
  그런데 객체는 참조(주소)를 사용해서 관계를 맺고 테이블은 외래 키를 사용해서 관계를 맺는다. 
  이 둘은 완전히 다른 특징을 가진다. 
  객체 관계 매핑(ORM)에서 가장 어려운 부분이 바로 객체 연관관계와 테이블 연관관계를 매핑하는 일이다. 
  객체의 참조와 테이블의 외래 키를 매핑하는 것이 이 장의 목표다. 

  시작하기 전에 연관관계 매핑을 이해하기 위한 핵심 키워드를 정리해보았다. 
  진행하면서 하나씩 이해해보자. 
  (1) 방향
  - 단방향, 양방향이 있다. 예를 들어 회원과 팀이 관계가 있을 때, 회원 -> 팀 또는 팀 -> 회원 둘 중 한 쪽만 참조하는 것을
    단방향 관계라 하고, 회원 -> 팀, 팀 -> 회원 양쪽 모두 서로 참조하는 것을 양방향 관계라 한다.
    방향은 객체관계에만 존재하고, 테이블 관계는 항상 양방향이다. 

  (2) 다중성
  - 다대일(N:1), 일대다(1:N), 일대일(1:1), 다대다(N:M) 다중성이 있다.
    예를 들어, 회원과 팀이 있을 때 여러 회원은 한 팀에 속하므로 회원과 팀은 다대일 관계다. 
    반대로 한 팀에 여러 회원이 소속될 수 있으므로 팀과 회원은 일대다 관계다.

  (3) 연관관계의 주인
  - 객체를 양방향 연관관계로 만들면 연관관계의 주인을 정해야 한다. 
  
</details>


-----------------------

### Cascade란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 자바 ORM 표준 JPA 프로그래밍  ] 
+ 특정 엔티티를 영속 상태로 만들 때, 연관된 엔티티도 함께 영속 상태로 만들고 싶으면,
  영속성 전이(transitive persistence) 기능을 사용하면 됩니다. 
  JPA는 CASCADE 옵션으로 영속성 전이를 제공합니다.
  쉽게 말해서 영속성 전이를 사용하면 부모 엔티티를 저장할 때, 자식 엔티티도 함께 저장할 수 있습니다. 

  예제 8.14의 부모 엔티티가 예제 8.15의 여러 자식 엔티티를 가지고 있습니다. 
  JPA에서 엔티티를 저장할 때 연관된 모든 엔티티는 영속 상태여야 합니다. 
  따라서 예제를 보면 부모 엔티티를 영속 상태로 만들고 자식 엔티티도 각각 영속 상태로 만듭니다.
  이럴 때, 영속성 전이를 사용하면 부모만 영속 상태로 만들면 연관된 자식까지 한 번에 영속 상태로 만들 수 있습니다. 

  1) 영속성 전이: 저장 
  영속성 전이를 활성화하는 CASCADE 옵션을 적용해보자. 
  부모를 영속화 할 때 연관된 자식들도 함께 영속화하라고 cascade = CascadeType.PERSIST 옵션을 설정했다.
  이 옵션을 적용하면 예제 8.17처럼 간편하게 부모와 자식 엔티티를 한 번에 영속화할 수 있다. 
  부모만 영속화하면 CascadeType.PERSIST로 설정한 자식 엔티티까지 함께 영속화해서 저장한다.
  데이터베이스에 입력된 데이터를 확인해보자. 

  SELECT * FROM CHILD

  이 코드의 쿼리 결과를 보면 데이터가 정상적으로 2건 입력된 것을 확인할 수 있다.
  쿼리 결과는 표 8.1과 같다. 
  영속성 전이는 연관관계를 매핑하는 것과는 아무 관련이 없다.
  단지 엔티티를 영속화할 때 연관된 엔티티도 같이 영속화하는 편리함을 제공할 뿐이다. 
  그래서 예제 8.17을 보면 양방향 연관관계를 추가한 다음 영속 상태로 만든 것을 확인할 수 있다. 

  2) 영속성 전이: 삭제 
  - 방금 저장한 부모와 자식 엔티티를 모두 제거하려면 다음 코드와 같이 각각의 엔티티를 하나씩 제거해야 한다. 
    영속성 전이는 엔티티를 삭제할 때도 사용할 수 있다.
    CascadeType.REMOVE로 설정하고 다음 코드처럼 부모 엔티티만 삭제하면 연관된 자식 엔티티도 함께 삭제된다.
     
    Parent findParent = em.find(PArent.class, 1L);
    em.remove(findParent);

    코드를 실행하면 DELETE SQL을 3번 실행하고 부모는 물론 연관된 자식도 모두 삭제한다. 
    삭제 순서는 외래 키 제약조건을 고려해서 자식을 먼저 삭제하고 부모를 삭제한다. 

    만약 CascadeType.REMOVE를 설정하지 않고 이 코드를 실행하면 어떻게 될까?
    그러면 부모 엔티티만 삭제된다. 하지만 데이터베이스의 부모 로우를 삭제하는 순간
    자식 테이블에 걸려 있는 외래 키 제약조건으로 인해,
    데이터베이스에서 외래 키 무결성 예외가 발생한다.

  3) CASCADE의 종류
  - 예제 8.18의 CascadeType 코드를 보면 다양한 옵션이 있는 것을 확인할 수 있다.
    public enum CascadeType{
       ALL,
       PERSIST,
       MERGE,
       REMOVE,
       REFRESH,
       DETACH
    }

  - 다음처럼 여러 속성을 같이 사용할 수 있다.
    cascade = {CascadeType.PERSIST, CascadeType.REMOVE}

    참고로 CascadeType.PERSIST, CascadeType.REMOVE는 em.persist(), em.remove()를 실행할 때,
    바로 전이가 발생하지 않고 플러시를 호출할 때 전이가 발생한다. 
</details>


-----------------------

### 고아 객체란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 자바 ORM 표준 JPA 프로그래밍 p.311] 
+ JPA는 부모 엔티티와 연관관계가 끊어진 자식 엔티티를 자동으로 삭제하는 기능을 제공하는데,
  이것을 고아 객체(ORPHAN) 제거라 한다.
  이 기능을 사용해서 부모 엔티티의 컬렉션에서 자식 엔티티의 참조만 제거하면,
  자식 엔티티가 자동으로 삭제되도록 해보자. 

  ```
  @Entity
  public class Parent{

    @Id @GeneratedValue 
    private Long id;

    @OneToMany(mappedBy="parent", orphanRemoval=true)
    private List<Child> children = new ArrayList<Child>();

  ```

  예제 8.19를 보면 고아 객체 제거 기능을 활성화 하기 위해 컬렉션에 orphanRemoval=true를 설정하자.
  이제 컬렉션에서 제거한 엔티티는 자동으로 삭제된다. 
  다음 사용 코드를 보자. 
  Parent parent1 = em.find(Parent.class, id);
  parent1.getChildren().remove(0); // 자식 엔티티를 컬렉션에서 제거 

  실행 결과 SQL은 다음과 같다.
  DELETE FROM CHILD WHERE ID=?

  사용 코드를 보면 컬렉션에서 첫 번째 자식을 제거했다. 
  orphanRemoval=true 옵션으로 인해 컬렉션에서 엔티티를 제거하면 데이터베이스의 데이터도 삭제된다.
  고아 객체 제거 기능은 영속성 컨텍스트를 플러시할 때 적용되므로 플러시 시점에 DELETE SQL이 실행된다. 
  모든 자식 엔티티를 제거하려면 다음 코드처럼 컬렉션을 비우면 된다. 
  parent1.getChildren().clear(); 

  고아 객체를 정리해보자. 고아 객체 제거는 참조가 제거된 엔티티는 다른 곳에서 참조하지 않는 고아 객체로 보고 삭제하는 기능이다. 
  따라서 이 기능은 참조하는 곳이 하나일 때만 사용해야 한다.
  쉽게 이야기해서 특정 엔티티가 개인 소유하는 엔티티에만 이 기능을 적용해야 한다. 
  만약 삭제한 엔티티를 다른 곳에서도 참조한다면 문제가 발생할 수 있다.
  이런 이유로 orphanRemoval은 @OneToOne, @OneToMany에만 사용할 수 있다. 

  고아 객체 제거에는 기능이 하나 더 있는데 개념적으로 볼 때 부모를 제거하면 자식은 고아가 된다. 
  따라서 부모를 제거하면 자식도 같이 제거된다.
  이것은 CascadeType.REMOVE를 설정한 것과 같다. 
  
  
</details>


-----------------------



