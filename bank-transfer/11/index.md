# bank-transfer #11 그림 목록

글: 은행 연동 송금 서비스 #11 — 코루틴이 빨라서가 아니다, 동시에 기다릴 수 있는 수 · 측정 49회 (P6-1)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다. 수치는 `bank-transfer/docs/perf/p6-1-consumer-coroutines.md` 와 같다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 11-1 | `11-01-overview.png` | 이 글을 한 장으로 | blocking 스레드 3개 대 coroutine 자리 64개, 대조 실험(상한 3), 운영 기본 blocking |
| 11-2 | `11-02-first-300ms.png` | 0. 결론부터 | 은행 지연 100ms 에서 처음 300ms 에 blocking 9건, coroutine 150건 (예시) |
| 11-3 | `11-03-thread-hops.png` | 1. 먼저 실험 | 코루틴 출금 한 건이 지나가는 스레드, await 뒤 Netty 이벤트 루프 → IO 스레드로 넘기기 |
| 11-4a | `11-04a-draft-sending-before-permit.png` | 3. 돈이 걸린 순서 | 버린 초안: SENDING 뒤 자리 대기 → 정리 작업 환불 뒤 송금 (CONFLICT) |
| 11-4b | `11-04b-permit-before-begin.png` | 3. 돈이 걸린 순서 | 채택: 자리를 먼저 잡고 begin 은 자리 안, 기다리는 동안 RECEIVED |
| 11-5 | `11-05-measure-one-run.png` | 4. 측정 방법 | 측정 한 회: 사전 확인 → 시드 → 발행만 → 처리만 → DB 시각 계산 → 정확성 |
| 11-6 | `11-06-control-permit-time.png` | 5. 대조 실험 | 자리 하나 쥐는 시간 blocking 약 144ms 대 coroutine 상한 3 약 123ms (계산) |
| 11-7a | `11-07a-ceiling-150.png` | 6. 용량 탐색 | 컨슈머 3 × poll 50 = 150 에서 은행 동시 호출이 멈추는 이유 |
| 11-7b | `11-07b-capacity-sweep.png` | 6. 용량 탐색 | 상한 16 ~ 256 처리량과 예상, 상한 256 에서 Hikari 10 / 20 / 40 |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`velog/b11/gen_b11.py`).
