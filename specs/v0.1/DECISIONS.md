> 버전: v0.1 · 작성일: 2026-10-31 · 상태: 확정 (2026-10-31)
>
> 이번 버전에 적용할 설계 결정을 기록한다. 변하지 않는 의도는 루트 `INTENT.md`에, 이번 버전에 무엇을 왜 하는지는 `specs/v0.1/INTENT.md`에 있다.

# DECISIONS — project-workflow v0.1

## D-1. 빈 폴더에 새로 쓰고, 원본은 refs/에 참고용으로 둔다

**선택**

D:\projects\project-workflow-compact 에 처음부터 새로 쓴다. 원본 nampluskr/project-workflow(v0.2)는 refs/project-workflow-v0.2/ 에 클론해 두고 읽기만 한다. GitHub 저장소 연결은 나중에 정한다.

**근거**

사용자가 골랐다(2026-10-31). 사용자 지시는 "좀더 실용적이고 간편한 버젼으로 다시 작성하고 싶습니다"이다. 원본을 refs/에 읽기 전용으로 두는 것은 버전 INTENT 제외 범위 "원본은 수정하지 않는다"와 맞는다.

**배제한 대안**

- **원본 클론 위에서 개정** — git 이력이 이어지는 안이었지만 사용자가 새로 작성을 골랐다. 배제.

**이후 변경** — v0.1 작업을 마친 뒤 사용자 요청으로 refs/ 를 삭제했다(2026-10-31). 원본은 GitHub `nampluskr/project-workflow`에 있다.

---

## D-2. 문서는 INTENT·DECISIONS·SPEC·PLAN·PROGRESS 다섯이다. BRIEF와 backlog는 두지 않는다

**선택**

다섯 문서의 역할은 다음과 같다.

- **INTENT** — 무엇을 왜 하는가. 루트는 프로젝트 전체, 버전 INTENT는 D-4
- **DECISIONS** — 선택과 근거와 배제한 대안
- **SPEC** — 이번 버전이 만족해야 할 요구와 판정 방법
- **PLAN** — Phase와 완료 조건
- **PROGRESS** — 실제로 한 일과 사용자 요청 작업의 기록

원본 BRIEF가 담던 배경과 하지 않을 것은 버전 INTENT의 "배경"·"제외 범위"가 담는다. 원본 backlog.json이 하던 task 분해는 두지 않고 PLAN의 Phase로 진행한다.

**근거**

사용자가 골랐다(2026-10-31, "INTENT - DECISIONS - SPEC - PLAN - PROGRESS / BRIEF, backlog 제외"). 사용자는 원본이 "지나치게 절차가 복잡"하다고 판단했다. 원본 v0.2는 문서 7종을 두었다. 이전에 검토한 compact 버전도 INTENT → DECISIONS → SPEC → PLAN으로 줄였고, PROGRESS는 사용자 요청으로 따로 더했다(compact DECISIONS D-2·D-9).

backlog는 원본에서 backlog CLI 설치를 전제로 했고, hook으로 직접 편집을 막았다. 원본 검토에서 그 hook이 새 버전 착수 때 backlog.json의 이동·삭제까지 막는 문제가 나왔다.

**배제한 대안**

- **원본 7종(BRIEF·backlog 포함) 유지** — 사용자가 절차가 복잡하다고 판단했다. 배제.

---

## D-3. 루트 INTENT.md와 specs/{version}/ 폴더에 저장하고, 복사 단계를 두지 않는다

**선택**

프로젝트 전체의 INTENT.md는 루트에 하나 둔다. 버전 문서는 specs/v0.1/, specs/v0.2/ … 처럼 버전마다 폴더를 두고 그 안에서 바로 쓴다. 새 버전은 새 폴더로 시작하고, 지난 버전 폴더는 그대로 둔다.

**근거**

사용자가 compact 구조를 골랐다(2026-10-31, 선택지 "버전마다 폴더를 두고 거기서 바로 쓴다. 복사하는 단계가 없다"). compact의 근거는 "버전별 설계와 실행 기록을 한곳에서 관리"였다(compact DECISIONS D-3). 지난 버전 폴더를 건드리지 않으므로 루트 INTENT의 원칙 "지난 버전은 지워지지 않는다"를 따른다.

원본은 docs/current/에서 작업하고 마감 때 docs/history/vX.Y/로 복사하면서 INTENT.md만 빼야 했고, history가 바뀌지 않게 hook으로 막았다.

**배제한 대안**

- **docs/current/ + docs/history/ 복사(원본 방식)** — 사용자가 compact 구조를 골랐다. 배제.

---

## D-4. 버전 의도는 specs/{version}/INTENT.md 한 파일에만 둔다

**선택**

버전마다 INTENT.md를 두고 "목적·범위·기대 결과", "배경", "제외 범위"를 적는다. DECISIONS·SPEC·PLAN·PROGRESS의 첫 항목에는 INTENT 절을 두지 않는다. 루트 INTENT는 버전과 무관한 의도를, 버전 INTENT는 이번 버전의 의도를 담는다.

**근거**

사용자가 골랐다(2026-10-31, "버전 INTENT 파일만").

**배제한 대안**

- **compact 방식(버전 INTENT 파일 + 각 문서 첫 항목의 INTENT)** — 사용자가 버전 INTENT 파일만 골랐다. 배제.
- **루트 INTENT 하나만 두고 버전 목적은 SPEC이나 PLAN 머리에 적기** — 같은 이유로 배제.

