# [Java ]Interview List

> 간단히 개념들을 정리해보며 머리 속에 넣자~  
> 질문 자체에 없는 질문 의도가 있는 경우 추가 했습니다.

- [언어(Java, C++ ... )](<https://github.com/kim6394/Dev_BasicKnowledge/blob/master/Interview/README.md#언어)
- [운영체제](<https://github.com/kim6394/Dev_BasicKnowledge/blob/master/Interview/README.md#운영체제)
- [데이터베이스](<https://github.com/kim6394/Dev_BasicKnowledge/blob/master/Interview/README.md#데이터베이스)
- [네트워크](https://github.com/kim6394/Dev_BasicKnowledge/blob/master/Interview/README.md#네트워크)
- [스프링](https://github.com/kim6394/Dev_BasicKnowledge/blob/master/Interview/README.md#스프링)

### 가비지 컬렉션이란?

- 정리되지 않은 메모리, 유효하지 않은 메모리 주소인 가비지를 정리해주는 프로그램
- Heap 메모리를 재활용 하기위해 참조되지 않는 객체들을 해제시켜 가용한 공간을 만드는 작업
- 프로그래머가 직접 메모리를 정리하지 않아도 되어 개발 속도가 대폭 향상된다.
- 메모리를 언제 되찾을 지 결정하기 위한 오버헤드 발생 문제점 존재

### StringBuilder와 StringBuffer의 차이는?

> mutation(가변), immutation(불변) 이해  
> 불변 객체인 String 의 연산에서 오는 퍼포먼스 이슈 이해

- String
    - immutation
    - String 문자열을 연산하는 과정에서 불변 객체의 반복 생성으로 퍼포먼스가 낮아짐.
- 같은점
    - mutation
    - append() 등의 api 지원
- 차이점
    - StringBuilder 는 동기화를 지원하지 않아 싱글 스레드에서 속도가 빠릅니다.
    - StringBuffer 는 멀티 스레드 환경에서의 동기화를 지원하지만 이런 구현은 로직을 의심해야 합니다.
- 참고
    - [실무에서의 String 연산](https://hyune-c.tistory.com/entry/String-%EC%9D%84-%EC%9E%98-%EC%8D%A8%EB%B3%B4%EC%9E%90)

### Serialization이란?

- 객체의 상태 혹은 데이터 구조를 기록할 수 있는 포맷으로 변환해줌
- 나중에 재구성 할 수 있게 자바 객체를 JSON으로 변환해주거나 JSON을 자바 객체로 변환해주는 라이브러리

### Java의 메모리 영역은?

- 메소드 : 바이트 코드, 전역 변수, static 변수
- 스택 : 매개 변수, 지역 변수 (사용 끝나면 바로 소멸, 컴파일 시에 메모리 할당)
- 힙 : new로 생성된 객체(c에서는 malloc()). 호출이 끝나도 사라지지 않고 프로그램 실행 시 동적 할당

### 오버로딩과 오버라이딩 차이는?

- 오버로딩
    - 반환타입 관계 없음, 메소드명 같음, 매개변수 다름 (자료형 또는 순서)
- 오버라이딩
    - 반환타입, 메소드명, 매개변수 모두 같음
    - 부모 클래스로부터 상속받은 메소드를 재정의하는 것.
- 참고
    - 오버로딩은 생성자가 여러개 필요한 경우 유용합니다.
    - 결합도를 낮추기 위한 방법 중 하나로 interface 사용이 있으며, 이 과정에서 오버라이딩이 적극 사용됩니다.

### 추상 클래스와 인터페이스 차이는?

- abstract class 추상 클래스
    - 단일 상속을 지원합니다.
    - 변수를 가질 수 있습니다.
    - 하나 이상의 abstract 메소드가 존재해야 합니다.
    - 자식 클래스에서 상속을 통해 abstract 메소드를 구현합니다. (extends)
        - abstract 메소드가 아닌 구현된 메소드를 상속 받을 수 있습니다.
- interface 인터페이스
    - 다중 상속을 지원합니다.
    - 변수를 가질 수 없습니다. 상수는 가능합니다.
    - 모든 메소드는 선언부만 존재합니다.
    - 구현 클래스는 선언된 모든 메소드를 overriding 합니다.
- 참고
    - java 버전이 올라갈수록 abstract 의 기능을 interface 가 흡수하고 있습니다.
        - java 8: interface 에서 default method 사용 가능
        - java 9: interface 에서 private method 사용 가능

### 제네릭이란?

- 클래스에서 사용할 타입을 클래스 외부에서 설정하도록 만드는 것
- 제네릭으로 선언한 클래스는, 내가 원하는 타입으로 만들어 사용이 가능함
- <안에는 참조자료형(클래스, 인터페이스, 배열)만 가능함 (기본자료형을 이용하기 위해선 wrapper 클래스를 활용해야 함)
- 참고
    - Autoboxing, Unboxing

### 접근 제어자란? Access Modifier

- public: 모든 접근 허용
- protected: 상속받은 클래스 or 같은 패키지만 접근 허용
- default: 기본 제한자. 자신 클래스 내부 or 같은 패키지만 접근 허용
- private: 외부 접근 불가능. 같은 클래스 내에서만 가능
- 참고
    - 보통 명시적인 표현을 선호하여 default 는 잘 쓰이지 않습니다.

### Call by Value vs Call by Reference

- 값에 의한 호출 : 값을 복사해서 새로운 함수로 넘기는 호출 방식. 원본 값 변경X
- 참조에 의한 호출 :  주소 값을 인자로 전달하는 호출 방식. 원본 값 변경O

### 배열과 연결리스트 차이는?

배열은 인덱스를 가짐. 원하는 데이터를 한번에 접근하기 때문에 접근 속도 빠름.  
크기 변경이 불가능하며, 데이터 삽입 및 삭제 시 그 위치의 다음 위치부터 모든 데이터 위치를 변경해야 되는 단점 존재  
연결리스트는 인덱스 대신에 현재 위치의 이전/다음 위치를 기억함.  
크기는 가변적. 인덱스 접근이 아니기 때문에 연결되어 있는 링크를 쭉 따라가야 접근이 가능함. (따라서 배열보다 속도 느림)  
데이터 삽입 및 삭제는 논리적 주소만 바꿔주면 되기 때문에 매우 용이함

- 데이터의 양이 많고 삽입/삭제가 없음. 데이터 검색을 많이 해야할 때 → Array
- 데이터의 양이 적고 삽입/삭제 빈번함 → LinkedList

### Hash란?

데이터 삽입 및 삭제 시, 기존 데이터를 밀어내거나 채우지 않고 데이터와 연관된 고유한 숫자를 생성해 인덱스로 사용하는 방법  
검색 속도가 매우 빠르다

### Java 컴파일 과정

컴파일러가 소스코드를 자바 바이트 코드(.class)로 변환  
JVM이 바이트코드를 기계어로 변환하고, 인터프리터 방식으로 애플리케이션 실행

### 스레드는 어떤 방식으로 생성하나요? 장단점도 말해주세요

생성방법 : Runnable(인터페이스)로 선언되어 있는 클래스 or Thread 클래스를 상속받아서 run() 메소드를 구현해주면 됨  
장점 : 빠른 프로세스 생성, 메모리를 적게 사용 가능, 정보 공유가 쉬움  
단점 : 데드락에 빠질 위험이 존재
