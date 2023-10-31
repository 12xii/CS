# Memory managing

---

# 가상 메모리 virtual memory

- 컴퓨터가 실제로 이용 가능한 메모리 자원의 추상화 -> 사용자들에게 매우 큰 메모리로 보이게 함
    - 가상적으로 주어진 주소 : 가상 주소 logical address
    - 실제 메모리 상에 있는 주소 : 실제 주소 physical address
    - 가상 주소는 MMU에 의해 실제 주소로 변환 -> 실제 주소 의식 필요 없이 프로그램 구축 가능
- 페이지 테이블로 관리
    - 페이지 테이블 : 가상 주소와 실제 주소 매핑, 프로세스의 주소 정보가 포함
    - 속도 향상을 위해 TLB를 사용
        - TLB : CPU - 메모리 사이에 있는 주소 변환을 위한 캐시, 캐싱 계층

## 스와핑 swapping

- Page fault 발생 시 하드디스크의 일부를 메모리처럼 불러와 쓰는 것
  - 메모리에서 당장 사용하지 않는 영역을 하드디스크로 이전

- Page fault : 프로세스의 주소 공간에는 존재하나 RAM에는 없는 데이터에 접근 시 발생

## 스레싱 thrashing

- 메모리의 Page fault 발생률이 높은 것
- 컴퓨터의 심각한 성능 저하 초래
- 너무 많은 프로세스가 메모리에 동시에 올라갈 경우 스와핑 다수 발생 => 스레싱 발생
    - Page fault 발생 시 CPU 이용률 하락

- 해결법
    - Working Set
        - 지역성을 이용해 결정된 페이지 집합을 만들어 미리 메모리에 로드
        - 일정 시간을 ∆라고 할 때 $w(t, ∆)$ => $[t-∆, t]$ 동안 참조된 page의 집합
            - $∆$ : window size / system parameter
            - $∆$는 고정 / allocation은 가변
        - 스와핑 감소, 탐색 비용 감소
        - 적재되는 page가 없어도 메모리 반납이 가능하며 적재되는 page가 있어도 교체가 없을 수 있음
    - PFF (Page Fault Frequency)
        - 상한선 도달 시 프레임 증가 / 하한선 도달 시 프레임 삭제
        - IFT ( Inter Fault Time ) 을 따져서 기준에 따라 메모리 관리
            - Page Fault 발생 시 IFT 계산 ( Page Fault 일어난 시간의 차 )
            - 기준치 < IFT => ($t_{c-1}$, $t_{c}$] 동안 참조된 page만 유지, 나머지는 내림
            - 기준치 ≥ IFT => 현재 page 유지, 참조된 page 추가 적재 

## 메모리 할당
- 연속 할당
    - 메모리의 연속적인 공간에 할당
    - 방식
        - 고정 분할 방식 fixed partition allocation
        - 가변 분할 방식 variable partition allocation
- 불연속 할당 ( 비연속 할당 )
    - 페이징 Paging
        - 프로세스의 논리 메모리 영역과 물리 메모리 영역을 각각 동일한 일정 크기의 page와 frame으로 나눔
        - 페이지와 프레임에는 각각 번호 할당, 프로세스 페이지와 메모리 프레임을 매핑 by 페이지 테이블'
    - 세그멘테이션 Segmentation
    - 하이브리드 Hybrid / 페이지드 세그멘테이션 Paged Segmentation

### 페이지 교체 알고리즘
- 오프라인 알고리즘 offline algorithm / MIN algorithm / OPT algorithm
    - 가장 좋지만 실현 불가능한 알고리즘
    - 미래를 예측하여 가장 적게 할당되는 페이지를 교체
    - 다른 알고리즘과의 성능 비교에 사용
- FIFO
    - Page Fault 발생 시 가장 먼저 적재되었던 page를 교체
    - 지역성을 따지지 않음
- LRU
    - Page Fault 발생 시 가장 적게 참조되었던 page를 교체
    - 최근에 들어온 page가 곧바로 교체될 수 있음

---

# 참조

- <기술 면접 대비 CS전공 핵심요약집>, 2023, 이수진
- <면접을 위한 CS 전공지식 노트>, 2022, 주홍철