# 자바 코딩테스트 5편 — 스택 · 큐 그림 목록

모든 그림은 가로 760px(PNG 는 2배인 1520px)이고 글자는 16px 이상이다. 글에는 PNG 를 넣고, SVG 는 원본이다. 그림 속 값은 JDK 21 에서 코드를 실행해 출력한 값이다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 그림 5-1 | `05-01-stack-vs-arraydeque-push-order.png` | 2-1. `Stack` 은 `Vector` 를 상속했다 | 같은 push 1, 2, 3 이 `Stack` 은 배열 0번 칸부터, `ArrayDeque` 는 head 를 왼쪽으로 옮기며 들어가 출력 순서가 반대가 되는 모습 |
| 그림 5-2 | `05-02-arraydeque-circular-head-tail.png` | 2-2. `ArrayDeque` 는 원형 배열이다 | 길이 8 배열에서 offerLast 1, 2, 3 뒤 offerFirst 0 을 하면 head 가 0 에서 7 로 돌아가는 과정과 배열 확장 17 → 36 → 74 → 111 |
| 그림 5-3 | `05-03-simulate-vs-calculate-days.png` | 3. 큐 시뮬레이션 두 방식 | 기능개발 예제 1 의 작업별 완료일(7, 3, 9)과 배포일, 하루씩 흘리기와 바로 계산이 하는 일의 양 비교 |
| 그림 5-4 | `05-04-monotonic-stack-next-greater.png` | 4. 패턴 ③ 단조 스택 | `[9, 1, 5, 3, 6, 2]` 에서 바퀴마다 스택(인덱스:값)과 ans 가 바뀌는 모습, push 6번 · pop 3번 |
| 그림 5-5 | `05-05-two-stack-queue.png` | 4. 패턴 ⑥ 스택 2개로 큐 만들기 | offer 1, 2 → poll → offer 3 → poll → poll 에서 in · out 스택과 반환값, "out 이 빌 때만 옮긴다" |
| 그림 5-6 | `05-06-valid-parentheses-trace.png` | 5-1. 예제를 손으로 따라가기 — 예 2 | `"(())()"` 에서 스택 크기와 카운터 open 이 함께 움직이는 모습, 예 3 · 예 4 가 false 가 되는 지점 |
| 그림 5-7a | `05-07a-deploy-sim-day-by-day.png` | 5-2. 예제를 손으로 따라가기 — 예 1 | 하루씩 흘리기에서 9일 동안 진도 p, 큐 q, answer 가 바뀌는 모습 (작업 1 이 3 ~ 6일째 대기) |
| 그림 5-7b | `05-07b-deploy-calc-groups.png` | 5-2. 예제를 손으로 따라가기 — 예 2 | 완료일 5, 10, 1, 1, 20, 1 을 releaseDay 와 비교해 [1, 3, 2] 로 묶는 과정 |
| 그림 5-8a | `05-08a-process-queue-rotation.png` | 5-3. 예제를 손으로 따라가기 — 예 2 | 프로세스 A ~ F 를 꺼내 뒤로 보내거나 실행하는 큐 회전, A 가 다섯 번째로 실행 |
| 그림 5-8b | `05-08b-process-heap-vs-count.png` | 5-3. 예제를 손으로 따라가기 — 예 2 | 같은 꺼내기에서 최대 힙과 개수 배열(cnt, max)이 "남은 것 중 최댓값" 을 알려 주는 모습 |
