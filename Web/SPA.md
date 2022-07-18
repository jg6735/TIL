## SPA(Single Page Application)

- **등장배경**

	과거의 웹 사이트는 문서 하나에 전달되는 파일의 용량이 적었고, 어떤 요소를 클릭할 때마다 완전히 새로운 페이지를 서버에서 전송해 주곤 했다.
	하지만 점차 웹 사이트가 고도화됨에 따라 한 페이지에 해당하는 페이지 용량이 커지고, 매번 새로운 페이지를 전달하는 게 점점 버거워졌다.
	
- **SPA의 등장**

	이러한 문제를 해결하기 위해 등장한 것이 **SPA(Single Page Application)**이다. 이름에서 파악할 수 있듯이, 어떤 웹 사이트의 전체 페이지를
	하나의 페이지에 담아 동적으로 화면을 바꿔가며 표현하는 것이 SPA다. 최초 로드된 자바스크립트를 통해 미리 브라우저에 올라간 템플릿만 교체하는 것이다.
	
- **SPA 프레임워크**

	SPA 프레임워크로 유명한 Angular, React, Vue 등이 있다. 세부적인 구현 개념은 다를 수 있지만 궁극적으로 목적은 모두 SPA를 쉽고 확장성 있게 구현하는 것을 목표로 하고 있다.
	Virtual DOM이라는 개념을 사용하여 SPA를 구현하는데, SPA의 문제점은 자바스크립트로 인한 DOM 조작이 빈번하게 일어나 브라우저의 성능을 저하시킨다는 점이다.
	Virtual DOM을 사용하는 프레임워크들은 실제 DOM 트리를 흉내낸 가상의 객체 트리로 html 정보를 저장하고 있다가, 이 트리에 변경이 발생하면 모든 변화를 모아
	단 한번 브라우저를 호출해 화면을 갱신하는 방법을 사용한다. 이렇게 하여 브라우저와의 불필요한 상호작용을 최소화하면서 인터렉티브한 웹 사이트를 개발하는 것이 가능하다.

### **Question** SPA의 개념에 대해서 설명해보세요.
- **답변 예시** 
	- SPA는 Single page application으로 기존 웹페이지를 개발할 때에는 각각의 페이지마다 뷰(View)파일을 가졌다면 SPA의 구조는 하나의 뷰(View)파일에 컴포넌트를 배치하는 방식으로 페이지를 구성하는 개념입니다.