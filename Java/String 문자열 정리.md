### String
자바에서 문자열에 해당하는 자료형

String 인스턴스는 한 번 생성되면 그 값을 읽기만 할 수 있고, 변경할 수 없다. 자바에서 `+` 연산자를 이용해 문자열 결합을 수행하면 기존 문자열이 변경되는 것이 아니라 새로운 String 인스턴스가 생성된다.

### 문자열 선언 및 할당
```java
String a = "Happy Java";
String b = "a";
String c = "123";

String a = new String("Happy Java");
String b = new String("a");
String c = new String("123");
```
첫번째 방식을 사용하는게 가독성도 좋고 컴파일 시 최적화에 도움을 준다.

String은 리터럴로 표기가 가능하지만 primitive 자료형이 아닌 참조형타입이다.


### 대표적인 String 메소드

|메소드|	설명|
|--|--|
|char charAt(int index)	|해당 문자열의 특정 인덱스에 해당하는 문자를 반환함.|
|int compareTo(String str)|해당 문자열을 인수로 전달된 문자열과 사전 편찬 순으로 비교함. 대소문자를 구분함. 두 문자열이 같으면 0, 해당 문자열이 인수로 전달된 문자열보다 작으면 음수, 크면 양수를 반환함.|
|int compareToIgnoreCase(String str)|해당 문자열을 인수로 전달된 문자열과 대소문자를 구분하지 않고 사전 편찬 순으로 비교함.|
|String concat(String str)	|해당 문자열의 뒤에 인수로 전달된 문자열을 추가한 새로운 문자열을 반환함.|
|int indexOf(int ch)|int indexOf(String str)|해당 문자열에서 특정 문자나 문자열이 처음으로 등장하는 위치의 인덱스를 반환함.|
|int indexOf(int ch, int fromIndex), int indexOf(String str, int fromIndex)|해당 문자열에서 특정 문자나 문자열이 전달된 인덱스 이후에 처음으로 등장하는 위치의 인덱스를 반환함. 포함되어 있지 않는 경우 -1을 반환함. 대소문자를 구분함.|
|int lastIndexOf(int ch)|	해당 문자열에서 특정 문자가 마지막으로 등장하는 위치의 인덱스를 반환함.|
|int lastIndexOf(int ch, int fromIndex)|	해당 문자열에서 특정 문자가 전달된 인덱스 이후에 마지막으로 등장하는 위치의 인덱스를 반환함.|
|String[] split(String regex)	|해당 문자열을 전달된 정규 표현식(regular expression)에 따라 나눠서 반환함.|
|String substring(int beginIndex)|	해당 문자열의 전달된 인덱스부터 끝까지를 새로운 문자열로 반환함.|
|String substring(int begin, int end)	|해당 문자열의 전달된 시작 인덱스부터 마지막 인덱스까지를 새로운 문자열로 반환함.|
|String toLowerCase()	|해당 문자열의 모든 문자를 소문자로 변환함.|
|String toUpperCase()	|해당 문자열의 모든 문자를 대문자로 변환함.|
|String trim()	|해당 문자열의 맨 앞과 맨 뒤에 포함된 모든 공백 문자를 제거함.|
|length()	|해당 문자열의 길이를 반환함.|
|isEmpty()	|해당 문자열의 길이가 0이면 true를 반환하고, 아니면 false를 반환함.|
|equals()|해당 문자열이 인수와 동일한 값을 가지고 있는지를 비교하여 결과값을 리턴함. 같으면 true, 다르면 false|
|String replaceAll()|문자열 중 특정 문자를 다른 문자로 바꿔줌|

- String 객체의 값을 비교할때는 `equals`를 사용해야 한다. `==`를 사용할 경우 참조값을 비교해 동일한 객체인지 판별하기 때문에 값이 같아도 false를 반환한다.

- for each문 String에 적용하는 법
  ```java
  for (char c : "xyz")  //이렇게 할 경우 compile error 발생

  String str = "xyz";
  str.chars().forEachOrdered(i -> System.out.print((char)i));

  for (String s : "xyz".split("")) {
    System.out.println(s);
  }

  for (char ch: "xyz".toCharArray()) {

  }
  ```