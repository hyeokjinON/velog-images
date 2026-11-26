# bank-transfer #9 그림 목록

글: 은행 연동 송금 서비스 #9 — 일마감 대사, 대사 파일, 은행 점검 시간, Spring Batch, 텔레그램 알림 (P5-1)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 9-1 | `09-01-overview.png` | 이 글을 한 장으로 | 은행 파일과 우리 출금을 거래번호로 맞추고, 결과를 모르는 출금만 확정하고 나머지는 기록 · 알림 |
| 9-2 | `09-02-recon-file-layout.png` | 0. 대사 파일은 이렇게 생겼다 | `RECON_20261030.dat` 예시 4줄과 상세 줄의 필드별 바이트(합 59) |
| 9-3a | `09-03a-verdict-open-transfers.png` | 1. 왜 결과를 모르는 출금만 고치나 | `UNKNOWN` · `SENDING` · `RECEIVED` 의 판정과 하는 일 |
| 9-3b | `09-03b-verdict-closed-transfers.png` | 1. 왜 결과를 모르는 출금만 고치나 | `COMPLETED` · `FAILED` · 우리에게 없는 줄 · 지갑의 판정 |
| 9-4 | `09-04-date-boundary.png` | 2. 날짜 경계 | 점검 시간이 없을 때 자정 직전 출금이 어긋나는 모습과, 23:50 ~ 00:10 점검이 있을 때 |
| 9-5a | `09-05a-job-steps-1-3.png` | 3. Spring Batch 6 잡 | ① 검증 ② 적재 ③ 우리 출금 판정과 손 확인(10-30) 때의 값 |
| 9-5b | `09-05b-job-steps-4-6.png` | 3. Spring Batch 6 잡 | ④ 은행 줄 ⑤ 원장 ⑥ 보고와 손 확인 값, 실패 경로 |
| 9-6 | `09-06-reread-isolation.png` | 3. ③ ④ 를 READ COMMITTED 로 낮춘 이유 | 확정 0건 뒤 다시 읽기: `REPEATABLE READ` 는 옛 상태, `READ COMMITTED` 는 새 상태 |
| 9-7a | `09-07a-resent-status-only.png` | 4. (1) 읽은 뒤 다시 보내진 출금 | 상태만 보는 조건이면 환불 후 은행이 처리해 이중 지급 |
| 9-7b | `09-07b-resent-sending-at-guard.png` | 4. (1) 읽은 뒤 다시 보내진 출금 | `sending_at` 범위 조건을 같은 UPDATE 에 넣으면 0건 → `RESENT_LATER` |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`gen_b09.py`).
