# Network
<br>

### HTTP란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.3] 
   
+ 전 세계의 웹 브라우저, 서버, 웹 애플리케이션은 모두 HTTP(Hypertext Transfer Protocol)를 통해 서로 대화합니다. <br> 
  HTTP는 현대 인터넷의 공용어입니다. <br> 
  이 장은 HTTP를 간결하게 설명합니다. 독자들은 얼마나 많은 웹 애플리케이션이 HTTP를 이용해 통신하고, <br>
  HTTP가 어떻게 그 일을 해내는지 개략적으로 알게 될 것입니다. <br> 
  특히 다음에 대해 이야기할 것입니다. <br> 
  
  (1) 얼마나 많은 클라이언트와 서버가 통신하는지 <br>
  (2) 리소스(웹 콘텐츠)가 어디서 오는지 <br> 
  (3) 웹 트랜잭션이 어떻게 동작하는지 <br> 
  (4) HTTP 통신을 위해 사용하는 메시지의 형식 <br> 
  (5) HTTP 기저의 TCP 네트워크 전송 <br> 
  (6) 여러 종류의 HTTP 프로토콜 <br> 
  (7) 인터넷 곳곳에 설치된 다양한 HTTP 구성 요소 <br> 
   
  공부할 거리를 충분히 확보했으니, 이제 HTTP의 세계로 여행을 떠나보자. <br>  
  
</details>

-----------------------

### HTTP가 인터넷의 멀티미디어 배달부라는 것이 무엇인가?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.4] 
   
+ 수십억 개의 JPEG 이미지, HTML 페이지, 텍스트 파일, MPEG 동영상, WAV 음성 파일, 자바 애플릿 등이 하루도 쉬지 않고 인터넷을 항해합니다. <br>
  HTTP는 전 세계의 웹 서버로부터 이 대량의 정보를 빠르고, 간편하고, 정확하게 사람들의 PC에 설치된 웹브라우저로 옮겨줍니다. <br> 
  
  HTTP는 신뢰성 있는 데이터 전송 프로토콜을 사용하기 때문에, 데이터가 지구 반대편에서 오더라도 전송 중 손상되거나 꼬이지 않음을 보장합니다. <br> 
  이 덕분에 사용자는 인터넷에서 얻은 정보가 손상된 게 아닌지 염려하지 않아도 됩니다. <br> 
  신뢰성 있는 전송은 인터넷 애플리케이션 개발자에게도 이로운데, <br> 
  
  HTTP 통신이 전송 중 파괴되거나, 중복되거나, 왜곡되는 것을 걱정하지 않아도 되기 때문입니다. <br> 
  개발자는 인터넷의 결함이나 약점에 대한 걱정 없이 애플리케이션 고유의 기능을 구현하는데 집중할 수 있습니다. <br>  
  
</details>

-----------------------



### HTTP는 웹 트래픽을 어떻게 전송합니까?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.4] 
   
+ 웹 콘텐츠는 웹 서버에 존재합니다. 웹 서버는 HTTP 프로토콜로 의사소통하기 때문에, 보통 HTTP 서버라고 불립니다. <br> 
  이들 웹 서버는 인터넷의 데이터를 저장하고, HTTP 클라이언트가 요청한 데이터를 제공합니다. <br> 
  그림 1-1에 그려진 대로, 클라이언트는 서버에게 HTTP 요청을 보내고, <br>
  서버는 요청된 데이터를 HTTP 응답으로 돌려줍니다. <br> 
  HTTP 클라이언트와 HTTP 서버는 월드 와이드 웹의 기본 요소입니다. <br> 
  
  아마 독자들은 HTTP 클라이언트를 매일 이용하고 있을 것입니다. <br> 
  가장 흔한 클라이언트는 마이크로소프트 인터넷 익스플로러나 구글 크롬 같은 웹브라우저입니다. <br> 
  웹브라우저는 서버에게 HTTP 객체를 요청하고 사용자의 화면에 보여줍니다. <br> 
   
  예를 들어, "http://www.oreilly.com/index.html" 페이지를 열어볼 때, <br>
  웹브라우저는 HTTP 요청을 www.oreilly.com 서버로 보냅니다. <br> 
  서버는 요청 받은 객체(이 경우 "/index.html")를 찾고, 성공했다면 그것의 타입, 길이 등의 정보와 함께 <br>
  HTTP 응답에 실어서 클라이언트에게 보냅니다. <br> 
</details>

-----------------------

### 리소스란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.5] 
   
