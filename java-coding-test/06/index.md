# 자바 코딩테스트 6편 — 이분탐색 그림 목록

모든 그림은 가로 760px(PNG 는 2배인 1520px)이고 글자는 16px 이상이다. 글에는 PNG 를 넣고, SVG 는 원본이다. 그림 속 값은 JDK 21 에서 코드를 실행해 출력한 값이다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 그림 6-1 | `06-01-binarysearch0-trace.png` | 2-2. JDK 21 소스 — `Arrays.binarySearch0(int[])` | `{1, 3, 3, 3, 5, 8, 13}` 에서 4 를 찾을 때 닫힌 구간 [low, high] 가 세 바퀴 만에 비고, low = 4 에서 -5 를 돌려주는 모습 |
| 그림 6-2a | `06-02a-last-true-floor-loop.png` | 3-2. 무한 루프 | 마지막 T 찾기(x ≤ 5, [0, 10])에서 mid 를 내림으로 구하면 lo = 5, hi = 6 이 바뀌지 않고 반복되는 모습 |
| 그림 6-2b | `06-02b-last-true-ceil-ends.png` | 3-2. 무한 루프 | 같은 문제에서 mid 를 올림으로 구하면 mid 5, 8, 6 세 바퀴 만에 lo = hi = 5 로 끝나는 모습 |
| 그림 6-3 | `06-03-first-true-narrowing.png` | 4. 파라메트릭 서치 템플릿 | firstTrue(0, 100, x² ≥ 50) 에서 [lo, hi] 막대가 일곱 바퀴 동안 F 와 T 의 경계 8 로 줄어드는 모습 |
| 그림 6-4a | `06-04a-lower-bound-3.png` | 5. 패턴 ② lower bound / upper bound | lowerBound(a, 3) 이 반열린 구간에서 mid 3, 1, 0 을 거쳐 첫 3 의 위치 1 에 멈추는 모습 |
| 그림 6-4b | `06-04b-upper-bound-3.png` | 5. 패턴 ② lower bound / upper bound | upperBound(a, 3) 이 mid 3, 5, 4 를 거쳐 4 에 멈추고, 4 - 1 = 3 이 3 의 개수가 되는 모습 |
| 그림 6-5a | `06-05a-immigration-binary-search.png` | 6-3. 예제를 손으로 따라가기 | 입국심사 예제(n = 6, [7, 10])에서 mid 21, 32, 27, 30, 29, 28 의 판정(본 사람 수)과 구간 변화 |
| 그림 6-5b | `06-05b-immigration-timeline.png` | 6-3. 예제를 손으로 따라가기 | 두 심사관의 시간표, 27분까지 5명 · 28분까지 6명, 6번이 21분까지 기다려 7분 심사관에게 가는 장면 |
| 그림 6-6 | `06-06-overflow-early-exit.png` | 6-6. 실수 포인트 | 판정 함수에 일찍 끝내기가 있으면 첫 심사관에서 true, 없으면 19 번째 심사관에서 done 이 음수로 넘치는 과정 |
