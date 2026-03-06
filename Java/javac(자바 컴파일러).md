java로 작성된 프로그램 실행 : java.exe
java 소스파일을 java가 실행시킬 수 있도록 변환하는 컴파일러 : javac

자바 컴파일러 : javac
C:\Program Files\java\jdk1.7.0_80\bin


### javac 작동원리

소스파일(.java) -> 목적파일 - 바이트파일(.class) -> 실행파일

소스파일 -> 목적파일로 넘어갈때 javac 가 작업
`소스파일 : 개발자가 작성하는 고레벨언어인 소스코드로 구성된 파일 ex. *.java, *.c`
`목적파일 : 소스파일을 컴파일해서 생긴 파일 ex. 바이트코드, 바이너리 코드`


바이트파일을 JVM이 읽어 실행시킴
여기서 처음 class를 메모리에 올리는 Class Loader에서 필요한 파일이 없는경우 exeption 발생