+ 웹서버는 웹 리소스를 관리하고 제공합니다. 웹 리소스는 웹 콘텐츠의 원천입니다. 가장 단순한 웹 리소스는 웹 서버 파일 시스템의 정적 파일입니다. <br> 
  정적 파일은 텍스트 파일, HTML 파일, 마이크로소프트 워드 파일, 어도비 아크로뱃 파일, JPEG 이미지 파일, AVI 동영상 파일, 그 외 모든 종류의 파일을 포함합니다. <br> 
  그러나 리소스는 반드시 정적 파일이어야 할 필요는 없습니다. 리소스는 요청에 따라 콘텐츠를 생산하는 프로그램이 될 수도 있습니다. <br> 
  이들 동적 콘텐츠 리소스는 사용자가 누구인지, 어떤 정보를 요청했는지, 몇 시인지에 따라 다른 콘텐츠를 생성합니다. <br> 
  또 카메라에서 라이브 영상을 가져와 보여주거나, 주식 거래, 부동산 데이터베이스 검색, 온라인 쇼핑몰에서 선물 구입을 할 수 있게 해줄 수도 있습니다. <br>  
  요약하자면, 어떤 종류의 콘텐츠 소스도 리소스가 될 수 있습니다. <br> 
  예컨대, 기업 판매 예측 스프레드시트 파일은 리소스입니다. 지역 공공 도서관의 서가를 탐색하는 웹 게이트웨이도 리소스입니다. <br> 
  인터넷 검색엔진 역시 리소스입니다. <br> 
</details>

-----------------------

### 미디어 타입이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.6] 
   
+ 인터넷은 수천 가지 데이터 타입을 다루기 때문에, HTTP는 웹에서 전송되는 객체 각각에 신중하게 MIME 타입이라는 데이터 포맷 라벨을 붙입니다. <br> 
  MIME(Multipurpose Internet Mail Extensions, 다목적 인터넷 메일 확장)은 원래 각기 다른 전자메일 시스템 사이에서 메시지가 오갈 때 겪는 문제점을 해결하기 위해 <br>
  설계되었습니다. MIME는 이메일에서 워낙 잘 동작했기 때문에, HTTP에서도 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해 채택되었습니다. <br> 
   
  웹 서버는 모든 HTTP 객체 데이터에 MIME 타입을 붙입니다. 웹브라우저는 서버로부터 객체를 돌려받을 때, 다룰 수 있는 객체인지 MIME 타입을 통해 확인합니다. <br> 
  대부분의 웹브라우저는 잘 알려진 객체 타입 수백 가지를 다룰 수 있습니다. <br> 
  이미지 파일을 보여주고, HTML 파일을 분석하거나 포맷팅하고, 오디오 파일을 컴퓨터의 스피커를 통해 재생하고, 특별한 포맷의 파일을 다루기 위해 외부 플러그인 소프트웨어 <br>
  를 실행합니다. <br> 
   
  MIME 타입은 사선(/)으로 구분된 주 타입(primary object type)과 부 타입(specific subtype)으로 이루어진 문자열 라벨입니다. <br> 
  예를 들면, 다음과 같습니다. <br> 
   
  (1) HTML로 작성된 텍스트 문서는 text/html 라벨이 붙습니다. <br> 
  (2) plain ASCII 텍스트 문서는 text/plain 라벨이 붙습니다. <br> 
  (3) JPEG 이미지는 image/jpeg가 붙습니다. <br> 
  (4) GIF 이미지는 image/gif가 됩니다. <br>
  (5) 애플 퀵타임 동영상은 vidoe/quicktime이 붙습니다. <br>
  (6) 마이크로소프트 파워포인트 프레젠테이션은 application/vnd.ms-powerpoint가 붙습니다. <br>
   
  수백 가지의 잘 알려진 MIME 타입과, 그보다 더 많은 실험용 혹은 특정 용도의 MIME 타입이 존재합니다. <br>
  MIME 타입 전체 목록은 부록 D에 실려 있습니다. <br> 
</details>

-----------------------

### URI란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.7] 
   
