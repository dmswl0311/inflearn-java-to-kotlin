# 1강 코틀린에서 변수를 다루는 방법


## var vs val

> 자바에서의 long, final long의 차이

var == 가변

val == 불변 (자바에서의 final과 같은 역할)

따라서 변수의 수정가능 여부 


~~~
var number1 = 10L

val number1 = 10L
~~~


> 코틀린에서는 모든 변수에 수정가능 여부를 명시해주어야 한다!

__자바는 변수를 선언할 때 타입을 지정해주어야 하지만, 코틀린은 의무적으로 타입을 작성할 필요가 없다.__


<br>

## 타입 명시 방법

> :  type

~~~
var number1: Long
~~~



초기값을 지정해 주지 않는 경우?

1. var

~~~
var number1: Long = 10L
~~~



2. val

불변이지만, 초기화 되지 않은 변수에 대해 최초 한번 값을 지정해 줄 수 있다.



초기값을 지정하지 않았을 경우에는 반드시 타입을 지정해주어야 하고, 값을 넣지 않은 채 사용할 수 없다.




val 컬렉션에는 element를 추가 할 수 있다.




모든 변수는 우선 val 로 만들고, 꼭 필요한 경우 var로 변경한다. 


<br>

## Primitive Type vs Reference Type

코틀린은 primitive와 reference의 구분이 없다. 

숫자, 문자, 불리언과 같은 타입은 실행 시 primitive value로 표현되지만, 코드에서는 평범한 클래스처럼 보인다.  

즉, 프로그래머가 boxing과 unboxing을 고려하지 않아도 된다. 


~~~
코틀린 -> JAVA로 decomplie

IntelliJ IDEA → Tools → Kotlin → Show Kotlin Bytecode → Decompile 클릭
~~~

<br>

## Nullable 변수

Kotlin에서의 Nullable 변수

> Kotlin에서 null이 변수로 들어갈 수 있다면 타입? 을 사용해야 한다.

~~~
var number3: Long?=1_000L 
number3=null
~~~



객체
~~~
var person = Person(“조은지”)
~~~

> 코틀린에서는 new를 붙이지 않아야 함. 

객체 인스턴스화 할때!

















