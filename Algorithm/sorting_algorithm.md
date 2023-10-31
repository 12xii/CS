# 정렬 알고리즘 Sorting Algorithm

---

## 비교하여 정렬하는 알고리즘

### 버블 정렬 bubble sort

- 양옆에 위치한 두 값을 비교하며 크기 순으로 정렬
- 배열의 뒤에서부터 정렬

<img src = "https://velog.velcdn.com/images/belper6/post/67cec295-6f2d-4b65-8acc-05f1f4b88453/image.png" width = "400px">

https://velog.io/@belper6/TIL-.-123-%EB%B2%84%EB%B8%94-%EC%A0%95%EB%A0%AC

- n번째 요소 정렬에 (n-1)번 비교 -> 연산 수행 횟수는 $\frac {n(n - 1)} {2}$ -> 시간복잡도 O($n^{2}$)
- 정렬 수행에 느린 편
- 별도의 메모리 공간이 필요하지 않음

### 선택 정렬 selection sort

- 배열을 순회하며 인덱스 $ i $ 부터 마지막 인덱스까지의 요소 중 최솟값을 선택해 위치를 교환

<img src = "https://blog.kakaocdn.net/dn/be0U7M/btrjJyxJxPy/DWJ1ZkW8dD7CJ7VJf1g9rK/img.jpg" width = "400px">

- 배열 전체에 대한 정렬 : $ (n-1) + (n-2) + ... + 2 + 1 = \frac {n(n-1)} {2} $ 번 수행하므로 시간 복잡도는 $ O(n^{2}) $
- 수행 시간은 느린 편이나 메모리 공간 불필요, 구현이 간단

### 삽입 정렬 insertion sort

- 배열을 앞에서부터 순회하며 정렬된 부분의 적절한 위치에 값을 삽입
- 인덱스 $ i $에 있는 $ a $를 정렬할 차례일 때, 인덱스 0부터 $ i - 1 $까지는 이미 정렬되어 있는 상태라면 정렬된 부분에서 $a_{1} \leq a \leq a_{2}$인 부분을 찾아 그 사이에 $ a $를 삽입

<img src = "https://miro.medium.com/v2/resize:fit:600/1*GwH68Z8NE5PA50AaaAieUw.png" width = "400px">

- 최대 $n-i$번을 탐색 -> $1 + 2 + ... + (n - 2) + (n - 1) = \frac {n(n-1)} {2}$
- 시간 복잡도는 $O(n^{2})$

---

## 비교하지 않는 정렬 알고리즘
