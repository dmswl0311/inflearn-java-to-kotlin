# 5강 코틀린에서 조건문을 다루는 방법

<br>

## if문
자바와 코틀린의 문법이 동일하다.
~~~java
private String getPassOrFail(int score){
    if(score>=50){
        return "P";
    }else{
        return "F";
    }
}
~~~
~~~kotlin
fun getePassOrFail(socre:Int): String{
    if(score>=50){
        reuturn "P"
    }else{
        return "F"
    }
}
~~~
자바에서 if-else문은 Statement, 코틀린에서는 Expression
> Statement? 프로그램의 문장, 하나의 값으로 도출되지 않는다. <br>
Expression? 하나의 값으로 결과가 도출되는 문장
~~~java
int score = 30+40; // -> 30+40은 Statement이자 Expression
~~~
~~~java
String grade = if(score>=50){
    return "P";
}else{
    return "F";
} // 자바에서 if문은 하나의 값으로 취급하지 않기 때문에 에러가 난다. >> Statement
~~~
~~~java
String grade= score>=50?"P":"F" //3항 연산자는 하나의 값으로 취급하기 떄문에 에러가 없다! >> Statement이자 Expression
~~~

<br>

## Expression과 Statement
~~~kotlin
fun getePassOrFail(socre:Int): String{
    if(score>=50){
        reuturn "P"
    }else{
        return "F"
    }
}
~~~
코틀린에서는 if-else문을 3항 연산자처럼 사용할 수 있다.
~~~kotlin
fun getePassOrFail(socre:Int): String{
    return if(score>=50){
        "P"
    }else{
        "F"
    }
}
~~~
> 어떠한 값이 특정 범위에 포함되어 있는지, 포함되어 있지 않은지
~~~
if(score >= 0 && score <= 100) >> if(score in 0..100)
if(score !in 0..100) // 범위 밖인 경우
~~~

<br>

## switch와 when
~~~java
private String getGradeWithSwitch(int score){\
    switch(score/10){
        case 9:
            return "A";
        case 8:
            return "B";
        case 7:
            return "C";
        default:
            return "D";
    }
}
~~~
코틀린에서는 switch-case문이 없다. 대신 when이 있다. 
~~~
when 사용 방법

when(값){
    조건부->구문
    조건부->구문
    else->구문
}
~~~
if-else와 마찬가지로 when도 expression이다.
~~~kotlin
fun getGradeWithSwitch(score:Int): String{
    return when(socre/10){
        9->"A"
        8->"B"
        7->"C"
        else->"D"
    }
}
~~~
특정 값으로 분기가 아니라, 다양한 조건을 이용해 분기가 가능하다.
~~~kotlin
fun getGradeWithSwitch(score:Int): String{
    return when(socre){
        in 90..99->"A"
        in 80..89->"B"
        in 70..79->"C"
        else->"D"
    }
}
~~~
조건부에는 어떠한 expression도 가능하다.
~~~java
private boolean startsWithA(Ojbect obj){
    if(obj instanceof String){
        return ((String)obj).startsWith("A");
    }else{
        return false;
    }
}
~~~
~~~kotlin
fun startsWithA(obj:Any): Boolean{
    return when(obj){
        is String->obj.stratsWith("A") // instanceof ==> is
        else->false
    }
}
~~~
여러개의 조건이 가능하다
~~~java
private void judgeNumber(int number){
    if(number == 1 || number == 0 || number == -1){
        System.out.println("어디서 많이 본 숫자입니다.");
    }else{
        System.out.println("1,0,-1이 아닙니다.");
    }
}
~~~
~~~kotlin
fun judgeNumber(number:Int){
    return when(number){
        1,0,-1->println("어디서 많이 본 숫자입니다.")
        else->println("1,0,-1이 아닙니다.")
    }
}
~~~
when 뒤에 값 자체가 없을 수도 있다.
~~~java
private void judgeNumber2(int number){
    if(number == 0){
        System.out.println("주어진 숫자는 0입니다.");
        return;
    }
    if(number%2 == 0){
        System.out.println("주어진 숫자는 짝수입니다.");
        return;
    }
    System.out.println("주어진 숫자는 홀수입니다.");  
}
~~~
~~~kotlin
fun judgeNumber2(number:Int){
    return when(){
        number==0->println("주어진 숫자는 0입니다.")
        number%2==0->println("주어진 숫자는 짝수입니다.")
        else->println("주어진 숫자는 홀수입니다.")
    }
}
~~~
when은 Enum class, Sealed class와 함께 사용할 경우, 더욱 진가를 발휘한다.