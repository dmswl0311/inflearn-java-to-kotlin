# 3강 코틀린에서 Type을 다루는 방법

<br>

## 기본 타입
자바와 동일하다.
> int Long Float Double

코틀린에서는 선언된 기본 값을 보고 타입을 추론한다.
~~~ kotlin
var num1= 3 (int)
var num2= 3L (Long)
var num3= 3.0f (Float)
var num4= 3.0 (Double)
~~~

<br>

> 자바: 기본 타입간의 변환은 암시적으로 이루어질 수 있다. 
<br>
코틀린: 기본 타입간의 변환은 명시적으로 이루어져야 한다. 

<br>

~~~ java
int num1=4;
long num2=num1;
System.out.println(num1+num2) // 타입이 다르지만, 결과 값은 계산이 됨. (int타입 -> long으로 암시적으로 변경됨)
~~~

~~~ kotlin
val num1= 4
val num2: Long=num1 // type mismatch 오류
println(num1+num2)
~~~
그럼 어떻게 변환해야 할까?  **.to변환타입() 을 사용해야 한다!**

~~~ kotlin
val num1=4
val num2: Long= num1.toLong()
println(num1+num2)
~~~
변수가 nullable이면 적절한 처리가 필요하다.
~~~ kotlin
val num1?=4
val num2: Long= num1?.toLong() ?:0L // null이 아니면 toLong() 실행, 그 결과가 null이면 0L 반환
~~~
<br>

## 타입 캐스팅
자바에서의 instanceof -> 코틀린에서 is 사용
~~~ kotlin

fun printAgeIfPerson(obj: Any){
    if(obj is Person){
        val person = obj as Person // 자바에서의 Person person=(Person)obj;와 동일 -> as Person은 생략 가능 -> 따라서 val person= obj으로 사용 가능! 
        println(person.age)
    }
}
~~~


instanceof의 반대 !is

만약, obj가 Nullable이라면?
~~~ kotlin
fun printAgeIfPerson(obj: Any?){
    val person = obj as? Person // as? -> 만약 obj가 Null이 아니면 Person 타입으로 변환, null이면 'obj as? Person' 전체가 null이 됨
    println(person?.age) // ?. -> null이 아니면 실행
}
~~~
<br>

## 코틀린의 특이한 타입 3가지
1. Any
    - 자바의 Object 역할(모든 객체의 최상위 타입)
    - 모든 Primitive Tpye의 최상위 타입도 Any
    - Any 자체로는 null을 표현할 수 없어 Any? 가 있음
    - Any에 Equals, hasCode, toString 존재
2. Unit
    - 자바의 void와 같은 역할
    - void와 다르게 unit은 그 자체로 타입 인자로 사용 가능하다.
    - 함수형 프로그래밍에서 Unit은 단 하나의 인스턴스만 갖는 타입을 의미. 즉, 코틀린의 unit은 실제 존재하는 타입이라는 것을 표현

3. Nothing
    - 함수가 정상적으로 끝나지 않았다는 사실을 표현하는 역할
    - 무조건 예외를 반환하는 함수 / 무한 루프 함수 등 (끝이 좋지 않은 함수)
    - 잘 쓰지 않음

<br>
<br>

## String interpolation / String indexing
${변수}를 사용하면 값이 들어간다. (자바의 String.format과 같은 역할)
~~~kotlin
val person = Person("조은지",26)
val log = "사람의 이름은 ${person.name}이고 나이는 ${person.age}이다."
~~~

> 변수 이름만 사용할 수도 있지만, ${변수}를 사용하는 것이 가독성, 일괄 변환, 정규식 활용 측면에서 좋다!

<br>


""" <br>

자바의 StringBuilder와 append 대신 사용

~~~kotlin
val name="조은지"
val str="""
ABC
DEF
${name}
""".trimIndex()
println(str)
~~~


자바 문자열에서 특정 문자 가져오기 [index] 사용
~~~java
String str="ABCDE"
char ch=str.charAt(1);
~~~

~~~kotlin
val str="ABCDE"
val ch=str[1]
~~~



