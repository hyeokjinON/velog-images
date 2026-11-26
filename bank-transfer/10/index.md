# bank-transfer #10 그림 목록

글: 은행 연동 송금 서비스 #10 — 보존 배치: VERIFIED 의 함정, DELETE LIMIT, READ COMMITTED 와 gap 락 (P5-2)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상(코드 15px)이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 10-1 | `10-01-overview.png` | 이 글을 한 장으로 | 06:30 시작 → 실행기 → 아웃박스 · 인증 두 단계 → 결과, 지우지 않는 것 |
| 10-2 | `10-02-hand-check-rows.png` | 0. 결론부터 (손 확인) | 시드 8행 중 아웃박스 1행 · 인증 3행만 지워지는 이유 (기준 시각과 비교) |
| 10-3 | `10-03-verified-trap.png` | 1. 함정 하나 | 인증 행의 일생: VERIFIED 도 expires_at 이 지나 있어 만료 시각만 보면 출금 422 |
| 10-4 | `10-04-tasklet-loop.png` | 2. 왜 Spring Batch, 왜 tasklet | 2,500행을 1,000 · 1,000 · 500 으로 세 번 커밋, 배수일 때 0건 호출 |
| 10-5a | `10-05a-repeatable-read-gap-lock.png` | 3. READ COMMITTED | REPEATABLE READ 범위 삭제의 next-key 락이 새 행의 빈 구간을 잠가 INSERT 대기 |
| 10-5b | `10-05b-read-committed-record-lock.png` | 3. READ COMMITTED | READ COMMITTED 는 지운 행만 잠가 INSERT 가 바로 들어감 |
| 10-6 | `10-06-mutation-lock-test.png` | 5. 변이 검사 | 잠금 테스트가 잡의 실제 속성을 꺼내 써서 변이 3 을 잡는 구조 |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`gen_b10.py`).
