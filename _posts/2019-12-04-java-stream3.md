---
layout: post
title: "[Java] 자바 스트림 API 공부하기(3)"
---
### [Java] 자바 스트림 API 공부하기(3)
<br><br>
앞선 포스팅과같이 스트림 API를 사용한 예제를 정리!<br>
<br>
#### 사용 메소드
```
distinct
sorted
min
sum
average
getAsDouble
getAsInt
```
<br><br>
#### distinct, sorted
distinct: 스트림 요소들중 중복을 제거해주는 메소드.<br>
sorted: 스트림 요소들을 정렬해주는 메소드. default는 오름차순<br>
```
예제
public static void main(String[] args) {
	double[] failArr = new double[5];
	failArr[0]=1.1;failArr[1]=0.1;failArr[2]=1.6;failArr[3]=1.1;failArr[4]=2.1;
	failArr = Arrays.stream(failArr).distinct().sorted().toArray();
}
```
```
결과
int[] failArr: [0.1, 1.1, 1.6, 2.1]
```
failArr = [1.1, 0.1, 1.6, 1.1, 2.1] 에서 중복을 제거하고 오름차순으로 정렬하여 결과와 같은 배열을 얻었다.<br>
알고리즘 문제를 풀다보면 중복제거, 정렬이 많이 필요하다.<br>
이전에는 주로 Set, Arrays.sort를 많이 사용했었는데<br>
스트림 API 사용법을 알게됐으니 이제 스트림을 많이 쓸 것 같다ㅎㅎ<br>
<br><br>

#### min, sum, average, getAsDouble, getAsInt
min: 스트림 요소들중 가장 작은 수 찾는 메소드.<br>
sum: 스트림 요소들 모두 더하는 메소드.<br>
average: 스트림 요소들의 평균값을 내는 메소드.<br>
getAsDouble: 계산된 스트림 요소를 double형으로 변환하여 리턴.<br>
getAsInt: 계산된 스트림 요소를 int형으로 변환하여 리턴.<br>
```
예제
public static void main(String[] args) {
	int[] scoreArr = new int[5];
	scoreArr[0]=10;scoreArr[1]=20;scoreArr[2]=30;scoreArr[3]=40;scoreArr[4]=50;
	
	int min = Arrays.stream(scoreArr).min().getAsInt();
	int sum = Arrays.stream(scoreArr).sum();
	double average = Arrays.stream(scoreArr).average().getAsDouble();
}
```
```
결과
min: 10
sum: 150
average: 30.0
```
수학관련 작업을 도와주는 메소드들. 프로그래머스 문제를 풀 때 아주 유용하게 사용했음.<br>
메소드 이름만 봐도 직관적으로 하는일을 알 수 있어서 이해하기 쉽다.<br>

<br><br>
예제로 쓰인 모든 코드는 제가 푼 프로그래머스 코드를 인용한 것으로<br>
제 github의 studyJava 프로젝트에 올라와 있으니 확인이 가능합니다.<br><br>
스트림 API를 사용한 예제들을 몇 개 정리해보며 리마인드 해보았다.<br>
아직은 스트림 API의 모든 것을 써본 것이 아니라 서툰점도 있지만<br>
차근차근 더 공부해나가야겠다!<br>
시작이 반이니까 나는 반이상 한 것 ㅎㅎㅎㅎㅎ<br>
끝!