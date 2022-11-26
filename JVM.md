# JVM
<br>

-----------------------

### JVM이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 자바 가상 머신으로서, 자바 바이트 코드를 OS에 특화된 코드(인터프리터와 JIT 컴파일러)로 변환하여 실행하는 표준 스펙을 의미합니다.  
</details>

-----------------------

### 자바 바이트 코드란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 자바 파일을 컴파일하여 생성되는 .class 파일을 의미합니다. 
</details>

-----------------------

### JRE란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 자바 애플리케이션을 실행할 수 있도록 구성된 배포판을 의미합니다. 
  단, 자바 컴파일러는 포함되지 않습니다. <br>
  JRE는 JVM과 핵심 라이브러리 및 자바 런타임 환경에서 사용하는 프로퍼티 세팅이나 리소스 파일을 갖고 있습니다. 
</details>

-----------------------

### JDK란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ JRE + 개발에 필요한 툴을 의미합니다. 
</details>

-----------------------

### JVM 언어에는 무엇이 있습니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ JVM 기반으로 동작하는 프로그래밍 언어로, 클로저, 그루비, JRuby, Jython, Kotlin, Scala 등이 있습니다.  
</details>

-----------------------

### 클래스 로더란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 로딩, 링크, static 변수 초기화 같은 작업을 하는 JVM의 모듈을 의미합니다.   
</details>

-----------------------

### 메모리의 메소드 영역(=스태틱 영역)이란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 메소드 영역은 클래스 수준의 정보를 저장하고 공유하는 자원입니다. 
</details>

-----------------------

### 메모리의 힙 영역이란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 힙 영역은 객체를 저장하고 공유하는 자원입니다.  
</details>

-----------------------

### 메모리의 스택 영역이란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 스택 영역은 쓰레드 마다 런타임 스택을 만들고,
  그 안에 메소드 호출을 스택 프레임이라 부르는 블럭으로 쌓습니다. 
</details>

-----------------------

### 메모리의 PC 레지스터란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ PC 레지스터는 스레드 마다 스레드 내 현재 실행할 스택 프레임을 가리키는  
  포인터를 의미합니다. 
</details>


-----------------------

### 메모리의 네이티브 메소드 스택이란 무엇입니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 메소드에 네이티브라는 키워드가 붙어 있고, 그 구현을 자바가 아닌<br>
  C나 C++로 한 것을 의미합니다. <br>
  ex) Thread 클래스의 currentThread 메소드
</details>

-----------------------

### 실행 엔진은 무엇으로 구성됩니까? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 인터프리터, JIT 컴파일러, GC로 구성됩니다. 
</details>

-----------------------

### 실행 엔진의 인터프리터의 역할은 무엇입니까? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 인터프리터는 바이트 코드를 한 줄씩 실행합니다. 
</details>

-----------------------

### 실행 엔진의 JIT 컴파일러의 역할은 무엇입니까? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ JIT 컴파일러는 인터프리터 효율을 높이기 위해,<br>
  반복되는 코드를 모두 네이티브 코드로 바꿔두는 역할을 합니다. 
  즉, JIT 컴파일러는 바이트 코드를 네이티브 코드로 컴파일해줍니다. 
</details>

-----------------------

### GC란 무엇입니까? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 더 이상 참조되지 않는 객체를 모아서 정리하는 것을 의미합니다. 
</details>

-----------------------

### 바이트코드 조작 라이브러리에는 무엇이 있는가? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ ASM, Javassist, ByteBuddy 등이 있습니다. 
</details>

-----------------------

### 스프링은 어떻게 컴포넌트 스캔을 하는가? 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+  
</details>

-----------------------
