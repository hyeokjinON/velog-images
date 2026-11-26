# bank-transfer #16 그림 목록

글: 은행 연동 송금 서비스 #16 — 쿠버네티스로 옮기고 일부러 부숴 봤다 (P8-3a)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 16-1 | `16-01-overview.png` | 이 글을 한 장으로 | PC > WSL2 > 노드 컨테이너 3개 > Pod 의 2중 구조와 배치 |
| 16-2 | `16-02-request-path.png` | 1. 구조 | 출금 요청 하나가 Postman → Envoy → api → MySQL · Kafka → 게이트웨이 → 모의 은행으로 가는 길 |
| 16-3a | `16-03a-prestop-0s.png` | 3. 롤링 업데이트 | preStop 0초: 입구 목록 갱신보다 앱 종료가 빨라 503 UF (5xx 4 · 9) |
| 16-3b | `16-03b-prestop-10s.png` | 3. 롤링 업데이트 | preStop 10초: 입구가 먼저 빼고 앱이 닫혀 5xx 0 · 0 |
| 16-4 | `16-04-bank-outage-probes.png` | 4. 은행 장애 | readiness 만(B1) 재시작 0 vs liveness 까지(B2) 재시작 1 · 2 |
| 16-5 | `16-05-reconnect-backoff.png` | 4. 숫자가 가설과 달랐다 | 재접속 대기 1 → 30초 상한이 복구 6.7 ~ 34초 편차를 만든 이유 (시도 시각은 설명용 계산값) |
| 16-6 | `16-06-networkpolicy-check.png` | 5. NetworkPolicy | 양성 대조 → FQDN → 종료 코드 28 만 막힘으로 보는 확인 순서 |
| 16-7 | `16-07-drain-overlap.png` | 6. drain | drain-1 에서 Recreate 게이트웨이 두 대가 함께 Ready 였던 구간 (+6.0 ~ +11.7초) |
| 16-8 | `16-08-node-stop-timeline.png` | 6. 노드 정지 | 감지 약 50초(5xx) + 퇴거 대기 300 vs 30초 → 대체 api 363 vs 88초 |
| 16-9 | `16-09-spread-skew.png` | 6. 레플리카 2개 ≠ 이중화 | 옛 ReplicaSet Pod 까지 세면 두 api 가 한 워커로 몰리는 과정과 matchLabelKeys 로 고친 뒤 (단순화한 순서) |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`b16/gen_b16.py`). 사이드 프로젝트 가이드 `images/11/*.svg`(1100px)는 내용만 참고하고 760px 로 새로 그렸다.
