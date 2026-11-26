# bank-transfer #4 그림 목록

글: 은행 연동 송금 서비스 #4 — 아웃박스 → Kafka → 은행 (P3-2)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 4-1 | `04-01-overview.png` | 이 글을 한 장으로 | 발행기 → Kafka → 컨슈머 → 조건부 UPDATE → 은행 → 결과 기록 → ack 의 흐름 |
| 4-2 | `04-02-resend-before-mark.png` | 이 단계가 푸는 문제를 장면으로 보면 (장면 1) | published_at 을 적기 전에 죽으면 같은 신호가 offset 0, 1 에 두 번 들어간다 |
| 4-3 | `04-03-skip-locked-two-relays.png` | 1. 발행 | 발행기 두 대가 SKIP LOCKED 로 서로 다른 행을 가져간다. FOR UPDATE 만 / 잠금 없음과 비교 |
| 4-4 | `04-04-consumer-conditional-update.png` | 2. 소비 | 같은 신호 두 개: UPDATE 1건인 쪽만 은행에 보내고 0건인 쪽은 ack 만 |
| 4-5 | `04-05-bank-outcomes.png` | 3. 은행 결과는 4가지 | 질문 세 개로 완료 · 거절 · 모름 · 안 보냄을 가른다 |
| 4-6 | `04-06-transaction-boundaries.png` | 3. 은행 호출은 트랜잭션 밖 | 트랜잭션 두 개 사이의 은행 호출, 죽는 시점별 결과, 버린 방식 |
| 4-7a | `04-07a-gap-lock-before.png` | 4. 최종 리뷰에서 나온 버그 | REPEATABLE READ 에서 빈 구간이 잠겨 새 아웃박스 INSERT 가 기다리다 1205 |
| 4-7b | `04-07b-gap-lock-after.png` | 4. 최종 리뷰에서 나온 버그 | 발행기만 READ COMMITTED: 행만 잠가 INSERT 가 바로 들어간다, 함께 고친 것과 테스트 |
| 4-8 | `04-08-blocking-retry.png` | 5. 은행이 아예 안 될 때 | 1 · 2 · 4 · 8 · 10초 간격 재시도 5번 뒤 commitRecovered 로 오프셋 커밋 |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`velog\bt04\gen_b04.py`, `render-b04.ps1`).
