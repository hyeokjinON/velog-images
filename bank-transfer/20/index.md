# bank-transfer #20 그림 목록

글: 은행 연동 송금 서비스 #20 — 출금 한 건을 trace 하나로 (P9b 분산 추적)

SVG 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 캡처(20-2, 20-6)는 가이드의 Grafana 화면 캡처에서 왼쪽 칸만 잘라 1.5배로 키운 것이다 (IP · 계정 없음 확인). 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 20-1 | `20-01-overview.png` | 이 글을 한 장으로 | 출금 한 건의 구간 7개, 스레드 · 프로세스별 위치, 자동 5곳과 손으로 이은 2곳, 아웃박스 대기 약 198ms |
| 20-2 | `20-02-tempo-trace-normal.png` | 0. 결론부터 | Tempo 에서 연 정상 출금 1건(304ms)의 구간 7개 (캡처) |
| 20-3 | `20-03-outbox-gap.png` | 2-1. 아웃박스 | 자동 계측만이면 trace 두 조각, trace_parent 열로 잇는 ①~⑤ |
| 20-4 | `20-04-traceparent.png` | 2-1. 아웃박스 | traceparent 55자의 네 칸과 실려 가는 곳(DB 열 · Kafka 헤더 · HTTP 헤더 · 로그, 은행 전문 제외) |
| 20-5 | `20-05-retry-vs-reconcile.png` | 2-2. 재시도는 같은 trace, 정리 작업은 새 trace | 재시도 토픽은 trace A, 정리 작업 재발행은 trace B, transfer.id 검색으로 함께 |
| 20-6 | `20-06-tempo-trace-bank-outage.png` | 2-2. 재시도는 같은 trace, 정리 작업은 새 trace | 은행 76초 끊김 중 출금 1건의 trace (20구간, 1분 37초, 캡처) |
| 20-7 | `20-07-export-pipeline.png` | 3. 넣지 않은 것 | 구간이 대기열 → 5초 묶음 → 거르기 → 예외 내용 지우기 → OTLP → Tempo 로 가는 길, Tempo 0대 실험 |
| 20-8 | `20-08-empty-reconcile-filter.png` | 5. PR 직전에 찾은 것 | 빈 정리 작업 판정 세 가지(옛 · parentId 만 · 새)를 실행 두 종류에 대 본 결과 |

같은 이름의 `.svg` 가 원본이다 (캡처 두 장은 PNG 만). 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`gen_b20.py`).