+ 웹 서버 리소스는 각자 이름을 갖고 있기 때문에, 클라이언트는 관심 있는 리소스를 지목할 수 있습니다. <br> 
  서버 리소스 이름은 통합 자원 식별자(uniform resource identifier) 혹은 URI로 불립니다. <br>
  URI는 인터넷의 우편물 주소 같은 것으로, 정보 리소스를 고유하게 식별하고 위치를 지정할 수 있습니다. <br> 
   
  '죠의 컴퓨터 가게'의 웹 서버에 있는 이미지 리소스에 대한 URI라면 이런 식입니다. <br>
   
   ```
    http://www.joes-hardware.com/specials/saw-blade.gif
   ```
   그림 1-4는 죠의 컴퓨터 가게 서버에 있는 GIF 형식의 톱날 그림 리소스에 대한 URI가 HTTP 프로토콜에서 어떻게 해석되는지 보여줍니다. <br> 
   HTTP는 주어진 URI로 객체를 찾아옵니다. <br> 
   URI에는 두 가지가 있는데, URL과 URN이라는 것입니다. 
</details>

-----------------------

### URL이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.8] 
   
+ 통합 자원 지시자(Uniform Resource Locator, URL)는 리소스 식별자의 가장 흔한 형태입니다. <br>
  URL은 특정 서버의 한 리소스에 대한 구체적인 위치를 서술합니다. <br> 
  URL은 리소스가 정확히 어디에 있고 어떻게 접근할 수 있는지 분명히 알려줍니다. <br> 
  그림 1-4는 어떻게 URL로 리소스의 정확한 위치와 접근방법을 표현하는지 보여줍니다. <br> 
  표 1-1은 URL의 몇 가지 예입니다. <br>
   
  대부분의 URL은 세 부분으로 이루어진 표준 포맷을 따릅니다. <br> 
  (1) URL의 첫 번째 부분은 스킵(scheme)이라고 불리는데, 리소스에 접근하기 위해 사용되는 프로토콜을 서술합니다. <br> 
      보통 HTTP 프로토콜(http://)입니다. <br>
  (2) 두 번째 부분은 서버의 인터넷 주소를 제공합니다.(ex) www.joes-hardware.com) <br>
  (3) 마지막은 웹 서버의 리소스를 가리킵니다( ex) /specials/saw-blade.fig). <br>
   
  - 오늘날 대부분의 URI는 URL입니다. <br> 
</details>

-----------------------

### HTTP 트랜잭션이란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.9] 
   
+ 클라이언트가 웹 서버와 리소스를 주고 받기 위해 HTTP를 어떻게 사용하는지 좀 더 자세히 알아보자. <br> 
  HTTP 트랜잭션은 요청 명령(클라이언트에서 서버로 보내는)과 응답 결과(서버가 클라이언트에게 돌려주는)로 구성되어 있습니다. <br> 
  이 상호작용은 그림 1-5에 묘사된 것과 같이 HTTP 메시지라고 불리는 정형화된 데이터 덩어리를 이용해 이루어집니다. <br> 
</details>

-----------------------

### HTTP 메서드란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.9] 
   
+ HTTP는 HTTP 메서드라고 불리는 여러 가지 종류의 요청 명령을 지원합니다. <br> 
  모든 HTTP 요청 메시지는 한 개의 메서드를 갖습니다. <br> 
  메서드는 서버에게 어떤 동작이 취해져야 하는지 말해줍니다. (웹 페이지 가져오기, 게이트웨이 프로그램 실행하기, 파일 삭제하기 등) <br> 
  표 1-2는 흔히 쓰이는 HTTP 메서드 다섯 개를 열거하고 있습니다. <br> 
   
  (1) GET - 서버에서 클라이언트로 지정한 리소스를 보내라. <br> 
  (2) PUT - 클라이언트에서 서버로 보낸 데이터를 지정한 이름의 리소스를 저장하라. <br> 
  (3) DELETE - 지정한 리소스를 서버에서 삭제하라 <br> 
  (4) POST - 클라이언트 데이터를 서버 게이트웨이 애플리케이션으로 보내라 <br> 
  (5) HEAD - 지정한 리소스에 대한 응답에서, HTTP 헤더 부분만 보내라 <br> 
   
</details>

-----------------------

### HTTP 상태 코드란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.10] 
   
+ 모든 HTTP 응답 메시지는 상태 코드와 함께 반환됩니다. <br> 
  상태 코드는 클라이언트에게 요청이 성공했는지 아니면 추가 조치가 필요한지 알려주는 세 자리 숫자입니다. <br> 
  흔히 쓰이는 상태 코드 몇 가지가 표 1-3에 나와 있습니다. <br>
  
  (1) 200 - 좋다. 문서가 바르게 반환되었다. <br>
  (2) 302 - 다시 보내라. 다른 곳에 가서 리소스를 가져가라 <br>
  (3) 404 - 없음. 리소스를 찾을 수 없음 <br> 
   
  HTTP는 각 숫자 상태 코드에 텍스트로 된 사유 구절도 함께 보냅니다. <br> 
  이 구문은 단지 설명만을 위해서 포함된 것일 뿐 실제 응답 처리에는 숫자로 된 코드가 사용됩니다. <br> 
  HTTP 소프트웨어는 다음에 열거된 상태 코드와 사유 구절을 모두 같은 것으로 취급합니다. <br> 
   
  200 OK
  200 Document attached
  200 Success
  200 All's cool, dude