---

## D-5. hook을 두지 않는다. 규칙은 AGENTS.md에 두고, CLAUDE.md에는 @AGENTS.md 한 줄만 둔다

**선택**

원본의 hook(guard.mjs·progress-check.mjs), .claude/rules/, reviewer agent, settings.json 등록, 차단 증명 절차를 두지 않는다. 에이전트가 지킬 규칙은 AGENTS.md에 둔다. CLAUDE.md에는 `@AGENTS.md` 한 줄만 적는다. AGENTS.md에 둘 규칙은 셋이다.

- **사람이 정하고 묻는다** — 문서의 요구·결정은 사람이 정한다. 모르면 지어내지 말고 묻는다.
- **지난 버전 폴더 불변** — specs/ 아래 지난 버전 폴더는 읽기만 하고 고치지 않는다.
- **PROGRESS 기록** — 작업을 끝낼 때마다 PROGRESS에 무엇을·결과·검증을 남기고, 계획 밖 작업은 사용자 요청 작업으로 적는다.

**근거**

사용자가 hook 없이 규칙 문서만 두기로 골랐고(2026-10-31, "hook 없이 CLAUDE.md만"), 미결 사항을 정할 때 규칙을 둘 자리를 "CLAUDE.md 에서 @AGENTS.md 1줄만 기록"으로 정했다(2026-10-31). 규칙 셋도 사용자가 골랐다. 사용자는 원본의 "하네스가 타이트하게 잡혀 있다"고 판단했다. 루트 INTENT의 다루지 않는 것 "필수 하네스·강제 장치. 규칙은 문서로 충분하다"와 원칙 "간편함이 우선이다"에 맞는다.

원본 검토에서 hook의 문제가 실제로 나왔다. 새 버전 착수 때 backlog.json 이동·삭제를 막았고, PowerShell 도구는 검사 대상에서 빠졌으며, Stop hook은 "막히면 멈추고 묻는다"는 규칙과 부딪혔다.

**배제한 대안**

- **docs/history 보호 hook 하나만 남기기** — 사용자가 hook 없음을 골랐다. 배제.
- **hook 템플릿을 선택 부록으로 두기** — 같은 이유로 배제.
- **규칙을 CLAUDE.md에 직접 적기** — 처음 답("hook 없이 CLAUDE.md만")의 형태였지만, 사용자가 CLAUDE.md는 @AGENTS.md 한 줄로 정했다. 배제.
- **"INTENT와 어긋나면 멈추고 보고한다" 규칙** — 후보였지만 사용자가 고르지 않았다. 배제.

---

## D-6. 다른 프로젝트가 참고할 가이드는 WORKFLOW·DOCUMENTS·templates 셋이다

**선택**

WORKFLOW는 신규 시작 → 작성 → 진행 → 버전 종료 → 다음 버전의 흐름을, DOCUMENTS는 문서별 항목과 작성 기준을, templates는 문서의 본보기를 담는다.

**근거**

사용자가 골랐다(2026-10-31). 루트 INTENT "다른 프로젝트가 참고하는 문서 가이드다"를 이 세 문서가 맡는다.

**배제한 대안**

- **MULTI-AGENT 문서 포함(compact 방식)** — 사용자가 고르지 않았다. 루트 INTENT가 "에이전트 도구 간 연결"을 다루지 않고, 버전 INTENT가 멀티에이전트 가이드를 이번 제외 범위로 정했다. 배제.

---

## D-7. 버전 번호는 v0.1에서 시작한다

**선택**

이번 개정을 v0.1로 한다. 원본 v0.2와 번호를 잇지 않는다.

**근거**

사용자가 골랐다(2026-10-31, 선택지 "새 프로젝트로 보고 v0.1부터 시작한다(compact와 같음)").

**배제한 대안**

- **v0.3** — 원본 v0.2의 다음 버전으로 잇는 안. 사용자가 v0.1을 골랐다. 배제.

---

## D-8. 가이드 문서는 docs/ 아래에 모두 둔다

**선택**

docs/WORKFLOW.md, docs/DOCUMENTS.md, docs/templates/. 루트에는 INTENT.md와 README.md를 둔다.

**근거**

사용자가 골랐다(2026-10-31, "docs/ 아래 모두"). compact도 DOCUMENTS·MULTI-AGENT를 docs/에 두었다.

**배제한 대안**

- **WORKFLOW.md는 루트, 나머지는 docs/** (원본 v0.2 배치) — 사용자가 docs/ 아래 모두를 골랐다. 배제.
- **guide/ 폴더에 따로 묶기** — 같은 이유로 배제.

---

## D-9. templates는 문서별 빈 템플릿으로 둔다

**선택**

루트 INTENT, 버전 INTENT, DECISIONS, SPEC, PLAN, PROGRESS의 빈 양식을 docs/templates/에 하위 폴더 없이 평면으로 둔다.

**근거**

사용자가 골랐다(2026-10-31, "문서별 빈 템플릿", compact 방식).

**배제한 대안**

- **빈 양식 없이 이 레포의 specs/v0.1/을 예시로만 가리키기** — 원본 v0.2는 빈 양식을 두지 않았다. 사용자가 빈 템플릿을 골랐다. 배제.
- **빈 템플릿에 CLAUDE.md 템플릿까지 두기** — 사용자가 고르지 않았다. 배제.

---

## 미결 사항

없음.
