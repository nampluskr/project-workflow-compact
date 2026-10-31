> 버전: v0.1 · 작성일: 2026-10-31 · 상태: 확정 (2026-10-31)
>
> Phase 인덱스다. 요구는 `SPEC.md`에, 설계 결정은 `DECISIONS.md`에 있다. 실제로 한 일과 검증 결과는 `PROGRESS.md`에 기록한다.

# PLAN — project-workflow v0.1

## 읽는 법과 이 순서에 걸린 규칙

**`R-n`은 v0.1 `SPEC.md`의 요구 번호, `D-n`은 v0.1 `DECISIONS.md`의 결정 번호다.**

**Phase 순서는 의존 때문이다.** Phase 1의 DOCUMENTS가 문서마다 절 구성을 정의하고, 뒤의 templates·WORKFLOW·v0.1 예시 문서가 그 정의를 따른다. 검증(Phase 4)은 모든 문서가 갖춰진 뒤에 한다.

**각 Phase를 닫기 전에 reviewer가 그 Phase의 완료 조건을 대조한다.** 같은 검토의 왕복은 최대 3회다. (사용자 결정: reviewer 검토 "Phase마다", 검증 왕복 "최대 3회")

**작업을 끝낼 때마다 `PROGRESS.md`에 무엇을·결과·검증을 남긴다(D-5의 규칙).** 그래서 `PROGRESS.md`는 Phase 1 착수 때 만든다. 계획 밖 작업은 PROGRESS의 사용자 요청 작업으로 적는다.

---

## Phase 1 — 문서 기준

**목적** — 문서마다 절 구성과 작성 기준을 정의하고, 그 정의를 따르는 빈 템플릿을 만든다.

**대응** — `R-2` · `R-3` · `D-2` · `D-4` · `D-6` · `D-8` · `D-9`

**완료 조건**
- docs/DOCUMENTS.md 가 있고, 루트 INTENT·버전 INTENT·DECISIONS·SPEC·PLAN·PROGRESS 여섯 문서마다 절이 있다. 각 절에 그 문서가 담는 것과 절 구성이 있다.
- DOCUMENTS에 버전 INTENT가 "목적·범위·기대 결과", "배경", "제외 범위"로 이뤄지고 다른 문서에는 INTENT 절을 두지 않는다는 것이 적혀 있다.
- DOCUMENTS의 작성 기준에 "항목마다 절을 두고 풀어 쓴다. 절 안의 보조 표는 쓸 수 있다"가 있다.
- docs/templates/ 바로 아래에 파일 6개가 있고, 하위 폴더가 없다.
- 템플릿이 여섯 문서(루트 INTENT·버전 INTENT·DECISIONS·SPEC·PLAN·PROGRESS)와 하나씩 대응한다.
- 템플릿의 절 제목이 DOCUMENTS의 정의와 같다.
- 템플릿에 절 제목과 작성 안내 외의 실제 내용이 없다.
- specs/v0.1/PROGRESS.md 가 만들어져 있고 Phase 1 기록이 있다.

---

## Phase 2 — 흐름과 규칙

**목적** — 다섯 단계의 버전 흐름을 안내하고, 에이전트가 지킬 규칙을 둔다.

**대응** — `R-1` · `R-4` · `D-3` · `D-5` · `D-6` · `D-8`

**완료 조건**
- docs/WORKFLOW.md 가 있고, 신규 시작 → 작성 → 진행 → 버전 종료 → 다음 버전 다섯 단계가 각각 절로 있다.
- 단계마다 누가(사람·에이전트) 무엇을 하는지와 어느 문서를 쓰는지가 적혀 있다.
- 새 버전은 specs/{version}/ 새 폴더로 시작하고 지난 버전 폴더는 그대로 둔다는 것이 적혀 있다.
- AGENTS.md·CLAUDE.md를 R-4와 같은 모양으로 두라는 안내가 있다.
- 루트 AGENTS.md 에 규칙 셋(사람이 정하고 묻는다 / 지난 버전 폴더 불변 / PROGRESS 기록)이 있다.
- 루트 CLAUDE.md 의 줄 수가 1이고 내용이 `@AGENTS.md` 이다.

---

## Phase 3 — 예시와 입구

**목적** — 이 레포의 v0.1 문서를 가이드를 따른 첫 작성 예시로 갖추고, 레포의 입구를 만든다.

**대응** — `R-5` · `R-6` · `D-2` · `D-3` · `D-4` · `D-8`

**완료 조건**
- specs/v0.1/ 에 INTENT.md, DECISIONS.md, SPEC.md, PLAN.md, PROGRESS.md 다섯이 있다.
- 다섯 문서의 절 구성이 DOCUMENTS의 정의와 같고, 내용이 DOCUMENTS의 작성 기준(항목마다 절을 두고 풀어 쓴다 등)을 따른다. Phase 1 전에 쓴 INTENT·DECISIONS·SPEC·PLAN 도 DOCUMENTS 에 맞는지 대조한다.
- 루트에 README.md 가 있고, 이 레포가 무엇인지 소개한다.
- README.md 가 docs/WORKFLOW.md·docs/DOCUMENTS.md·docs/templates/ 와 예시 specs/v0.1/ 을 가리키는 링크가 있다.
- README.md 에 어느 문서부터 읽는지를 안내하는 문장이 있다.
- README.md 의 소개가 루트 INTENT와 어긋나지 않는다.

---

## Phase 4 — 검증

**목적** — 문서 전체의 링크·인코딩을 확인하고, 다른 프로젝트가 가이드만 보고 시작할 수 있는지 시도해 본다.

**대응** — `R-7` · `R-8`

**완료 조건**
- refs/ 를 뺀 레포의 Markdown 문서에서 깨진 상대 링크가 0개다.
- 모든 .md 를 UTF-8 엄격 모드로 다시 읽었을 때 오류가 0건이다.
- 한글 텍스트를 읽어 깨진 글자가 없는지 점검했다.
- reviewer 가 README.md 와 docs/ 만 받고 가상 프로젝트의 v0.1 문서 뼈대를 만들어 보고, 막힌 곳을 보고한다.
- 보고된 곳을 고친 뒤 reviewer 가 다시 시도한다.
- 재시도에서 막힌 곳이 없으면 충족이다. 재시도 뒤에도 남은 문제가 있으면, 그 문제가 시작을 막는지는 사용자가 판단한다.