</details>

-----------------------

### 웹 페이지가 여러 객체로 이루어질 수 있다는 것이 무엇인가?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.10] 
   
+ 애플리케이션은 보통 하나의 작업을 수행하기 위해 여러 HTTP 트랜잭션을 수행합니다. <br> 
  예를 들어, 웹브라우저는 시각적으로 풍부한 웹페이지를 가져올 때, 대량의 HTTP 트랜잭션을 수행합니다. <br>
  페이지 레이아웃을 서술하는 HTML '뼈대'를 한 번의 트랜잭션으로 가져온 뒤, <br>
  첨부된 이미지, 그래픽 조각, 자바 애플릿 등을 가져오기 위해 추가로 HTTP 트랜잭션들을 수행합니다. <br> 
   
  이 리소스들은 그림 1-6에 묘사된 것과 같이 다른 서버에 위치할 수도 있습니다. <br>
  이와 같이 '웹페이지'는 보통 하나의 리소스가 아닌 리소스의 모음입니다. <br> 
</details>

-----------------------

### HTTP 메시지란? (1장)

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.11] 
   
+ 이제 HTTP 요청과 응답 메시지의 구조를 살짝 들여다봅니다. <br> 
  우리는 3장에서 HTTP 메시지를 자세히 공부할 것입니다. <br> 
  HTTP 메시지는 단순한 줄 단위의 문자열입니다. 이진 형식이 아닌 일반 텍스트이기 때문에 사람이 읽고 쓰기 쉽습니다. <br> 
  그림 1-7은 간단한 트랜잭션에 대한 HTTP 메시지를 보여주고 있습니다. <br> 
   
  웹 클라이언트에서 웹 서버로 보낸 HTTP 메시지를 요청 메시지라고 부릅니다. <br> 
  서버에서 클라이언트로 가는 메시지는 응답 메시지라고 부릅니다. <br> 
  그 외에 다른 종류의 HTTP 메시지는 없습니다. <br> 
  HTTP 요청과 응답 메시지의 형식은 굉장히 비슷합니다. <br> 
   
  HTTP 메시지는 다음의 세 부분으로 이루어집니다. <br> 
  
  시작줄 <br>
  - 메시지의 첫 줄은 시작줄로, 요청이라면 무엇을 해야 하는지 응답이라면 무슨 일이 일어났는지 나타냅니다. <br> 
  
   헤더 <br> 
  - 시작줄 다음에는 0개 이상의 헤더 필드가 이어집니다. 각 헤더 필드는 쉬운 구문분석을 위해 쌍점(:)으로 구분되어 있는 하나의 이름과 <br> 
     하나의 값으로 구성됩니다. 헤더 필드를 추가하려면 그저 한 줄을 더하기만 하면 됩니다. <br> 
     헤더는 빈 줄로 끝납니다. <br> 
   
   본문 <br>
  - 빈 줄 다음에는 어떤 종류의 데이터든 들어갈 수 있는 메시지 본문이 필요에 따라 올 수 있습니다. <br> 
    요청의 본문은 웹 서버로 데이터를 실어 보내며, 응답의 본문은 클라이언트로 데이터를 반환합니다. <br> 
    문자열이며 구조적인 시작줄이나 헤더와 달리, 본문은 임의의 이진 데이터를 포함할 수 있습니다. (이미지, 비디오, 오디오 트랙, 응용 소프트웨어) <br>
    물론 본문은 텍스트도 포함할 수 있습니다. <br> 
   
   
</details>

-----------------------

### HTTP 메시지의 간단한 예시는? (1장)

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.12] 
   
