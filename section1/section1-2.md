# 2강 코틀린에서 null을 다루는 법

코틀린에서는 null이 가능한 타입을 완전히 다르게 취급한다.

<br>

## safe call

> ?. 앞에 있는 변수가 null이 아니면 실행


<br>

## Elvis 연산자

> ?: 앞에 연산 결과가 null이면 뒤에 값을 사용


<br>

## 널 아님 단언

> !! 사실 어떤 경우에도 null일 수가 없다 -> 정말 null이 아닌게 확실할 경우에만 단언함

<br>

## 플랫폼 타입
코틀린에서 자바 코드를 사용할 때 어떻게 사용할까?<br>
null에 대한 어노테이션 정보를 코틀린이 인식한다!(자바로 작성된 코드에 대해)<br>
만약, 어노테이션이 없다면? 코틀린이 이게 Null인지 아닌지를 알 수 없다. -> 플랫폼 타입이다.<br>
런타임시 exception이 날 수 있다.















