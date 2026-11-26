# 자바 코딩테스트 2편 — 해시 그림 목록

모든 그림은 가로 760px(PNG 는 2배인 1520px)이고 글자는 16px 이상이다(고정폭 코드 · 값은 15px 이상). 글에는 PNG 를 넣고, SVG 는 원본이다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 그림 2-1 | `02-01-bucket-index.png` | 2-1. 키 → 칸 번호 계산 | apple, banana, cherry 가 hashCode → 섞기 → 아래 4비트로 칸 번호를 얻는 과정과, 실제 HashMap 내부 배열(0번 칸 banana → date, 1번 칸 apple → cherry) |
| 그림 2-2 | `02-02-same-hash-resize-treeify.png` | 2-2. 충돌 | hashCode 가 모두 42 인 키 11개를 넣을 때 16칸 → 32칸 → 64칸으로 resize 된 뒤에야 칸이 트리가 되는 과정 |
| 그림 2-3 | `02-03-mutated-key-lost.png` | 3. equals / hashCode 계약 | 넣은 뒤 키 필드를 바꾸면 원소는 2번 칸에 남는데 get(p) 는 10번 칸, get(new (1,2)) 는 equals 에서 실패한다 |
| 그림 2-4 | `02-04-prefix-sum-count.png` | 4. 패턴 ⑦ 누적합 + 해시 | [1,2,3,-3,3], k=3 에서 반복마다 sum, sum−3, seen 에서 찾은 횟수와 찾은 구간 |
| 그림 2-5a | `02-05a-marathon-hash-trace.png` | 5-1. 완주하지 못한 선수 — 예제를 손으로 따라가기 | 예 3 을 해시 풀이로: merge 마다 ana, mislav, stanko 의 개수가 바뀌어 mislav 만 1 이 남는다 |
| 그림 2-5b | `02-05b-marathon-sort-trace.png` | 5-1. 완주하지 못한 선수 — 예제를 손으로 따라가기 | 예 3 을 정렬 풀이로: 같은 위치끼리 비교하다 2번 칸에서 처음 어긋난다. 예 1 은 끝까지 같아 마지막 사람 |
| 그림 2-6 | `02-06-ponketmon-set.png` | 5-2. 폰켓몬 — 예제를 손으로 따라가기 | 예 1, 2, 3 에서 Set 에 남은 종류 수와 N/2 를 막대로 비교해 min 을 구한다 |
| 그림 2-7a | `02-07a-phonebook-hash-trace.png` | 5-3. 전화번호 목록 — 예제를 손으로 따라가기 | 예 1 을 해시 풀이로: 번호마다 만든 접두어 12개 중 1195524421 의 "119" 에서 Set 에 있어 멈춘다 |
| 그림 2-7b | `02-07b-phonebook-sort-neighbors.png` | 5-3. 전화번호 목록 — 예제를 손으로 따라가기 | 예 1 정렬 전후, 예 3 에서 "12" 로 시작하는 번호가 정렬 후 연달아 오는 모습(이웃만 비교해도 되는 이유) |
