# HERDR-SETUP — workflow 멀티 에이전트 구성안

- 상태: 승인됨 (2026-10-31, plan 승인)
- 작성: wf-leader (2026-10-31)
- 가이드: D:\projects\docs\guides\herdr\README.md

## 1. 근거

- INTENT.md: "INTENT.md 없음" — 이번 작업이 INTENT.md 를 만드는 것이다
- 사용자 지시: "이 프로젝트 워크플로우는 지나치게 절차가 복잡하고, 하네스가 타이트하게 잡혀 있습니다. 이를 좀더 실용적이고 간편한 버젼으로 다시 작성하고 싶습니다." / "herdr 환경 구축을 하고, INTENT.md 파일만 작성해야 합니다." / "이후 leader 에이젼트가 사용자와 대화를 통해 다른 문서와 폴더등을 생성합니다."
- 사용자에게 확인한 것:
  - 작성 위치 → "빈 폴더에 새로 작성" (원본은 refs/project-workflow-v0.2 에 참고용으로 둠)
  - 하네스 → "hook 없이 CLAUDE.md만"
  - 문서 세트 → "INTENT - DECISIONS - SPEC - PLAN - PROGRESS / BRIEF, backlog 제외"
  - 에이전트 → "leader + writer + reviewer"

## 2. 작업 유형

- 바탕 구성: 가이드 PLANNING.md 6.2 A. 문서·가이드
- 페어: Claude 주력
- 바꾼 점: checker 없음 — INTENT.md 는 명령·사실 확인 대상이 없음. reviewer 를 둠 (사용자 선택)

## 3. 탭·패널 배치

| 탭 | 이름 | 패널 |
| --- | --- | --- |
| 1 | control | wf-leader |
| 2 | agents | wf-writer (왼쪽), wf-reviewer (오른쪽) |
| 3 | run | 없음 |

```
탭 2 agents
┌──────────────────────┬──────────────────────┐
│ wf-writer            │ wf-reviewer          │
└──────────────────────┴──────────────────────┘
```

## 4. 에이전트

| 이름 | kind | 모델 · effort | 위치 | 역할 | 파일 수정 범위 |
| --- | --- | --- | --- | --- | --- |
| wf-leader | claude | Opus 5.5 · medium | 1 control | 소통·조율, 사용자 질문 진행 | docs/HERDR-SETUP.md, docs/HERDR-DECISIONS.md |
| wf-writer | claude | Sonnet 5.5 · high | 2 agents 왼쪽 | 문서 초안 작성·수정 | INTENT.md, specs/, docs/WORKFLOW.md, docs/DOCUMENTS.md, docs/templates/, AGENTS.md, CLAUDE.md, README.md |
| wf-reviewer | codex | gpt-6.1-sol · high | 2 agents 오른쪽 | 문서별 적대적 리뷰 | 안 함 |

## 5. runner

없음

## 6. 토큰 부담

| 구독 | 이 워크스페이스 | 동시에 도는 다른 워크스페이스 |
| --- | --- | --- |
| Claude | ◐ leader, ● writer | projects(w8): leader 1개, idle |
| Codex | ◐ reviewer 1~2회 | 없음 |
| agy | 없음 | 없음 |

## 7. 대리 응답 범위

- 가이드 OPERATING.md 1절 기준을 따른다
- 이 프로젝트에서 따로 정한 것:
  - (2026-10-31 사용자 위임) leader 가 사용자 승인 권한을 가진다. 하위 에이전트의 결정 요청을 검토해 승인·수정 요청하고, 판단마다 근거를 HERDR-DECISIONS.md 에 남긴다. 이전 규칙 "INTENT 내용은 사용자에게 올린다"를 대체한다
  - 위임 밖: push 등 외부 전송, 파일·폴더 삭제 등 되돌리기 어려운 작업은 하지 않는다
  - git init · push 는 하지 않는다
  - 같은 에이전트와의 검증 왕복은 최대 3회 (사용자 지시, 가이드 PLANNING 4절의 2회 대신)

## 8. 정리 방법

- 닫을 탭·패널: 탭 2 agents — 단, 이후 문서 작업에 쓰므로 사용자가 닫으라고 할 때까지 유지
- 지울 worktree: 없음
- 남길 것: 탭 1 control (wf-leader)

## 9. 변경 이력

| 날짜 | 내용 | 승인 |
| --- | --- | --- |
| 2026-10-31 | 초안 작성, plan 승인으로 승인 | 사용자 승인 |
| 2026-10-31 | writer 수정 범위에 specs/ 추가, reviewer 문서별 리뷰 (사용자 지시 "이와 유사하게 문서들을 작성") | 사용자 지시 |
| 2026-10-31 | 검증 왕복 최대 3회로 변경 (사용자 지시) | 사용자 지시 |
| 2026-10-31 | leader 에게 사용자 승인 권한 위임, writer 수정 범위를 PLAN 산출물로 확대, PLAN Phase 1~4 일괄 진행 (사용자 지시) | 사용자 지시 |
