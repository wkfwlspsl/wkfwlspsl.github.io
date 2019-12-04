---
layout: post
title: "[Java] 자바 스트림 API 공부하기(2)"
---
### [Java] 자바 스트림 API 공부하기(2)
<br><br>
자바 스트림 API를 공부한 후 실제 API를 써보면서 익혀보았다.<br>
그동안 프로그래머스 level1을 모두 풀었고 최대한 스트림을 써보려고 노력했다.<br>
총 39문제가 있었고 그중 난이도가 낮은 연습문제가 30개, 난이도가 조금 있는 문제가 9개다.<br>
level1이라 비교적 쉬운 문제들이었지만.. 현생을 살다보니 
공부할 시간이 별로 없어 생각보다 오래 걸렸다.<br>
내가 풀었던 코드중 스트림 API 코드를 인용해와 예제를 설명하면서 스트림 API 공부를 마치려고 한다.<br>
<br>
#### 사용 메소드
```
reduce
filter
boxed
collect
mapToInt
toArray
```
<br><br>
#### reduce
reduce: 스트림 요소들을 결합하여 새로운 결과를 도출하는 메소드.<br>
```
예제
public static void main(String[] args) {
	List<String> strList = new LinkedList<>();
	strList.add("abc");strList.add("02");strList.add("ㄱㄴㄷ");
	
	String resultStr = strList.stream().reduce((s1, s2) -> s1 + s2).get();
	System.out.println(resultStr);
}
```
```
결과
abc02ㄱㄴㄷ
```
strList에 있는 요소들을 스트림으로 만들어준 후에 모든 요소들을 더해서 String으로 return해주는 코드다.<br>
알고리즘 문제를 풀 때, string을 연결하는 로직이 필요할 때가 많은데<br>
그럴 때 사용하면 매우 유용한 코드다.<br>
<br><br>

#### filter, boxed, collect
filter: 조건에 맞는 스트림을 반환하는 메소드<br>
boxed: primitive type을 객체로 변환할 때 쓰는 메소드<br>
collect: 스트림 요소를 모을 때 쓰는 메소드<br>
```
예제
public static void main(String[] args) {
	int[] students = new int[5];
	students[0] = 1; students[1] = 0; students[2] = 0; students[3] = 1; students[4] = 1;
	
	List<Integer> stdList = Arrays.stream(students).boxed().collect(Collectors.toList());
	stdList = stdList.stream().filter(s -> s > 0).collect(Collectors.toList());
	System.out.println(stdList.size());
}
```
```
결과
3
```
0과 1로 구성된 int 배열을 List<Integer> 타입의 리스트로 만들어준 후<br>
stdList의 각 요소를 필터링 하면서 0보다 큰 값들만 리스트로 만들어준다<br>
primitive type을 박싱해서 계산해야할 때, 배열을 리스트로 변환해야할 때 boxed, collect 메소드를 활용하면 유용하고<br>
리스트 내에서 특정 조건에 맞는 요소만 추출할 때 filter메소드를 활용하면 유용하다<br>
<br><br>

#### mapToInt, toArray
mapToInt: 스트림 요소를 int형으로 바꾸는 메소드<br>
toArray: 스트림 요소들을 배열로 리턴<br>
```
예제
public static void main(String[] args) {
	String binary = "1010";
	int[] arr = Stream.of(binary.split("")).mapToInt(Integer::parseInt).toArray();
}
```
```
결과
int[] arr: [1, 0, 1, 0]
```
이진수로 표현된 string객체를 빈값으로 split하여 배열을 만들어준 후 스트림을 생성.<br>
각 요소마다 parseInt 메소드를 통해 int로 변환해준 후<br>
모든 스트림 요소를 array로 변환해주었다.<br>

<br><br>
예제로 쓰인 모든 코드는 제가 푼 프로그래머스 코드를 인용한 것으로<br>
제 github의 studyJava 프로젝트에 올라와 있으니 확인이 가능합니다.<br><br>
다음 포스팅에서는 distinct, sorted, min, sum, average, getAsDouble, getAsInt <br>
메소드 사용예제를 정리 해보려고 한다.<br>
To be continue..!