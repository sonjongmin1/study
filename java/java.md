# `JAVA 특징`

1. JVM 위에서 실행, 운영체제 관계없이 실행

- 객체지향프로그래밍(OOP), 재활용성이 있어야 된다.
- 상속성(상위 객체가 하위 객체가 물려줌)
- 다형성 : 업캐스팅, 오버라이딩
  - 업캐스팅 : 내가 가진 타입을 부모가 가진 형으로 업시키는 것
  - 오버라이딩 : 재정의, 부모가 가진 똑같은 이름으로 다시 재정의
- 캡슐화 : 외부에서 직접적으로 접근하지 못하고, 안에서만 접근 할 수 있는 것
- 추상화 : 클래스에서 공통적인것을 뽑아 상위클래스로 옮김, 공통적인것 ex) 직원
  - 필요한 기능만 노출, 내부구현은 숨기는 것

2. 데이터베이스 연결 (JDBC), 네트워크(SOCKET), API 제공(각각에 다른 어플리케이션을 둘이서 통신이 가능하게 하는 것) 주고 받는 방식

- WEB API : REST API

### 도구

- JDK(java Development Kit)
- IDE(통합 개발 환경) : Eclipse, IntelliJ
- Apache Tomcat(톰캣) : java 웹 애플리케이션 (Servlet, jsp)
- 데이터베이스 연결 (jdbc)

### 자바 설치

window

- 오라클 홈페이지에서 자바jdk 21버전 설치
  - https://www.oracle.com/java/technologies/downloads/?er=221886#jdk21-windows
- Win + R -> sysdm.cpl
- cmd java -version 자바가 설치되어있는지 확인
- cmd javac -version 으로 확인
- 자바를 웹쪽으로 연결시키기 위해 Tomcat 설치
  - https://tomcat.apache.org/download-90.cgi
