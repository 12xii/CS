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

### 합병 정렬 merge sort

- 재귀를 이용하는 분할 정복 알고리즘
    - 분할 : 배열을 쪼갬
    - 정복 : 분할한 배열을 정렬하며 하나로 합병
- 정렬하려는 배열의 크기가 0 또는 1이 될 때까지 절반씩 분할
- 합병 시 합병의 대상이 되는 배열 2개와 배열 두 개를 합친 크기의 빈 배열이 필요

<img src = "https://images.velog.io/images/peanut_/post/37548189-961b-4912-b1c2-353ee306bbdd/image.png" width = "400px">

- 시간 복잡도는 $O(n \log n)$ => 수행 시간 면에서 효율적
    - $O(n)$ : 배열이 정렬되는 데 걸리는 시간 복잡도
    - $O(\log n)$ : 배열의 분할 또는 합병 시 걸리는 시간 복잡도

### 퀵 정렬 quick sort

- 분할 정복 알고리즘
- 배열에서 특정 값 **피벗 pivot**을 선택하여 피벗보다 작은 값으로 구성된 배열과 피벗보다 큰 값으로 구성된 배열로 분할 정복
- 수행 시 low와 high라는 변수를 통해 피벗을 기준으로 배열을 분할해 정렬
    - low는 첫 번째 요소에서, high는 마지막 요소에서 시작
    - low가 피벗보다 작을 경우 오른쪽으로 한 칸 이동, high가 피벗보다 클 경우 왼쪽으로 한 칸 이동
    - low와 high가 모두 이동하지 않을 시 두 변수가 가리키는 값을 교환
    - low가 high보다 오른쪽에 위치할 경우 배열이 피벗을 기준으로 정렬되었으므로 분리
- 분할은 배열의 크기가 1 이하가 될 때까지 반복

<img src = "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRjU60xIibiTbv3As3FcB1OEUy3UEY2M_AgSxmujkSLnftXvPBpHI484YSb_k3AFgBGbHE&usqp=CAU" width = "400px">

- 시간 복잡도는 $O(n \log n)$이지만 평균적인 시간 복잡도가 되려면 피벗을 기준으로 배열의 균등 분할이 가능해야 함
    - 역순 배열 정렬의 경우 $O(n^{2})$가 될 수 있음
    - 즉 피벗을 어떤 값으로 선택하느냐에 따라 퀵 정렬의 성능이 좌우됨

### 힙 정렬 heap sort

- 최대 힙이나 최소 힙 자료 구조를 이용해 정렬 수행
    - 최대 힙 : 오름차순
    - 최소 힙 : 내림차순
- 힙 정렬 과정 (2종류)
    - 힙 생성 알고리즘 과정 heapify : 배열 -> 힙
    - 힙에서 요소를 꺼내 정렬하는 과정
- 과정
    1. n개의 노드에 대한 완전 이진 트리를 구성한다. 이때 루트 노드부터 부모노드, 왼쪽 자식노드, 오른쪽 자식노드 순으로 구성한다.
    2. 최대 힙을 구성한다. 최대 힙이란 부모노드가 자식노드보다 큰 트리를 말하는데, 단말 노드를 자식노드로 가진 부모노드부터 구성하며 아래부터 루트까지 올라오며 순차적으로 만들어 갈 수 있다.
    3. 가장 큰 수(루트에 위치)를 가장 작은 수와 교환한다.
    4. 2와 3을 반복한다.

<img src="https://velog.velcdn.com/images%2Femplam27%2Fpost%2F5d2c2b06-676c-45dd-b7cd-c20c22134345%2F%ED%9E%99%EC%A0%95%EB%A0%AC1.png" width = "400px">
<img src="https://velog.velcdn.com/images%2Femplam27%2Fpost%2F38089014-6d91-4285-80bf-bd524270a4f3%2F%ED%9E%99%EC%A0%95%EB%A0%AC2.png" width = "400px">

*2023.11.03 - 사실 힙 정렬 알고리즘은 잘 모르겠다... 더 이해를 해봐야 할 것 같다*



---

## 비교하지 않는 정렬 알고리즘
