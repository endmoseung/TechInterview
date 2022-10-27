## 같이 걷는 개발자 김승모입니다.
> 기술면접 하면서 공부했던 내용을 기록<br/>
> 모두가 봐도 어색하지 않도록 정확한 내용만을 담을것

## 면접때 받은 질문들
이벤트루프 ,머지와 리베이스차이, http란 무엇인가, 리액트의 useState는 비동기인가 동기인가, recoil을 쓰는 이유, 리액트는 왜  자바스크립트에는 없는 return구문으로 동작하는가

## 정리한 질문들

### 이벤트루프 
이벤트루프를 알기위해서는 우선 비동기처리가 나와야되고 비동기 처리는 왜 나왔는지 알아야된다. 우선 비동기처리가 왜 나왔냐면 우선 자바스크립트는 싱글쓰레드로 돌아가는 언어이고, 자바스크립트에서는 여러 작업을 처리하기위해서 멀티쓰레드가아닌 외주를 맡기는것처럼 위임한다. 이게 비동기방식인데, 이를 관리하기 위해서 이벤트루프를 사용한다.	우선 이벤트루프는 큐라는 시스템을 사용하는데, 큐는 FIFO방식으로 진행되고 아까 맡겼던 위임을 넘겨주고 그 위임이 끝나면 내부의 큐에 콜백함수를 담는다. 이제 자바스크립트가 처리할 준비가 됐으면 큐안에 있는 콜백함수를 하나하나 실행한다.

### 머지와 리베이스 차이 
리베이스(rebase)는 브랜치(branch)의 베이스(base)를 재설정하여 다시 커밋을 재적용하는 작업을 의미한다. 브랜치는 베이스 지점을 가지고 있고 베이스에서 코드를 수정한다. 깃 히스토리를 살펴보면 베이스가 어디에 있는지를 알 수 있다.
리베이스는 즉 베이스를 새로 이동시키면서 히스토리를 재작성하고 머지는 히스토리를 보존하는데 하나의 깃에서 여러명이 작업하고있고 어떤 base를 기준으로 브랜치가 나눠져서 한명이 작업을 merge했다면 해당 브랜치를 리베이스해서 히스토리를 관리해주면 좋다

### http란 무엇인가? 
 HTTP는 Hyper Text Transfer Protocol의 두문자어로, 인터넷에서 데이터를 주고받을 수 있는 프로토콜입니다. 프로토콜은 규칙이라고 생각하시면 됩니다
그래서 정해진 규칙으로 서버와 클라이언트에서 데이터를 주고받으며 이에 주로 클라이언트에서 get,post,push,delete같은 메소드들로 서버에서 데이터를 받아온다

### 리액트의 useState는 동기인가 비동기인가
정답은 비동기이고 왜 비동기로 사용하냐? 정답은 비동기로 함으로써 한번에 값을 처리해주고 해당값으로 렌더링하면서 불필요한 렌더링을 막을 수 있다. 그리고 해당 바뀐 state의 값은 해당 setState할떄 바뀌는게 아니라 렌더링 직전에 업데이트된다. 동기적으로 처리한다면 값의 상태가 하나바뀔떄 마다 업데이트 해줘야되므로 상당한 비효율을 야기한다.

### 호이스팅 발생원리 
실행 컨텍스트에서 평가와 실행과정으로 이뤄지는데,  평가란, 실행 컨텍스트를 생성하고 변수, 함수 등의 선언문을 파악하여서 현재 스코프 내에서 사용할 수 있는 변수, 함수의 식별자를 실행 컨텍스트에 등록하는 과정입니다.평가과정에서 식별자들에 대한 정보가 먼저 실행 컨텍스트에 기록되는 것 뿐입니다.그래서 var는 전역객체의 프로퍼티로 등록되고호이스팅이 발생한다.

### 웹 스토리지 
 웹의 데이터를 클라이언트에 저장할 수 있는 새로운 자료구조로 localStorage sessionStorage가 있다.
기존 Cookie와는 다르게 객체정보를 저장 가능하고,최대 용량이나 storage의 갯수의 제한이 없다, 그리고 만료기간의 설정이 없다.
LocalStorage
저장한 데이터를 명시적으로 지우지 않는 이상 영구적으로 보관이 가능하다. 앞서 말한대로 도메인마다 별도로 로컬 스토로지가 생성된다. Windows 전역 객체의 LocalStorage라는 컬렉션을 통해 저장과 조회가 이루어진다.
SessionStorage
SessionStorage는 데이터의 지속성과 액세스 범위에 특수한 제한이 존재한다. SessionStorage는 windows 전역 객체의 sessionStorage라는 컬렉션을 통해 저장과 조회가 이루어진다.
데이터 유지 측면
SessionStorage는 데이터가 지속적으로 보관되지 않는다. 이는 마치 브라우저 기반 세션 쿠키와 그 성질이 비슷한데, 현재 페이지가 브라우징되고 있는 브라우저 컨텍스트 내에서만 데이터가 유지된다.
LocalStorage는 브라우저를 종료해도 데이터는 보관되어 다음번 접속에도 그 데이터를 사용할 수 있는 반면, SessionStorage는 브라우저가 종료되면 데이터도 같이 지워진다. 즉, 브라우저가 종료되면 SessionStorage도 삭제된다는 것이다.
그리고 session은 새로운 탭을 만들면 새로운 공간이 형성되서 기존에 있던 동일한 Url과 정보를 제공하지 못한다.

