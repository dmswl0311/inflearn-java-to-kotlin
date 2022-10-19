# 6강 코틀린에서 반복문을 다루는 방법

<br>

## for-each문

숫자가 들어있는 리스트를 하나씩 출력하는 예제
~~~java
List<Long> numbers=Arrays.asList(1L,2L,3L);
for(long num : numbers){
    Sytem.out.println(num);
}
~~~
~~~kotlin
val numbers= lifstOf(1L,2L,3L)
for(num in numbers){
    println(num)
}
~~~

> 차이점
- 컬렉션을 만드는 방법
- ':' 대신 'in' 사용
- 타입 추론이 가능하기 때문에 타입이 없다.

<br>

## 전통적인 for문

~~~java
for(int i=0; i<=10; i++){
    Sytem.out.println(i);
}
~~~
~~~kotlin
for(i in 0..10){
    println(i)
}
~~~
> 차이점
- 범위를 나타낼 때 '..' 사용

> 만약, 내려가는 경우는? <br> downTo 사용
~~~kotlin
for(i in 10 downTo 0){
    println(i)
}
~~~
> 만약, 2칸씩 올라가는 경우는? <br> step 사용
~~~kotlin
for(i in 0..10 step 2){
    println(i)
}
~~~

<br>

## Progression과 Range
연산자: 범위를 만들어내는 연산자 
<br> 
ex) 1..3: 1부터 3까지의 범위 
<br> 
사실은 range(구간)을 만들고 있는 것! 
등차 수열을 만들고 있는 함수이다. 

<br> 

> downTo, step도 함수이다. <br> '변수.함수이름(argument)'가 아닌 '변수 함수이름(argument)'로 사용할뿐..

따라서 코틀린에서의 전통적인 for문은 알고보면 등차수열을 이용한 것이다!


<br>

## while문
자바와 코틀린 완전히 같다.
~~~kotlin
var i = 1
while(i <= 3){
    println(i)
    i++
}
~~~
