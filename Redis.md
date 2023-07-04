# Redis
<br>

-----------------------

### Redis vs Memcached?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
 
   1. Redis
  - Redis는 캐시 솔루션 + 저장소입니다. <br>
  - Redis는 Key-value, List, Hash, Set, Sorted Set과 같은 다양한 자료구조를 지원합니다. <br>
  - Redis는 싱글 스레드로 동작합니다. <br>
  - Redis는 트랜잭션, 스냅샷, Replication, Pub/sub, Lua Scripting과 같은 기능을 지원합니다. <br>
   
   2. Memcached 
  - Memcached는 캐시 솔루션입니다.
  - Memcached는 Key-value 자료구조를 지원합니다.
  - Memcached는 멀티 스레드로 동작합니다. 
</details>

-----------------------

### Redis에서 Client-side caching이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
 [참고: https://redis.io/docs/manual/client-side-caching/]

- 클라이언트 측 캐싱은 고성능 서비스를 만드는데 사용되는 기술입니다
  데이터베이스 노드와 비교하여 일반적으로 별개의 컴퓨터인 서버인 애플리케이션 서버에서
  사용 가능한 메모리를 활용하여 데이터베이스 정보의 일부 하위 집합을 애플리케이션 측에 직접 저장합니다.

  일반적으로 데이터가 필요한 경우 애플리케이션 서버는 다음 다이어그램과 같이 이러한 정보에 대해 데이터베이스에 요청합니다.
  +-------------+                                +----------+
|             | ------- GET user:1234 -------> |          |
| Application |                                | Database |
|             | <---- username = Alice ------- |          |
+-------------+                                +----------+
   클라이언트 측 캐싱이 사용되면 애플리케이션은 인기 있는 쿼리의 응답을 애플리케이션 메모리 내부에
   직접 저장하므로 나중에 데이터베이스에 다시 접속하지 않고도 이러한 응답을 재사용할 수 있습니다.
   +-------------+                                +----------+
|             |                                |          |
| Application |       ( No chat needed )       | Database |
|             |                                |          |
+-------------+                                +----------+
| Local cache |
|             |
| user:1234 = |
| username    |
| Alice       |
+-------------+
  - 로컬 캐시에 사용되는 애플리케이션 메모리는 그다지 크지 않을 수 있지만,
    로컬 컴퓨터 메모리에 액세스하는데 필요한 시간은 데이터베이스와 같은
    네트워크 서비스에 액세스하는 것과 비교할 때 훨씬 적습니다.
    동일한 작은 비율의 데이터가 자주 액세스되기 때문에 이 패턴은 애플리케이션이 데이터를
    가져오는 대기 시간과 동시에 데이터베이스 측의 로드를 크게 줄일 수 있습니다.

  - 또한, 항목이 매우 드물게 변경되는 많은 데이터 세트가 있습니다.
    예를 들어, 소셜 네트워크의 대부분의 사용자 게시물은 변경할 수 없거나
    사용자가 거의 편집하지 않습니다 .
    여기에 일반적으로 소수의 게시물이 매우 인기가 있다는 사실을 추가하면
    소수의 사용자가 팔로워가 많거나 최근 게시물의 가시성이 훨씬 높기 때문에
    이러한 패턴이 나타날 수 있는 이유는 분명합니다. 

  - 일반적으로 클라이언트 쪽 캐싱의 두 가지 주요 이점은 다음과 같습니다.
  (1) 매우 짧은 대기 시간으로 데이터를 사용할 수 있습니다
  (2) 데이터베이스 시스템은 더 적은 쿼리를 수신하므로, 더 적은 수의 노드로 동일한 데이터 세트를 제공할 수 있습니다. 
</details>

-----------------------

### Redis Client-side cacheing의 문제점은 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: https://redis.io/docs/manual/client-side-caching/] 
+  
</details>

-----------------------


### Redis Single thread는 어떤 식으로 동작하는가?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+  
</details>

-----------------------


### Redis Pub-sub은 어떤 식으로 동작하는가?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ Pub-sub 패턴이란, Publisher들이 특정한 subscriber를 고려하지 않고 메시지를 생성한 후, <br>
  Publish된 메시지들이 channel로 분류된 후, <br>
  Subscribers는 자신이 관심 있는 channel에 있는 메시지만 받아보는 방식을 의미합니다.<br>
   
  이러한 Publisher와 Subscriber의 디커플링으로 인해 갖게 되는 Pub-sub 패턴의 장점은<br>
  높은 확장성과 다이내믹한 네트워크 토폴로지를 가능하게 한다는 점입니다.  
</details>

-----------------------

