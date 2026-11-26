# bank-transfer #2 그림 목록

글: 은행 연동 송금 서비스 #2 — Docker Compose 로 MySQL · Kafka(KRaft) · Redis 로컬 인프라 만들기 (P3-0)

모든 그림은 가로 760px(PNG 는 2배, 1520px)이고 글자는 16px 이상이다. 글에서는 PNG 를 쓴다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 2-1 | `02-01-overview.png` | 이 글을 한 장으로 | Git Bash 세 줄 → Compose 가 컨테이너 3개 + 볼륨 3개를 띄움 → verify.sh 로 쓰기 · 읽기 → CI 가 같은 파일로 반복 |
| 2-2 | `02-02-kraft-vs-zookeeper.png` | 3. Kafka 4.1 — ZooKeeper 가 없다 | 예전 Kafka 3대 + ZooKeeper 3대와, 노드 1개가 broker · controller 를 함께 맡는 KRaft 로컬 구성 |
| 2-3a | `02-03a-kafka-listeners-two.png` | 3-1. 리스너를 둘로 나눈 이유 | PC 앱은 EXTERNAL(localhost:9092), kafka-ui 는 INTERNAL(kafka:29092)로 처음 접속 → 안내 → 다시 접속 |
| 2-3b | `02-03b-kafka-listener-one-fails.png` | 3-1. 리스너를 둘로 나눈 이유 | advertised 가 kafka:29092 하나면 처음 접속은 되고 보내기는 시간 초과 |
| 2-4 | `02-04-volume-lifecycle.png` | 3-4. 데이터 경로는 /tmp 가 아니게 | up → down → up → down -v → up 마다 볼륨과 infra_check 행의 상태 |
| 2-5 | `02-05-ready-three-stages.png` | 4. "떴다" ≠ "쓸 수 있다" | 컨테이너 시작 · healthcheck + --wait · verify.sh 세 단계가 확인하는 것과 못 잡는 것, MySQL healthcheck 숫자 |
| 2-6 | `02-06-ci-infra-smoke.png` | 5. CI 에서도 같은 파일로 | infra-smoke 잡 checkout → Start → Verify → 실패 시 로그 / 항상 down -v |
| 2-7a | `02-07a-two-bash.png` | 5-2. bash 가 두 개다 | PowerShell 의 bash(WSL 실행기)는 docker-desktop 배포판에 /bin/bash 가 없어 실패, Git Bash 는 통과 |
| 2-7b | `02-07b-msys-path-conversion.png` | 5-2. bash 가 두 개다 (원인 2) | Git Bash 가 /opt/... 를 C:/Program Files/Git/opt/... 로 바꿔 127, MSYS_NO_PATHCONV=1 로 해결 |

같은 이름의 `.svg` 가 원본이다. 그림 생성 스크립트는 작업용 임시 폴더에 있다 (`b02/figs_b02.py`, 도우미 `b02/gen_b02.py`).