+ 그림 1-8은 간단한 HTTP 메시지를 주고받는 트랜잭션을 보여주고 있습니다. <br> 
  웹브라우저는 리소스 http://www.joes-hardward.com/tools.html를 요청합니다. <br> 
   
  그림 1-8에서, 웹브라우저는 HTTP 요청 메시지를 보냅니다. 요청 시작줄에 GET 메서드가 있고, <br>
  로컬 리소스는 /tools.html입니다. <br>
  HTTP 프로토콜과 1.0버전으로 요청을 보내고 있음도 표시되어 있습니다. <br> 
   
  본문은 없는데, 서버에서 간단한 문서를 가져오는데는 요청 데이터가 필요 없기 때문입니다. <br> 
  서버는 HTTP 응답 메시지를 돌려줍니다. <br>
  응답에는 HTTP 버전 번호(HTTP/1.0), 성공 상태 코드(200), 사유 구절(OK), 응답 헤더 필드 영역, <br>
  마지막으로 요청한 문서가 담겨 있는 응답 본문이 들어 있습니다. <br> 
  응답 본문 길이는 Content-Length 헤더에, 문서의 MIME 타입은 Content-Type 헤더에 적혀있습니다. <br>  
  
</details>

-----------------------

### TCP 커넥션이란? (1장)

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.13] 
   
+ 이제 HTTP 메시지가 어떻게 생겼는지 대략 살펴보았으니, 어떻게 TCP 커넥션을 통해 한 곳에서 다른 곳으로 옮겨가는지 <br>
  잠깐 이야기해보도록 합니다. <br> 
   
  HTTP는 애플리케이션 계층 프로토콜입니다. HTTP는 네트워크 통신의 핵심적인 세부사항에 대해서 신경쓰지 않는다. <br> 
  대신 대중적이고 신뢰성 있는 인터넷 전송 프로토콜인 TCP/IP에게 맡깁니다. <br> 
   
  TCP는 다음을 제공합니다. <br>
  (1) 오류 없는 데이터 전송 <br> 
  (2) 순서에 맞는 전달 (데이터는 언제나 보낸 순서대로 도착합니다) <br> 
  (3) 조각나지 않는 데이터 스트림 (언제든 어떤 크기로든 보낼 수 있습니다) <br> 
   
  인터넷 자체가 전 세계의 컴퓨터와 네트워크 장치들 사이에서 대중적으로 사용되는 TCP/IP에 기초하고 있습니다. <br> 
  TCP/IP는 TCP와 IP가 층을 이루는, 패킷 교환 네트워크 프로토콜의 집합입니다. <br> 
   
  TCP/IP는 각 네트워크와 하드웨어의 특성을 숨기고, 어떤 종류의 컴퓨터나 네트워크든 서로 신뢰성 있는 의사소통을 하게 해줍니다. <br> 
  일단 TCP 커넥션이 맺어지면, 클라이언트와 서버 컴퓨터 간에 교환되는 메시지가 없어지거나, 손상되거나, 순서가 뒤바뀌어 수신되는 일은 결코 없습니다. <br> 
   
  네트워크 개념상, HTTP 프로토콜은 TCP 위의 계층입니다. HTTP는 자신의 메시지 데이터를 전송하기 위해 TCP를 사용합니다. <br>
  이와 유사하게 TCP는 IP 위의 계층입니다. <br> 
   
  
  
</details>

-----------------------

### 접속, IP주소, 그리고 포트 번호란? (1장)

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드 p.14] 
   
