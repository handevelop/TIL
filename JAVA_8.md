# JAVA 8 변경 사항

2014 년에 발표된 JAVA 8 로 인해 많은 변화가 있었고 이로인해 JAVA 의 큰 발전이 있었다고 한다.
과연 무슨 변화가 있었고 주목할만한 점이 무엇인지 알아보자.


## 람다 표현식 (lambda expression)

람다 표현식이란 메소드를 하나의 식으로 표현한 방식.
즉 식별자 없이 실행할 수 있는 함수 표현식을 의미하며 이로인해 익명함수라고도 부른다.

AS-IS : 메소드를 사용하기 위해 클래스를 만들고 객체를 생성하고 메소드를 사용.
람다 표현식 : 메소드를 사용하기 위해 클래스나 객체를 생성하지 않아도 메소드를 사용 가능.

장점은 다음과 같다.
1. 코드 수를 줄일 수 있다. 가독성이 증가.
2. 람다 표현식으로 메소드의 매개변수로 전달, 결과값으로 리턴 가능 => 함수형 프로그래밍


사용법은 간단하다 화살표(->) 기호를 사용하여 람다 표현식을 작성할 수 있다. (이때문에 화살표 함수라고 부르기도 한다.)

유의 사항은 다음과 같다.
1. 매개변수의 타입을 추론할 수 있는 경우에는 타입을 생략할 수 있다
2. 매개변수가 하나인 경우에는 괄호(())를 생략할 수 있다.
3. 함수의 몸체가 하나의 명령문만으로 이루어진 경우에는 중괄호({})를 생략할 수 있다. (이때 세미콜론(;)은 붙이지 않음)
4. 함수의 몸체가 하나의 return 문으로만 이루어진 경우에는 중괄호({})를 생략할 수 없다.
5. return 문 대신 표현식을 사용할 수 있으며, 이때 반환값은 표현식의 결과값이 됨. (이때 세미콜론(;)은 붙이지 않음)

EX)
```java
// 기존 메소드 사용법
int min(int x, int y) {

    return x < y ? x : y;

}

// 람다 표현식 사용
(x, y) -> x < y ? x : y;
```


## 스트림 API

스트링 API 는 데이터를 추상화하여 저장된 데이터를 읽고 쓰기 위한 방법을 제공하는 API 이다.
기존에 배열이나 컬렉션들을 반복문이나 iterator 를 사용하여 코드를 작성했던 것을
stream() 이라는 스트림 API 를 통해 가독성을 높이고 코드 수를 줄일 수 있다.

EX)
```java
String[] arr = new String[]{"넷", "둘", "셋", "하나"};

 

// 배열에서 스트림 생성

Stream<String> stream1 = Arrays.stream(arr);

stream1.forEach(e -> System.out.print(e + " "));

System.out.println();

 

// 배열의 특정 부분만을 이용한 스트림 생성

Stream<String> stream2 = Arrays.stream(arr, 1, 3);

stream2.forEach(e -> System.out.print(e + " "));
```


## Calendat 클래스 문제점 해결

1. Calendar 인스턴스는 불변 객체(immutable object)가 아니라서 값이 수정될 수 있음.
2. 윤초(leap second)와 같은 특별한 상황을 고려하지 않음.
3. Calendar 클래스에서는 월(month)을 나타낼 때 1월부터 12월을 0부터 11까지로 표현해야 하는 불편함이 있음.

위의 대표적인 문제점들을 해결했다.


## 나즈혼 사용

기존에 JS 의 엔진으로 모질라의 Rhino(리노) 를 사용했으나
Java8 부터는 JS 의 엔진으로 오라클의 Nashorn(나즈혼) 을 사용하게 되었다.
성능과 메모리 관리면에서 크게 개선된 스크립트 엔진이라 평가 받고 있다.