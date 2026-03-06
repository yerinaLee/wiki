**한줄요약**
Java로 프로그래밍을 해야함 : JDK
Java 프로그램을 실행시켜야함 : JRE

![](../0.images/Pasted%20image%2020260306132145.png)
![](Pasted%20image%2020260306111855.png)

![](Pasted%20image%2020260306111916.png)


출처 : 
https://inpa.tistory.com/entry/JAVA-%E2%98%95-JDK-JRE-JVM-%EA%B0%9C%EB%85%90-%EA%B5%AC%EC%84%B1-%EC%9B%90%EB%A6%AC-%F0%9F%92%AF-%EC%99%84%EB%B2%BD-%EC%B4%9D%EC%A0%95%EB%A6%AC


## JDK (Java Development Kit)

> - 자바 개발키트. 자바로 개발하는데 사용되는 SDK(Software Development Kit)키트임
> - 라이브러리, javac, javadoc 등의 개발도구 포함
> - JER(Java Runtime Environment) 도 포함 - 자바 프로그램 실행을 위해서


**특징**
-- JDK는 종류가 여러가지 있음
-- java의 소스코드는 오픈소스지만, JDK 라이센스가 유료가 될 수 있어 여러 JDK버전이 출시됨(linux와 비슷)
```
// java 버전 및 밴더사 조회
java -XshowSettings:properties -version
```


## JRE(Java Runtime Environment)

>- JVM과 자바 프로그램을 실행시킬 때 필요한 라이브러리 API를 함께 묶어 배포되는 패키지
> - JDK11 이전에는 따로 설치 가능, 이후에는 JDK와 함께 설치됨


## JVM(Java Virtual Machine)
>- Java 실행 프로그램. Java로 작성된 모든 프로그램은 JVM에서만 실행됨
>- JRE가 로컬 컴퓨터 OS에 맞게 설치되어있으면 됨 -> OS 제약 X


**JVM 작동방식**
1. Java Compiler가 .java파일을 .class파일로 Byte Code 컴파일 (OS 이전에 JVM이 이해하는 코드)
.java => .class

2. JVM이 Byte Code를 Binary Code(기계어)로 컴파일

3. JVM이 컴파일한 기계어가 CPU에서 실행