+ HTTP 클라이언트가 서버에 메시지를 전송할 수 있게 되기 전에, <br> 
  인터넷 프로토콜(Internet Protocol, IP) 주소와 포트번호를 사용해 클라이언트와 서버 사이에 TCP/IP 커넥션을 맺어야 합니다. <br> 
  TCP 커넥션을 맺는 것은 다른 회사 사무실에 있는 누군가에게 전화를 거는 것과 다소 비슷합니다. <br> 
  먼저 회사의 전화번호를 누릅니다. 이렇게 하면 그 회사로 연결됩니다. <br> 
  그 다음엔 전화를 걸고자 하는 상대방이 쓰는 번호를 누릅니다. <br> 
   
  TCP에서는 서버 컴퓨터에 대한 IP 주소와 그 서버에서 실행 중인 프로그램이 사용 중인 포트번호가 필요합니다. <br> 
  다 좋은데, HTTP 서버의 IP 주소와 포트번호를 어떻게 알아낼 수 있을까? <br>
  그렇습니다. URL을 이용하면 됩니다. <br> 
  앞에서 URL이란 리소스에 대한 주소라고 언급했었습니다. <br>
  따라서 당연하게도 URL은 그 리소스를 가지고 있는 장비에 대한 IP 주소를 알려줄 수 있습니다. <br> 
   
  몇 가지 URL을 살펴봅니다. <br> 
  
  ```
  http://207.200.82.29:80/index.html 
  http://www.netscape.com:80/index.html
  http://www.netscape.com/index.html 
  ```
   
  첫 번째 URL은 IP 주소 '207.200.83.29'와 포트번호 '80'을 갖고 있습니다. <br> 
  두 번째 URL에는 숫자로 된 IP 주소가 없습니다. 대신 글자로 된 도메인 이름 혹은 호스트 명("www.netscape.com")을 갖고 있습니다. <br> 
  호스트 명은 IP 주소에 대한 이해하기 쉬운 형태의 별명입니다. <br> 
  호스트 명은 도메인 이름 서비스(Domain Name Service, DNS)라 불리는 장치를 통해 쉽게 IP로 변환될 수 있으므로, <br>
  모든 준비는 끝난 것입니다. <br> 
  DNS와 URL에 대해서는 2장에서 많이 이야기할 것입니다. <br> 
   
  마지막 UL은 포트번호가 없습니다. HTTP URL에 포트번호가 빠진 경우에는 기본값 80이라고 가정하면 됩니다. <br> 
  IP 주소와 포트번호를 이용해 클라이언트는 TCP/IP로 쉽게 통신할 수 있습니다. <br> 
  그림 1-10은 웹브라우저가 어떻게 HTTP를 이용해서 멀리 떨어진 곳에 있는 서버의 단순한 HTML 리소스를 사용자에게 보여주는지 묘사하고 있습니다. <br> 
  순서는 다음과 같습니다. 
   
  (a) 웹브라우저는 서버의 URL에서 호스트 명을 추출합니다. <br>
  (b) 웹브라우저는 서버의 호스트 명을 IP로 변환합니다. <br> 
  (c) 웹브라우저는 URL에서 포트번호(있다면)를 추출합니다. <br> 
  (d) 웹브라우저는 웹 서버와 TCP 커넥션을 맺습니다. <br> 
  (e) 웹브라우저는 서버에 HTTP 요청을 보냅니다. <br> 
  (f) 서버는 웹브라우저에 HTTP 응답을 돌려줍니다. <br> 
  (g) 커넥션이 닫히면, 웹브라우저는 문서를 보여줍니다. <br> 
   
  
</details>

-----------------------
### HTTP 메시지란? (3장) 

<details>
   <summary> 답안 보기 (👈 Click)</summary>
[참고: HTTP 완벽 가이드] 
   
+ HTTP가 인터넷의 배달원이라면, HTTP 메시지는 무언가를 담아 보내는 소포와 같습니다. <br> 
  1장에서 우리는 어떻게 HTTP 프로그램이 일을 처리하기 위해 서로에게 메시지를 전달하는지 보여주었습니다. <br> 
  이번 장은 HTTP 메시지의 모든 것(어떻게 메시지를 만들고 이해하는지)에 대해 말해줍니다. <br> 
  이번 장을 읽고 나면 당신만의 HTTP 애플리케이션을 만들기 위해 필요한 대부분을 알게 될 것입니다. <br> 
  좀 더 구체적으로, 다음을 배우게 될 것입니다. <br> 
   
  (1) 메시지가 어떻게 흘러가는가 <br>
  (2) HTTP 메시지의 세 부분(시작줄, 헤더, 개체 본문) <br>
  (3) 요청과 응답 메시지의 차이 <br>
  (4) 요청 메시지가 지원하는 여러 기능(메서드)들 <br>
  (5) 응답 메시지가 반환하는 여러 상태 코드들 <br> 
  (6) 여러 HTTP 헤더들은 무슨 일을 하는가 <br> 
   
  HTTP 메시지는 HTTP 애플리케이션 간에 주고 받은 데이터의 블록들입니다. <br> 
  이 데이터의 블록들은 메시지의 내용과 의미를 설명하는 텍스트 메타 정보로 시작하고, <br> 
  그 다음에 선택적으로 데이터가 올 수 있습니다. <br> 
  이 메시지는 클라이언트, 서버, 프락시 사이를 흐릅니다. <br> 
  '인바운드', '아웃바운드', '업스트림', '다운스트림'은 메시지의 방향을 의미하는 용어입니다. <br> 
  
</details>

-----------------------

### CORS란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
+ 
</details>

-----------------------

### CSRF란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
+ CSRF는 Cross Site Request Forgery의 줄임말로,  
  사용자가 위조된 코드가 포함된 페이지에 접근하면,
  사용자에게 스크립트가 전송되고, 브라우저에 의해 스크립트가 실행되는데,
  스크립트가 사용자를 대신해 동작을 실행하는 공격을 의미합니다. 
