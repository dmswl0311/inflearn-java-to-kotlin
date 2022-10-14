# 4강 코틀린에서 연산자를 다루는 방법

<br>

## 단항 연산자 / 산술 연산자
단항 (++,--) <br>
산술 (+,-,*,/,%) <br> 
산술대입 (+=,-=,*=,/=,%=) <br>
자바와 코틀린 모두 동일 

<br>

## 비교 연산자와 동등성, 동일성

비교 (>,<,<=.>=) <br> 
자바와 코틀린 모두 동일 
단, 자바와 다르게 객체를 비교할 때 비교 연산자를 사용하면 자동으로 compareTo를 호출해준다. -> 직관적이다.

자바
~~~java
...
public int compareTo(@NotNull JavaMoney o){
    return Long.compare(this.amount,o.mount);
} // 객체의 값을 비교해 음수 or 0 or 양수를 출력해주는 메서드

JavaMoney money1=new JavaMoney(2000L);
JavaMoney money2=new JavaMoney(1000L);
 
if(money1.compareTo(money2)>0){
    System.out.println("Money1이 Money2보다 금액이 큽니다.");
}
~~~
코틀린
~~~kotlin
val money1 = JavaMoney(2000L)
val money2 = JavaMoney(1000L)
if(money1 > money2){
    println("money1이 money2보다 크다.")
} // 코틀린에서는 비교 연산자 상황이 되면 자동으로 compareTo를 호출한다.
~~~

<br>

## 동등성과 동일성
동등성(Equality): 두 객체의 값이 같은가? <br>
동일성(Identity): 완전히 동일한 객체인가? 즉, 객체의 주소가 같은가?

**java**  <br>
==: 레퍼런스가 같은지 확인 <br>
equals: 값이 같은지 확인

**kotlin**  <br>
===: 레퍼런스 확인  <br>
==: 값이 같은지 확인 -> 간접적으로 equals를 호출해줌

<br>

## 논리 연산자
논리 연산자(&&,||,!)는 자바와 완전히 동일하다.  <br>

또한, 자바처럼 Lazy 연산을 수행한다.
> Lazy 연산? 
~~~kotlin
fun main(){
    if(fun1() || fun2()){
        println("본문") //무조건 '본문'이 출력된다. fun1이 true이기 때문에 fun2를 보지않고 실행된다. 이를 lazy 연산이라 한다. 
    }
}
fun fun1(){
    return true
}
fun fun2(){
    return false
}
~~~

<br>

## 코틀린에 있는 특이한 연산자
- in / !in
    - 컬렉션이나 범위에 포함되어 있다. / 포함되어 있지 않다.
- a..b
    - a부터 b까지 범위 객체를 생성한다.
- a[i]
    - a에서 특정 index i 값을 가져온다.
- a[i]=b
    - a의 특정 index i에 b를 넣는다.

<br>

## 연산자 오버로딩
자바
~~~java
public JavaMoney plus(JavaMoney other){
    return new JavaMoney(this.amount+other.amount);
}
...
JavaMoney money1 = new JavaMoney(1000L);
JavaMoney money2 = new JavaMoney(2000L);
System.out.println(money1.plus(money2));
~~~
코틀린
~~~kotlin
val money1 = Money(1000L)
val money2 = Money(2000L)
println(money1 + money2)
~~~
코틀린에서는 객체마다 연산자를 직접 정의할 수 있다.