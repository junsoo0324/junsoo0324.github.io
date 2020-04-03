---
layout: single
title: java 버전별 차이
time: 2020-04-02 18:57:00 +0900
author: JunSoo
---



### JDK 1.1

1. 이너 클래스, JavaBeans, RMI, 리플렉션, 유니코드 지원, 국제화(Internationalization) 등이 추가



###  J2SE 1.2

1. strictfp, Swing GUI, JIT, Java Applet을 구동하는 웹 브라우저 플러그인, CORBA, Collections 등이 추가



###  J2SE 1.3

1. HotSpot JVM, JNDI, JPDA, JavaSound 등이 추가되었다.

2. RMI가 CORBA를 지원하도록 변경되었다.



###  J2SE 1.4

1. assert, 정규표현식, IPv6, Non-Blocking IO, XML API, JCE, JSSE, JAAS, Java Web Start 등이 추가되었다.



###  J2SE 5

1. Generics, Annotation, Auto Boxing/Unboxing, Enumeration, 가변 길이 파라미터, Static Import, 새로운 Concurrency API 등이 추가되었다.

2. J2SE 5에 들어서 java.util.Scanner가 추가되면서 이전보다 편하게 표준 입력을 사용할 수 있게 되었다.



###  Java SE 6

1. Scripting Language Support, JDBC 4.0, Java Compiler API, Pluggable Annotation 등이 추가

2. 스크립팅 언어 지원과 함께 Rhino JavaScript 엔진이 기본으로 탑재



###  Java SE 7

1. Dynamic Language 지원, switch문에서 String 사용, try문에서 자동 자원 관리, Diamond Operator <>, 이진수 리터럴, 숫자 리터럴에 _ 지원, 새로운 Concurrency API, 새로운 File NIO 라이브러리, Elliptic Curve Cryptography, Java2D를 위한 XRender, Upstream, Java Deployment Ruleset 등이 추가



###  Java SE 8

1. Lambda Expression, Rhino 대신 Nashorn JavaScript 엔진 탑재, Annotation on Java Types, Unsigned Integer 계산,

2. Repeating Annotation, 새로운 날짜와 시간 API, Static Link JNI Library, Interface Default Method, PermGen 영역 삭제, Stream API 등이 추가.
3. GC 성능 대폭 개선



###  Java SE 9

1. JShell, 선행 컴파일(Ahead-Of-Time Compilation)이 실험 기능으로 추가되었다.

2. Deprecated 표시에는 해당 버전과 제거 예정 여부를 표시할 수 있게 되었다.

3. 프로퍼티 파일에 UTF-8이 지원되었으며, 구조적 불변 컬렉션, 통합 로깅, HTTP/2, private 인터페이스 메소드, HTML5 Javadoc 등이 지원되었다.
4. 인터페이스 내에 private 구현체 가능
5. 모듈시스템 등장(jigsaw)



###  Java SE 10

1. var 키워드를 이용한 지역 변수 타입 추론, 병렬 처리 가비지 컬렉션,개별 쓰레드로 분리된 Stop-The-World, 루트 CA 목록 등이 추가

2. JDK의 레포지토리가 하나로 통합되었으며, JVM 힙 영역을 시스템 메모리가 아닌 다른 종류의 메모리에도 할당할 수 있게 되었다.

3. 실험 기능으로 Java 기반의 JIT 컴파일러가 추가되었고, Deprecated 처리된 API는 Java SE 10에서 모두 삭제되었다.
4. Local Variable Type Inference → var 사용



###  Java SE 11

1. 람다 파라미터에 대한 지역변수 문법이 변화 되었고, HTTP 클라이언트 표준화 기능이 추가되었다.

2. 네스트 기반 액세스 컨트롤 ,다이나믹 클래스-파일 콘스탄스, 엡실론 가비지 컬렉터, The Z Garbage Collector, 플라이트 레코더가 추가되었다.



### Java SE 12

1. 문법적으로 switch문이 확장되었다.

2. 비지 컬렉터 개선, 마이크로 벤치마크 툴 추가, 성능 개선 등의 변경점이 있다.



###  Java SE 13

1. java 12에서의 스위치 개선을 이어 yield 라는 예약어가 추가되었다.

