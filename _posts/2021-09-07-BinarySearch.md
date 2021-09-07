---
layout: single
title: '[Algorithm] Binary Search, 이진탐색'
---

오름차순 정렬된 정수의 배열(arr)과 정수(target)를 입력받아 target의 인덱스를 리턴해야 한다.

입력
인자1 : arr
- number 타입을 요소로 갖는 배열
- arr[i]는 정수

인자2: target
- number 타입의 정수

출력
- number 타입을 리턴한다.

주의사항
- 이진 탐색 알고리즘을 사용해야 한다.
- 단순한 배열 순회로는 전부 통과할 수 없다
- target이 없는 경우엔 -1을 리턴한다.

![](https://images.velog.io/images/skagns211/post/666b90cc-513b-4cd7-8710-9932c35fafdc/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-09-07%2021.58.54.png)


위 그림과 같이 입력된 배열을 반으로 나누고, 나눴을 때의 index element가 target보다 크므로 우측은 전부 버리고 좌측을 다시 반으로 나누고, 나눴을 때의 index element가 target이므로 그 index를 리턴한다.

```jsx
const binarySearch = function (arr, target) {
  // 🟥 배열의 0번째 idx와 마지막 idx를 선언해준다
  let left = 0,
  let right = arr.length - 1; 
  // 🟥 left(시작)가 right(끝)와 같거나 작을동안 실행
	while (left <= right) {
	  // 🟥 middle(반으로 나눈 idx). 홀수일시 소숫점이 나오므로 parseInt로 정수로 뽑아온다
	  let middle = parseInt((right + left) / 2);
	  // 🟥 arr[middle] (arr을 반으로 나눈 idx)가 target이면 middle를 리턴한다.
	  if (arr[middle] === target) {
	    return middle;
	  }
	  // 🟥 target이 반으로 나눈 녀석보다 작다면 right는 middle - 1을 해준다
	  // (middle는 target이 아니란걸 확인했고 target이 그것보다 작으므로 필요없는 부분 삭제)
	  if (target < arr[middle]) {
	    right = middle - 1;
	  // 🟥 그게 아니고 target이 반으로 나눈 녀석보다 크다면 left는 middle + 1을 해준다
	  // (middle는 target이 아니란걸 확인했고 target이 그것보다 크므로 필요없는 부분 삭제)
	  } else {
	    left = middle + 1;
	  }
	}
	return -1;
};
```