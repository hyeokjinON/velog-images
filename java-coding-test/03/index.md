# 자바 코딩테스트 3편 — 문자열 · 구현 그림 목록

모든 그림은 가로 760px(PNG 는 2배인 1520px)이고 글자는 16px 이상이다. 글에는 PNG 를 넣고, SVG 는 원본이다.

| 번호 | 파일 | 글의 절 | 무엇을 보여 주나 |
|---|---|---|---|
| 그림 3-1 | `03-01-string-pool-equality.png` | 2-3. `==` 는 언제 true 인가 | 다섯 식이 pool 의 "ab" 와 힙의 새 객체 중 어느 것을 가리켜 true / false 가 갈리나 |
| 그림 3-2 | `03-02-compact-strings-bytes.png` | 2-5. `length()` 는 글자 수가 아니다 | "abc", "가나다", "a😀" 가 String 안 byte 배열에 몇 바이트로 담기고 length() 와 codePointCount 가 얼마인가, UTF-8 / EUC-KR 바이트 수 |
| 그림 3-3a | `03-03a-concat-copies-all.png` | 3-2. 이유 | 루프 안 `s += 'a'` 가 반복마다 새 String 을 만들며 앞 글자를 복사하는 모습과 10만 번의 복사 누계 4,999,950,000 |
| 그림 3-3b | `03-03b-builder-buffer-growth.png` | 3-2. 이유 | StringBuilder 의 16칸 배열에 이어 쓰기, 10만 번 append 중 배열을 늘린 13번(16 → 34 → … → 147,454)과 복사 147,412 글자 |
| 그림 3-4 | `03-04-run-length-pointers.png` | 5. 패턴 ④ 연속 구간 묶기 | "aaabccdddd" 에서 i 와 j 가 구간마다 어디서 멈추고 sb 가 "3ab2c4d" 가 되기까지 |
| 그림 3-5a | `03-05a-new-id-seven-stages.png` | 6-1. 예제를 손으로 따라가기 — 예제 1 | 신규 아이디 추천 예제 1 이 1 ~ 7단계를 지날 때마다의 문자열과 길이 (27 → 23 → 20 → 19 → 15) |
| 그림 3-5b | `03-05b-new-id-edge-cases.png` | 6-1. 예제를 손으로 따라가기 — 예제 5 | 15자로 자른 뒤 끝에 새로 생긴 점(예제 5)과 빈 문자열이 "aaa" 가 되는 과정(예제 3) |
| 그림 3-6 | `03-06-words-scan-pointer.png` | 6-2. 예제를 손으로 따라가기 — 예제 1 | 풀이 B 가 "one4seveneight" 를 while 4바퀴로 읽으며 i 가 0 → 3 → 4 → 9 → 14, sb 가 "1478" 이 되는 과정 |
| 그림 3-7a | `03-07a-compress-units.png` | 6-3. 예제를 손으로 따라가기 — 예제 3 | "abcabcdede" 를 단위 1 ~ 5 로 자른 조각과 압축 결과, 단위 3 의 8자가 답 |
| 그림 3-7b | `03-07b-compress-unit3-steps.png` | 6-3. 예제를 손으로 따라가기 — 예제 3 | 단위 3 에서 조각마다 prev, count, sb 가 바뀌는 순서와 루프 밖 마지막 묶음 붙이기 |
