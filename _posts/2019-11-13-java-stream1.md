---
layout: post
title: "[Java] 자바 스트림 API 공부하기(1)"
---
### [Java] 자바 스트림 API 공부하기(1)
<br><br>
자바 8에서 추가된 스트림 API를 공부해보려고 한다.<br>
공부한 내용들을 두서없이.. 적을예정 ㅠㅠ<br>
<br>

#### Stream API
Stream API가 나오게 된 가장 주된 이유는 Java에서 선언적 프로그래밍이 가능해졌기 떄문이다.<br>
선언적 프로그래밍은 sql로 예를들면 쉽다.<br>
```
select * from member where id='suji'
우리가 필요한 데이터는 member에 있고요~ id가 suji였으면 좋겠어요~
```
<br>
Stream API는 거의 모든 것이 람다식으로 이루어져 있다.<br>
람다식은 "식별자 없이 실행 가능한 함수"라고 설명이 되어있는데 무슨 소리인지 잘 모르겠다.<br>
나는 "메소드를 따로 재정의하지 않고 사용하는 식" 이렇게 이해를 했다!<br>
아래는 람다식의 예시이다<br>
```
public class Calculator {
    interface IntegerMath {
        int operation(int a, int b);   
    }
  
    public int operateBinary(int a, int b, IntegerMath op) {
        return op.operation(a, b);
    }
 
    public static void main(String... args) {
    
        Calculator myApp = new Calculator();
        IntegerMath addition = (a, b) -> a + b;
        IntegerMath subtraction = (a, b) -> a - b;
        System.out.println("40 + 2 = " + myApp.operateBinary(40, 2, addition));
        System.out.println("20 - 10 = " + myApp.operateBinary(20, 10, subtraction));    
    }
}
```
[출처] <a href="https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#approach1">https://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html#approach1</a><br>
<br>
IntegerMath의 operation 메소드를 재정의하지않고<br>
람다식으로 덧셈, 뺄셈이 가능한 addition, subtraction 객체를 만들었다.<br>
실제 위 코드를 돌려보면 아주 깔끔하게 돌아간다.<br>
람다식이 아니었다면 IntegerMath 인터페이스를 덧셈, 뺄셈 객체로 구현하여<br>
각각 operation 메소드를 재정의 하여 사용했을 것이다.<br>
<br>
sql 문법이 쉽게 느껴졌던 것은 선언식이어서 쉽게 느껴진 것인데<br>
실제 람다식으로 작성된 자바 코드를 보니 확실히 선언식 프로그래밍이 쉽게 이해된다.<br>
<br>
#### Stream API의 특징
Stream API는 "이 객체가 이런 모양이었으면 좋겠어"라고 선언하는 것이다.<br>
목록처리 등 일련의 작업들을 선언적으로 처리할 수 있는 장점이 있다.<br>
그리고 원본 데이터를 건들지 않으며, 새로운 요소를 만들어서 리턴해준다.<br>
<br>
stream은 재사용이 불가능한데, stream의 뜻인 "시냇물"을 생각해보면 쉽다.<br>
시냇물이 한 번 지나가면 되돌아 올 수 없듯이 stream도 재사용이 불가능하다.<br>
<br>
stream 속의 각 element들은 상호작용하지 않는다.<br>
즉, 하나의 stream 요소가 처리될 때 다른 요소에 영향을 주면 안 된다는 것.<br>
모든 element는 독립적이라 stream API는 재귀호출에는 어울리지 않는다.<br>
<br><br>
stream에 대해서 조금 공부해본 내용을 적어보았다.<br>
다음번엔 API를 직접 사용해보자!<br>
To be continue..!