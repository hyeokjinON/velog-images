# bank-transfer #19 그림 목록

글: 은행 연동 송금 서비스 #19 — 지표로 보고 필요할 때만 울린다: 알림 49초 · 점검 중 거짓 알림 0 (P9a)

그린 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 화면 캡처(19-3 · 19-6 · 19-8 · 19-9)는 2026-11-18 kind 에서 찍은 Prometheus · Grafana 화면이며, Pod IP 는 가리고 필요한 부분만 잘랐다 (SVG 원본 없음). 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 19-1 | `19-01-overview.png` | 이 글을 한 장으로 | 앱 → Prometheus(5초 pull, 규칙 11) → Alertmanager → alert-sink, Grafana 는 질의만, 입구는 지표 404 |
| 19-2 | `19-02-event-vs-state.png` | 1. 무엇을 셌나 | 카운터 차이 −420 (버린 방법) vs 사건 카운터 · 상태 DB 게이지 (고른 방법) |
| 19-3 | `19-03-prom-targets.png` | 2. 어떻게 모았나 | 캡처: Target health, bank-transfer 4/4 UP (게이트웨이 리더 · 대기가 따로 보인다) |
| 19-4 | `19-04-alert-timeline.png` | 3-1. 알림이 오기까지 50초 | 수집 5 + 평가 5 + for 30 + 묶기 10 = 50초, 실측 49초 |
| 19-5 | `19-05-inhibit.png` | 3-2. 거짓 알림을 줄인 장치 세 가지 | 게이트웨이 0대: 두 알림 다 firing, Alertmanager 가 BankDisconnected 억제 |
| 19-6 | `19-06-prom-alerts-outage.png` | 3-2. 거짓 알림을 줄인 장치 세 가지 | 캡처: 은행 끊김 2분 뒤 Alerts, FIRING 1 · INACTIVE 10 |
| 19-7a | `19-07a-nc-sink-loss.png` | 4. 알림 절반이 조용히 사라졌다 | nc 반복 수신기: sleep 1 이 루프 시작 때 흘러 1초 뒤 온 알림은 200 만 받고 유실 |
| 19-7b | `19-07b-httpd-cgi-sink.png` | 4. 알림 절반이 조용히 사라졌다 | httpd + CGI: 본문을 다 읽고 로그에 쓴 뒤 200 |
| 19-8 | `19-08-flow-latency-p99.png` | 5. 숫자가 거짓말하는 방식 (②) | 캡처: 접수 → 확정 p99 가 30분 가까이로 보이는 패널 (실제 최대 8분 남짓) |
| 19-9 | `19-09-flow-accept-complete.png` | 6. 대시보드는 질문부터 | 캡처: 접수선 평평, 완료선 0 → 복구 때 솟음 → 재발행 때 한 번 더 |

같은 이름의 `.svg` 가 그린 그림의 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`gen_b19.py`, 캡처 자르기 `crop_b19.py`).