</details>

-----------------------

### XSS란?

<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
+ 
</details>


-----------------------

### DNS란? DNS는 어떻게 동작하나요? 
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 인터넷 사용자가 호스트를 지칭할 때는 문자형의 도메인 이름으로 주소를 표현합니다. <br> 
  그러므로 도메인 이름을 네트워크에서 사용하려면 IP 주소로 변환하는 과정이 필요합니다. <br> 
  
  DNS는 계층 구조를 지원하는 도메인 기반의 주소 표기 방법을 위한 분산 데이터베이스 시스템으로, <br>
  기본 목적은 도메인 이름에서 IP 주소를 얻는 것입니다. <br> 
  
  예를 들어, IP 주소를 원하는 응용 프로그램은 도메인 이름을 매개변수로 하여 해석기(Resolver)를 호출합니다. <br> 
  해석기는 UDP를 이용해 자신이 위치한 지역의 DNS 네임 서버에 변환을 요청하여 호스트의 IP 주소를 얻습니다. <br> 
   
  유닉스 시스템에서 지원하는 nslookup 명령은 DNS를 이용해 주소 변환 요구를 수행하는 대화형 프로그램입니다. <br>
  다음의 예처럼 도메인 이름이 information.korea.co.kr인 호스트의 IP 주소를 얻으려면 nslookup을 다음과 같이 실행합니다. <br>
   
  실행 결과는 사용자가 로그인한 유닉스 시스템의 환경 설정에서 DNS 서버가 server.korea.co.kr이라 가정한 경우입니다. <br> 
  따라서 nslookup 프로그램은 이 서버에 information.korea.co.kr의 IP 주소를 요청합니다. <br> 
  그 결과 DNS 서버의 도메인 이름(server.korea.co.kr)과 IP 주소(211.223.201.30)가 반환됩니다. <br> 
   
  DNS 서버 server.korea.co.kr은 정해진 방법으로 IP 주소를 찾아 nslookup에 결과를 돌려주므로, <br>
  nslookup이 화면에 출력한 결과로 information.korea.co.kr의 IP주소가 <br>
  211.223.201.29임을 알 수 있습니다. <br> 
   
  DNS는 도메인 네임 스페이스, 네임 서버, 해석기라는 세 가지 요소로 구성됩니다. <br>  
</details>

-----------------------

### 도메인 네임 스페이스란 무엇입니까?  
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 도메인 네임 스페이스는 트리 구조의 네임 스페이스를 비롯해 데이터에 대한 이름 관련 규칙을 정의합니다. <br> 
  도메인 네임 스페이스의 트리에 연결된 호스트는 자원 레코드(Resource Record)라는 정보 집합체로 표현됩니다. <br> 
  DNS의 정보 문의 과정은 이 집합체에서 특정 유형의 정보를 얻는 과정입니다. <br> 
  예를 들어, 인터넷에서 특정 도메인의 이름을 사용하는 호스트의 IP 주소 자원을 요청하는 질의에 대해 IP 주소를 반환합니다. <br>  
</details>

-----------------------

### 네임 서버란?  
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 네임서버는 네임 스페이스의 트리 구조와 트리에 보관된 정보 집합체를 관리하는 프로그램입니다. <br> 
  일반적으로 자신이 관리하는 도메인 공간에 관한 정보를 책임지며, 전체 도메인 구조의 다른 부분 정보를 제공하기 위한 <br>
  네임 서버 포인터를 가지고 있습니다. 
</details>

-----------------------

### 해석기란?  
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />

+ 해석기는 네임 서버로부터 클라이언트의 요청 정보를 얻어낸느 프로그램입니다. <br> 
  최소 하나 이상의 네임 서버와 접촉하며, 네임 서버의 정보를 이용해 응용 프로그램의 질의에 응답한다. <br> 
  처음 접촉한 네임 서버에 도메인 정보가 없으면 다른 네임 서버에 접속해 계속 질의한다. <br> 
</details>

-----------------------


### SSH란? 
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: https://library.gabia.com/contents/infrahosting/9002/] 
   
+ Secure Shell의 줄임말로, 원격 호스트에 접속하기 위해 사용되는 보안 프로토콜입니다. 
</details>


-----------------------

### 패킷이란? 
 
<details>
   <summary> 답안 보기 (👈 Click)</summary>
<br />
[참고: 성공과 실패를 결정하는 1%의 네트워크 원리 p.145] 
   
