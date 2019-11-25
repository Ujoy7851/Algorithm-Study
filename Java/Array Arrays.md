## Array 배열

배열은 같은 타입의 데이터를 연속된 공간에 나열시키고 각 데이터에 인덱스(index)를 부여해 놓은 자료구조로, 한 번 생성하면 그 길이를 변경할 수 없다.

배열 변수는 참조변수로 힙 영역에 생성된 배열 객체를 참조한다. 따라서 new를 해주지 않으면 해당 배열은 null값을 가지며, 이를 이용하려고 하면 NullPointerException이 발생한다.

```java
//선언과 동시에 초기화
int[] odds = {1, 3, 5, 7, 9};
String[] weeks = {"월", "화", "수", "목", "금", "토", "일"};


//선언 후 초기화
int[] i = new int[8];   //초기값 0
String[] weeks = new String[7]; //초기값 ""
weeks[0] = "월";
weeks[1] = "화";


//선언만 해놓고 나중에 초기화 시켜도 됨
int[] array;
array = new int[3];
Arrays.fill(array, 1);  //모든 값을 1로 초기화



//초기값없이 배열을 만들때 아래처럼 길이값없이 선언하면 안됨.
String[] weeks = new String[];


//객체 배열 선언
Car[] car = new Car[3]; //배열의 각 원소는 아직 null값
for(int i=0; i < car.length; i++) {
	car[i] = new Car(); //초기화 시켜줘야함
}


//dynamic array - 2차원 배열을 생성할 때 열의 길이를 명시하지 않으면, 행마다 다른 길이의 배열을 요소로 저장할 수 있음.
int[][] arr = new int[2][];
arr[0] = new int[2];
arr[1] = new int[4];
```

#### 배열의 크기
```java
int[] odds = {1, 3, 5, 7, 9};
System.out.println(odds.length);  //5
//odds.length()가 아님 주의!
```

#### for-each문

배열에 for-each문을 사용할 수 있지만 for-each 문 내부에서 사용되는 배열 요소는 배열 요소 그 자체가 아닌 배열 요소의 복사본이다. 값의 변경이 불가능하므로 요소를 참조할 때만 사용하는 것이 좋다.

```java
int[] arr = new int[]{1, 2, 3, 4, 5};
for (int e : arr2) {
    e += 10;
}
//{1, 2, 3, 4, 5}
```

#### 배열의 복사
- System 클래스의 arraycopy() 메소드
- Arrays 클래스의 copyOf(), copyOfRange() 메소드
- Object 클래스의 clone() 메소드
- for 문과 인덱스를 이용한 복사

```java
int[] arr1 = new int[]{1, 2, 3, 4, 5};
int newLen = 10;

//System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length);
int[] arr2 = new int[newLen];
System.arraycopy(arr1, 0, arr2, 0, arr1.length);

//Arrays.copyOf(T[] original, int newLength)
//비는 부분은 0 또는 null로 padding
int[] arr3 = Arrays.copyOf(arr1, 10);

int[] arr4 = (int[])arr1.clone();

int[] arr5 = new int[newLen];
for(int i=0; i < arr5.length; i++) {
    arr5[i] = arr1[i];
}
```

가장 성능이 좋은 것은 arraycopy(), 가장 많이 사용되는 메소드는 copyOf()이다.

arraycopy(), copyOf() 메소드와 for 문을 이용한 복사는 배열의 길이를 마음대로 늘일 수 있지만, clone() 메소드는 이전 배열과 같은 길이의 배열밖에 만들 수 없다.

#### 배열 전체 출력
배열을 그대로 출력하면 hashcode가 출력된다.
배열을 문자열로 출력하려면 Arrays 클래스의 toString, deepToString 메소드를 사용한다. (1차원 배열은 toString, 다차원 배열은 deepToString 사용)
```java
int[] arr1 = {5, 2, 1, 6, 7};
int[][] arr2 = {{1, 2, 3, 4, 5}, {5, 4, 3, 2, 1}}; 
System.out.println(arr1);    //[I@15db9742
System.out.println(Arrays.toString(arr1));   //[5, 2, 1, 6, 7]
System.out.println(Arrays.deepToString(arr2));  //[[1, 2, 3, 4, 5], [5, 4, 3, 2, 1]]
```

#### 배열 정렬
- 오름차순 : Arrays.sort(arr);
- 내림차순: Arrays.sort(arr, Comparator.reverseOrder());

---

## java.util.Arrays 클래스
배열을 다루기 위해 유용한 메소드를 포함한 클래스로 java.util.Arrays를 import 해줘야 사용 가능하다.

Arrays 클래스의 모든 메소드는 Static method이므로, 객체를 생성하지 않고 바로 사용할 수 있다.


메소드 | 설명
----|---
static <T> List<T> asList(T... a) | 전달받은 배열을 고정 크기의 리스트(list)로 변환하여 반환함.
static int binarySearch(Object[] a, Object key) | 전달받은 배열에서 특정 객체를 이진 검색 알고리즘을 사용하여 검색한 후, 그 위치를 반환하고, 검색 안 된 경우 음수값을 반환함. 배열이 정렬되어 있어야 정상적으로 작동함.
static <T> T[] copyOf(T[] original, int newLength) | 전달받은 배열을 특정 길이의 새로운 배열로 복사하여 반환함.
static <T> T[] copyOfRange(T[] original, int from, int to) | 전달받은 배열의 특정 범위에 해당하는 요소만을 새로운 배열로 복사하여 반환함.
static boolean equals(Object[] a, Object[] a2) | 전달받은 두 배열이 같은지를 확인함.
static void fill(Object[] a, Object val) | 전달받은 배열의 모든 요소를 특정 값으로 초기화함.
static void sort(Object[] a), static <T> void sort(T[] a, Comparator<? super T> c) | 전달받은 배열의 모든 요소를 오름차순으로 정렬함.
static String toString(Object[] a) | 전달받은 배열의 모든 요소를 문자열로 반환함. ("[ , , ]"의 형태로 반환)

> Arrays.sort()는 Tim sort와, Dual-pivot Quick Sort를 사용한다. Tim sort는 stable 하므로 Object에, Dual-pivot Quick sort는 unstable 하므로 primitive type에 쓰인다.