# codingtest-greedy
[큰 수의 법칙, biggest number]


순서대로 배열의 크기 n, 총 덧셈 횟수 m, 특정 인덱스가 연속해서 더해질 수 있는 값 n 을 입력 받는다.

예를 들면 2,4,5,4,6 으로 이루어진 배열이 있을 때 m이 8이고 k가 3이라고 가정한다.
그러면 가장 큰수인 6과 다음수인 5가 6+6+6+5+6+6+6+5 = 46 으로 값이 구해진다.

일단 배열을 sort로 정렬하고 가장 큰수인 마지막 인덱스와 두번째로 큰 수인 인덱스를 first와 second로 정의해줬다.

first=arr[n-1]
second=arr[n-2]

처음에는 for문을 이용하여 result에 값을 누적시키는 방법으로 구현하였다.
하지만 이 방법은 m이 커진다면 시간 초과 판정을 받을 것이다.

수학적인 접근방법으로 다시 해결해보았다.
반복되는 수열의 길이는 k+1이다. 따라서 m을 k+1로 나눈 몫이 수열의 반복 횟수가 된다.
ex) 6+6+6+5   +6+6+6+5    => 수열의 길이 4 : (k+1=3+1), 수열의 반복 횟수 2 : (m/(k+1) = 8/(3+1))
이때 m이 k+1로 나누어 떨어지지 않을 경우도 고려해야하므로, m%(k+1)를 더해준다.

결과적으로 가장 큰 수가 더해지는 횟수의 식은 int(m/(k+1)) * k + m%(k+1) 이 된다.
따라서 result값에는 first값에 위의 식을 곱해준 값과 위의 식에서 m 값을 뺀 값과 second 을 곱한 값을 누적시켜주면 최종 답안이 출력된다.