### this란 ?
this는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-reference variable)이다.
* this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.
* this는 자바스크립트 엔진에 의해 암묵적으로 생성된다.
* this는 코드 어디서든 참조할 수 있다.
* 하지만 this는 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 일반적으로 객체의 메서드 내부 또는 생성자 함수 내부에서만 의미가 있다.
* 함수를 호출하면 인자와 this가 암묵적으로 함수 내부에 전달된다.
* 함수 내부에서 인자를 지역 변수처럼 사용할 수 있는 것처럼, this도 지역 변수처럼 사용할 수 있다.
* 단, this가 가리키는 값, 즉 this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다.
* 크게 전역에서 사용할 때와 함수안에서 사용할 때로 나눌 수 있다.

### 자바스크립트는 싱글스레드?
자바스크립트는 간단하게 만든 싱글스레드 언어로 한번에 하나의 작업만 실행할수있으나 동시성을 지원하기위해서 비동기 방식을 채택하게됐다.이는 간단하게 설명하면 일을 하는 쓰레드는 하나지만 이 일꾼이 외부업체에 위임이 가능해서 해당일을 위임하고 처리된결과를 해야할일에 정리하고 최종 실행만한다.
이제 이 비동기처리를 구동하는 환경에서 가지고 있는 이벤트루프가 하고 이 이벤트루프는 내부의 큐를 가지고 있으면서 비동기처리가 완료가 되면 콜백함수에 담아둔다. 그러고 자바스크립트가 실행을 할떄 해당값을 하나씩 엔진에 넘겨줘서 실행한다.
이런 비동기 지옥을 해결하기위해 우리는 이런값을 받는다고 동기적으로 처리하는 promise가 등장했고 그럼에도 너무 코드가 난잡해서 async await구문이 나왔으며 async는 이 코드는 Promise가 반환된다고 약속해주는 코드이며 await은 promise가 settled 될떄까지 함수의 실행을 멈추고 settle되면 함수를 게속 실행

### 태스크큐와 마이크로태스크큐
어떤 함수를 실행하냐에 따라서 태스크큐와 마이크로태스크큐에 들어가는지가 달라지며 태스크큐에는 setTimeout, setInterval, setImmediate, requestAnimationFrame, I/O, UI 렌더링 이런 함수들이 들어가고
마이크로 태스크큐에는
process.nextTick, Promise, Object.observe, MutationObserver
이런 함수들이 들어가며 우선순위는 마이크로 태스크큐를 우선한다.

### 리코일을 쓰는 이유
기존 리덕스같은 애들은 초기 세팅값이 너무 컸고 리액트와는 별게로 상태관리 로직이 돌아갔기 떄문에 이를 해결하기위해 Recoil이 나왔다. 리코일은 컨텍스트 API에서 부분적인 상태를 관리하는게 불편했고 리코일은 이런 불편함을 해소가능하다.<br>
즉 Context 에서는 상태변경시, 구독한 하위 컴포넌트들이 모두 리렌더링 되는 문제가 있는데, Recoil 은 atom, selector 를 구독하면 구독한 컴포넌트만 리렌더링이 일어나며 해당 값이 Hook 기반으로 작성되어 있어서, 코드를 작성하기 용이하고 코드의 재사용성이 높다.(리액트스럽다) 
고로 상태관리도구로써 context Api를 사용하기보다는 Context Api는 props drilling을 위해서 사용하자.

### 리액트를 쓰는 이유
기존 Dom과는 다르게 Vdom을 이용해서 불필요한 렌더링을 막을 수 있다. <br>
html을 재사용이 가능하다. <br>
SPA를 만들기 위한 좋은 라이브러리다. <br>
명령형으로 Dom을 직접 조작하는 바닐라 자바스크립트처럼 구현하지 않아도 된다.

### 클로저
클로저는 자신이 생성될 때의 환경을 기억하고, 그를 사용하는 함수이다. 즉 환경이란 Lexical Environment를 지칭하는데 이는 본인이 있던 함수가 종료됐을때 사라지는게 맞지만 자바스크립트의 GC(garbage Collecting)은 해당 클로저가 Lexical Environment를 지칭하고 있다면 이 환경을 지우지 않는다. 그래서 사용이 가능하다.
클로저는 리액트에서 useState , useEffect같은 훅에서도 클로저를 사용해서 만들었다.

### 리액트의 불변성
리액트에서 불변성을 지켜주는 이유는 리액트가 상태 업데이트를 하는 원리 때문입니다. 리액트는 상태값을 업데이트 할 때 얕은 비교를 수행합니다. 즉 객체의 속성 하나하나를 비교하는게 아니라 참조값만 비교하여 상태 변화를 감지합니다.

### 리액트에서 함수형을 사용하는 이유
리액트 컴포넌트 라는 것이 함수+훅 방식으로 사용할 때 더욱 깔끔하고 가볍기 때문, 선언형으로 추상화해서 구현이 가능하다. 리액트가 추구하는 방향인 불변성, 재사용성에도 함수형 프로그래밍이 유리하며, 우리는 자연스럽게 useEffect같은 훅을통해 함수형 코딩을 하고 있다.

### 콜백지옥 탈출하기
콜백 지옥을 탈출하기 위해서 async await구문을 사용해서 해결한다. async를 사용하면 무조건 promise가 반환되고 await구문을 사용해서 해당 구문을 처리한 후 다음코드로 넘어간다.

### 전역관리를 하는 이유
context API를 사용하면 부모를 구독하는 자식들이 모두 리렌더링을 하게되는 문제가 발생하고 이를 useMemo같은 훅들로 처리가 가능하지만 그에따른 보일러플레이트가 비대해지고 해당값이 복잡한 객체일경우 수정이 어렵다는 단점이있다.
그래서 이를 해결하기위해서 전역관리 라이브러리를 사용한다.