+ TCP 담당 부분은 접속, 송수신, 연결 끊기의 각 단계에서 통신 상대와 대화할 때, IP 담당 부분에 의뢰하여 대화하는 데이터를 
  패킷의 모습으로 만들어 상대에게 도착합니다.
  이번에는 의뢰를 받은 IP 담당 부분이 어떻게 패킷을 상대에게 송신하는지 살펴보겠습니다. 

  패킷은 '헤더'와 '데이터'의 두 부분으로 구성됩니다.
  헤더에는 수신처를 나타내는 주소 등의 제어 정보가 들어 있는데,
  이 부분은 택배의 전표와 같은 것입니다. 
  그리고 그 뒤에 의뢰처에서 의뢰한 데이터가 이어지는데, 이것이 화물의 내용물에 해당합니다.
  이 패킷을 다음과 같이 해서 목적지까지 운반합니다.

  먼저 패킷의 송신처가 되는 기기가 패킷을 만드는데, 헤더에는 적절한 제어 정보를 기록하고,
  데이터 부분에는 얼마간의 데이터를 넣은 후 패킷을 가장 가까운 중계 장치에 송신합니다.
  그러면 패킷이 가장 가까운 중계 장치에 도착하고, 중계 장치는 도착한 패킷의 헤더를 조사하여 패킷의 목적지를 판단합니다.
  이 때, 어느 수신처가 어느 방향에 있는지에 대한 정보를 기록한 표와 같은 것을 사용합니다.
  즉, 패킷의 헤더에 기록되어 잇는 수신처와 표에 등록된 내용을 결합하여 패킷의 수신처가 표의 어느 부분에 해당하는지 찾아내고,
  거기에 등록되어 있는 내용에서 패킷의 목적지를 판단합니다. 
  예를 들어, 패킷의 수신처와 표를 결합해서 'xxxx라는 주소는 xxxx번째 케이블'이라는 정보가 해당한다는 것을 알았다면,
  xxxx번째 케이블에 패킷의 신호를 송신합니다. 이렇게 해서 목적지를 향해 패킷을 송신하면 패킷은 다음 중계 장치에 도착할 것입니다. 

  이와 같은 방법으로 패킷을 중계하면 다시 그 다음의 중계 장치에 패킷이 도착합니다
  이렇게 해서 차례로 패킷을 중계하면 최종적으로 수신처의 기기에 패킷이 도착하는 것입니다. 
  또한 송신처에서 수신처를 향해 패킷을 보내면 보통 수신처에서 송신처를 향해 회답 패킷이 되돌아옵니다. 
  그러므로 어떤 시점에서 패킷을 보낼 때는 송신처였던 기기가 다음 시점에서는 수신처가 된다는 상태이므로
  송신처와 수신처를 명확하게 구별하지 않는 쪽이 편리할 수도 있습니다. 
  이러한 경우 송신처와 수신처의 기기를 묶어서 '엔드노드'라고 부릅니다.

  이 패킷의 기본은 여러 가지 패킷 통신 방식에 적합하므로 TCP/IP 네트워크에도 적합합니다.
  그러나 TCP/IP의 패킷 구조는 이 기본에서 발전한 것이므로 좀 더 복잡합니다.
  56쪽의 'IP 주소의 기본'에서 설명했듯이 서브넷은 '라우터'와 '허브'라는 두 종류의 패킷 중계 장치에서
  다음과 같은 역할을 분담하면서 패킷을 운반하기 때문입니다. 

  (1) 라우터가 목적지를 확인하여 다음 라우터를 나타냅니다.
  (2) 허브가 서브넷 안에서 패킷을 운반하여 다음 라우터에 도착합니다.

  허브는 이더넷의 규칙에 따라 패킷을 운반하고, 라우터는 IP의 규칙에 따라 패킷을 운반하기 때문에
  위의 설명을 다음과 같이 바꾸어 말할 수 있습니다.

  (1) IP가 목적지를 확인하여 다음 IP의 중계 장치를 나타냅니다. 
  (2) 서브넷 안에 있는 이더넷이 중계 장치까지 패킷을 운반합니다.

  좀 더 구체적으로 말하면 TCP/IP의 패킷에는 [그림 2-14]의 (b)와 같이 다음의 두 개의 헤더가 붙어 있습니다.
  그리고 다음과 같이 역할을 분담하여 패킷을 운반합니다.

  (a) MAC 헤더(이더넷용 헤더)
  (b) IP 헤더(IP용 헤더) 
</details>

