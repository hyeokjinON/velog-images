# 자바 코딩테스트 1편 — 문법 · API 암기 노트 그림 목록

모든 그림은 가로 760px(PNG 는 2배인 1520px)이고 글자는 16px 이상이다(고정폭 코드 · 값은 15px 이상). 글에는 PNG 를 넣고, SVG 는 원본이다. 그림 속 값은 JDK 21 로 실행해 출력한 값이다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 그림 1-1 | `01-01-ops-at-n-100000.png` | 1-3. 복잡도의 종류 | n = 100,000 에서 O(log n), O(n), O(n log n), O(n²) 의 연산 횟수를 로그 눈금 막대로 비교하고, 1억 번(약 1초) 선을 넘는 것이 O(n²) 뿐임을 보여 준다 |
| 그림 1-2 | `01-02-n-to-allowed-complexity.png` | 1-4. 허용 복잡도 | 제한사항의 n 범위 일곱 줄마다 허용 복잡도, 대입 결과, 떠올릴 알고리즘을 표로 묶었다 (예: n ≤ 1,000,000 → O(n log n) → 정렬, 이분탐색, 우선순위 큐) |
| 그림 1-3 | `01-03-arraylist-inside.png` | 1-6. 연산 복잡도 | ArrayList 안의 배열: 11번째 add 에서 10칸 → 15칸으로 옮겨 적기, add(0, "x") 가 원소 4개를 미는 모습, contains("z") 가 4번 비교하는 모습 |
| 그림 1-4 | `01-04-two-pointer-trace.png` | 1-8. 종합 예제 A | 정렬한 [-1, 1, 3, 3, 5, 7] 에서 합 10 을 찾을 때 반복 세 번 동안 l, r 의 위치와 버린 칸 |
| 그림 1-5 | `01-05-clone-shallow-deep.png` | 3-1. 배열 (2차원 복사 함정) | grid.clone() 은 행 배열 2개를 함께 가리켜 99 가 grid 에도 보이고, 행마다 clone() 하면 행 배열이 4개가 되어 77 이 grid 에 보이지 않는다 |
| 그림 1-6 | `01-06-arraydeque-ring.png` | 4-2. ArrayDeque | 17칸 배열에서 push 1, 2, 3 이 16, 15, 14번 칸에 들어가는 모습(head 이동)과 offer 1, 2, 3 이 0, 1, 2번 칸에 들어가는 모습(tail 이동), pop · poll 뒤의 head |
| 그림 1-7 | `01-07-priorityqueue-heap.png` | 4-3. PriorityQueue (더 맵게) | 힙 배열 [1, 2, 3, 9, 10, 12] → [3, 5, 10, 12, 9] → [9, 12, 10, 13] 과 각 단계의 트리 모양 |
| 그림 1-8 | `01-08-treemap-floor-ceiling.png` | 4-5. TreeMap / TreeSet | 키 0, 70, 80, 90 에서 x = 85 와 x = 80 일 때 floorKey, ceilingKey, lowerKey, higherKey 가 고르는 키 |
