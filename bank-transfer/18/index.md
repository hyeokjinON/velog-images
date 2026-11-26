# bank-transfer #18 그림 목록

글: 은행 연동 송금 서비스 #18 — 복제본 2개는 이중화가 아니다, DoNotSchedule 로 353초 → 14.4초 (P8-3c)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 18-1 | `18-01-overview.png` | 이 글을 한 장으로 | 워커가 빠지면 대체 게이트웨이는 Pending, 워커가 돌아오면 그 워커에 뜬다 |
| 18-2a | `18-02a-before-colocate.png` | 1. 어떻게 몰렸나 | `ScheduleAnyway` 에서 두 대가 한 워커에 몰리고 353.4초(감지 약 50초 + 축출 대기 300초) |
| 18-2b | `18-02b-after-spread.png` | 1. 어떻게 몰렸나 | `DoNotSchedule` 에서 같은 순서(S3 → S4)가 Pending → 복귀 → 14.4초, 막대 비교 |
| 18-3 | `18-03-skew-count.png` | 2. 바꾼 것 | `nodeTaintsPolicy` Ignore 는 빠진 워커를 0개 칸으로 세서 금지, Honor 는 빼서 허용(몰림) |
| 18-4 | `18-04-rolling-count.png` | 2. 바꾼 것 | 롤링 중 같은 리비전끼리만 세면 N2 가 반드시 다른 워커로, 옛 Pod 까지 세면 몰릴 수 있음, 필수 anti-affinity 는 멈춤 |
| 18-5 | `18-05-pending-reasons.png` | 3. 직접 해 본 것 | `0/3 nodes are available` 문구를 노드별로: 분산 규칙 · taint · unschedulable, drain 과 장애의 차이 |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`gen_b18.py`).
