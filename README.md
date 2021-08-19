# JDD (Ju-Dung-A-Li Driven Development/주둥아리 주도 개발)
![image](https://user-images.githubusercontent.com/10369528/130068355-049861db-ce6e-45cd-a74c-a262ee4fb01a.png)

JDD 는 실제 코드를 작성하는것보다 변명거리를 미리 생각하여 수많은 버그를 양상할 수 있는 개발 방법론이다.

JDD 는 아래와 같은 중요 가치를 따른다.

```
우리는
- 남이 쓰는 기술보다는 내가 쓰는 기술을
- Clean 한 코드 보다는 Tricky 한 코드를
- 버그 Fix 보다는 변명을
- 귀찮음 보다는 편함을
가치 있게 여긴다. 이 말은, 왼쪽에 있는 것들은 귀찮고 오른쪽에 있는 것들은 편하기 때문에 더 높은 가치를 둔다는 것이다.
```

JDD 를 실천하기 위해서는 쉬지않고 험난한 길이지만 꾸준하게 노력해야한다.
중요한것은 관련된 힙한 용어를 들먹이면서 실제 문제에 대한 답변을 회피하는것이다. 꾸준한 연습이 필요하다.


# JDD 를 위한 지침서

### 참된 리더
참된 리더는 부하직원을 괴롭히지 않는다.

```
- 누군가 PR을 했다는 사실자체가 보기 좋은 일이다. LGTM 

- 누군가 PR을 날리면 자동으로 LGTM 를 날리는 CI/CD 를 활용해라
```

### 방어적 프로그래밍
방어적 프로그래밍은 개발자의 기본 소양이다.

```
- 방어적 프로그래밍을 해라 코드로 방어하지 말고 너에게 들어오는 일감을 방어해라

- 작업양이 많은가? 그냥 특정 테스트케이스에서만 돌아가게 짜고 나머지는 "고도화" 작업에서 한다고 해라. 
"고도화" 작업 하기전에 이직하자
```

### 멀티 쓰레드
동시성은 어렵고, 성과가 눈에 띄지 않는다.
```
- 멀티 쓰레드 환경에서 가변변수 사용으로 인한 오류는 가끔 발생한다.
가끔 발생한다는거에 비하여 사용은 너무 편하다. 누가 뭐라고 하면 그럴일 없다고 하면 그만이다.

- 어쩔수없이 멀티 쓰레드 업무가 들어오면 언어를 욕하면서 이 작업이 왜 어려운지 설명해라,
아 이 언어는 Actor 모델이 빈약해서요, CSP 구현체가 없어서요, STM 이 지원안되서요.
욕을 할수록 작업기한이 늘어난다.

- 비동기 흐름내에서 동기함수를 몰래 써도 된다. 여기에 병목 찾는 작업 + 비동기로 개선 하는 작업하는 기한까지 나중에 받을수있다.
```

### 문서화
우리의 본분을 잊지 말자.

```
- 주석은 절대 작성하지 않는다. 누가 뭐라고하면 클린코드를 들먹이자, 물론 그렇다고해서 코드가 리더블하지는 않다.

- 우리는 개발자다, 어떤한 이유에서든지 문서작성은 금물, 누가 뭐라고하면 "코드가 곧 문서"
```

### 모던 프로그래밍
모던은 현재이다. 즉 지금 내가쓰는 기술이 곧 모던한 기술이다.

```
- 예외처리를 하지 않는다. 누가 뭐라고 하면 Let it crash 전략이라고 한다.

- 언어의 Feature 를 최대한 사용하지 않는다. 누가 뭐라고하면 유지보수를 위해 누구나 알수있게 짜둔거라고 한다.

- 언어의 Feature 를 최대한 활용하자, 누가 뭐라고하면 모던 프로그래밍이라고 하면된다.

- 의존성이 복잡하게 연결되있으면, 패턴이라고한다.

- 체이닝이 하나라도 있으면, Fluent API 스타일

- 함수들만 호출하는 함수가 있으면, 미니 언어로 DSL 을 구축했다고 해라

- 데이터를 넘겨주는 함수가 있으면, Data-Driven Programing 이라고 해라

- 함수 파라미터가 너무 많아졌다? 누가 뭐라고 하면 보다 "순수" 하게 짠거라고 해라

- 람다 함수로만 구성한다. 누가 뭐라고하면 고차함수 함수형 프로그래밍이라고한다.

- 패턴을 전혀 쓰지않는다. 누가 뭐라고 하면 단순성의 원칙이라고 한다.

- Map-Reduce-Filter 같은 고차함수는 일절 사용하지 않는다. 누가 뭐라고 하면 이 역시 단순성의 원칙이라고 한다.

- 어노테이션과 같은 메타데이터를 수십개는 달자. 누가 뭐라고하면 메타프로그래밍기법이라고 한다.

- OOP로 개발하는 사람들 사이에서 FP 패턴을 적극 활용하자, 
라이브러리까지 쓰면 더 좋다. Maybe 클래스를 만드는건 기본중에 기본. 누가 뭐라고 하면 "이게 요즘 스타일이예요"

- FP로 개발하는 사람들 사이에서 OOP 패턴과 가변변수를 적극 활용하자. 누가 뭐라고하면, "이렇게 하는게 더 편한데요?"

- 콜백헬을 보고 뭐냐고 물어보면 CPS 라고 답해줘라

- 모든 if문은 삼항연산자로 써라, 누가 뭐라고 하면, "아 if는 문이고 삼항은 식이니까요"

- 리스트 컴프리헨션, 옵셔널 체이닝, 리엑티브등을 쓰고 자랑스럽게 말해라 "모나딕하게 해결했다고". 
그게 뭐냐고 물어보면 "모나드의 저주로 인하여 설명하기 힘들다" 까지 말하는거까지 해야한다.

- 두개 이상 실행되는 서비스가 있으면 MSA 다.
테스트를 돌려주는 스크립트만 따로있어도 MSA 다.
거기에 언어가 다르면 폴리글랏까지 했다고 말할 수 있다.
```

### 설계 
어떻게 설계해도 돌아간다.
```
- 클래스, 인터페이스, 이넘, 맴버등 구조 설계에 대해서 뭐라고하면, ADT 에서 합타입이 어쩌고 곱타입이 어쩌고

- 클래스에 기능이 너무 적으면, 아 그건 레코드로 쓰려고 했습니다.

- 상속이 합성보다 편하다, 누가 뭐라고하면 OOP 에서는 당연히 상속을 써야하는게 맞다고 하면된다.

- null 은 10억불의 가치가 있다. 뭐든 애매하면 null을 리턴해라

- Object 나 Any는 폴리몰피즘의 극의이다. 뭐든 애매하면 Object 타입을 리턴해라,
Object 타입을 리턴하는 함수에서 null 을 리턴하도록 하는게 베스트
```

### 테스트
솔직히 테스트코드 짜는건 재미없다
```
- 테스트코드를 전혀 작성하지 않는다. 누가 뭐라고하면 repl로 테스트가 끝낫다고 해라.

- 테스트가 어떨때는 성공하고 어떨때는 실패하면, "속성 기반 테스트" 를 작성해서 그렇다고 해라
```

### 성능최적화
CPU 성능은 내 실력과 달리 날로 발전한다.
```
- DTO/VO 변환은 쓰지않는다. 누가 뭐라고 하면 성능 최적화라고 해라

- DB는 그때 그때 필요한 필드를 추가해라, 정규화나 규칙은 생각조차 하지말아라, 누가 뭐라고 하면 이 또한 성능 최적화

- 패턴이나 아키텍처는 쓰지 않는다. 클래스로도 나누지 마라. N중 포문과 if문으로 절차적으로 작성해라, 
누가 뭐라고 하면 이건 진짜 성능최적화라고 해라

- 성능최적화는 그 어떠한 경우에도 금물, 누가 뭐라고 하면 요즘은 "컴파일러" 한테 맡기는게 대세라고 해라
```

### 백엔드
백앤드는 모던 비즈니스의 핵심이다. 엄한데 힘빼지 말자
```
- 그건 DBA 가 해야할 일 이라고 해라
- 그건 프론트엔드가 해야할 일 이라고 해라
```

### 프론트엔드
프론트엔드는 유저가 마주하는 첫인상이다. 엄한데 힘빼지 말자
```
- 그건 백엔드가 해야할 일 이라고 해라
- 그건 퍼블리셔가 해야할 일 이라고 해라
- 그건 디자이너가 해야할 일 이라고 해라
- 그건 유저가 해야할 일 이라고 해라
```

### 기타
솔직히 좀 뇌절인듯
```
- 그날 배운 기술은 그날 회사 프로젝트에 적용해라, 누가 뭐라고 하면 그날 배운 지식을 자랑하면된다

- 기술 스택을 공부하지말고, 해당 기술 스택의 단점리스트만 공부해라, 누가 해당 기술 스택을 물어보면, 단점을 들먹이자

- 도커같이 가상화가 조금이라도 들어간건 사용하지 말아라, 누가 뭐라고하면 네이티브 환경에서의 확인이 필요하다고 해라
```


# Contributing
더 좋은 주둥아리 방법을 알고있다면 PR 을 날려주세요


# License
JDD 는 어떠한 제약조건도 없습니다.
단 책임도 지지 않습니다.
