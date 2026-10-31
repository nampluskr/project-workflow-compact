> 버전: v0.1 · 작성일: 2026-10-31 · 상태: 진행 중
>
> 실제로 한 일과 검증 결과를 기록한다. 계획은 `PLAN.md`에, 요구는 `SPEC.md`에, 설계 결정은 `DECISIONS.md`에 있다.

# PROGRESS — project-workflow v0.1

## Phase별 진행

### Phase 1 — 문서 기준

상태: 완료

- **DOCUMENTS 작성** (2026-10-31)
  - 무엇을 했나: docs/DOCUMENTS.md 를 썼다. 공통 작성 기준, 문서 관계, 여섯 문서(루트 INTENT·버전 INTENT·DECISIONS·SPEC·PLAN·PROGRESS)별 절을 두었다. 문서마다 담는 것·절 구성·작성 기준·담지 않는 것과 템플릿 링크를 적었고, 마지막 절에서 specs/v0.1/ 을 예시로 가리킨다.
  - 결과: 버전 INTENT 가 "목적·범위·기대 결과", "배경", "제외 범위"로 이뤄지고 다른 문서에는 INTENT 절을 두지 않는다는 것이 적혀 있다. 공통 작성 기준에 "항목마다 절을 두고 풀어 쓴다"와 "절 안의 보조 표는 쓸 수 있다"가 있다.
  - 검증: 여섯 문서의 절과 위 두 문장을 읽어 확인했다. 파일 안의 상대 링크 10개 중 9개가 실제 파일·폴더를 가리킨다.
  - 특이사항: docs/WORKFLOW.md 링크는 Phase 2 에서 파일이 생길 때까지 깨져 있다.

- **템플릿 6개 작성** (2026-10-31)
  - 무엇을 했나: docs/templates/ 에 PROJECT-INTENT.md, INTENT.md, DECISIONS.md, SPEC.md, PLAN.md, PROGRESS.md 를 하위 폴더 없이 두었다. 절 제목은 DOCUMENTS 정의와 같고, 본문은 `<...>` 자리표시와 짧은 작성 안내만 둔다.
  - 결과: 여섯 문서와 템플릿이 하나씩 대응한다.
  - 검증: 파일 6개, 하위 폴더 0개를 확인했다. 템플릿마다 절 제목을 뽑아 DOCUMENTS 의 절 구성과 대조해 같음을 확인했다. 본문에 실제 내용이 없음을 읽어 확인했다. docs/·specs/·루트 INTENT.md 의 .md 14개를 UTF-8 엄격 모드로 다시 읽어 오류 0건, 깨진 글자(U+FFFD)와 이모지 0건을 확인했다.
  - 특이사항: 없음.

- **PROGRESS 생성** (2026-10-31)
  - 무엇을 했나: specs/v0.1/PROGRESS.md 를 만들고 Phase 1 기록을 남겼다.
  - 결과: 이 문서가 있다.
  - 검증: 구성이 docs/templates/PROGRESS.md 와 같음을 읽어 확인했다.
  - 특이사항: reviewer 의 Phase 1 완료 조건 대조는 아직 받지 않았다. 이미 쓴 specs/v0.1/INTENT.md 는 맨 위 인용 블록이 없고 제목이 `# INTENT — v0.1` 이라 DOCUMENTS 의 정의와 다르다. PLAN 에 따라 Phase 3 에서 대조해 고친다.

- **reviewer 대조** (2026-10-31)
  - 무엇을 했나: reviewer 가 Phase 1 완료 조건을 대조했다(1회).
  - 결과: 지적 1건(DOCUMENTS 루트 INTENT 작성 기준의 출처)은 leader 가 유지로 승인했다(HERDR-DECISIONS D-010). 버전 INTENT 인용 블록·제목은 Phase 3 으로 넘겼다.
  - 검증: reviewer 의 대조 1회.
  - 특이사항: 없음.

### Phase 2 — 흐름과 규칙

상태: 완료

- **WORKFLOW 작성** (2026-10-31)
  - 무엇을 했나: docs/WORKFLOW.md 를 썼다. 신규 시작·작성·진행·버전 종료·다음 버전 다섯 단계를 절로 두고, 단계마다 사람·에이전트·쓰는 문서를 적었다. 새 버전은 `specs/{새 버전}/` 새 폴더로 시작하고 지난 버전 폴더는 읽기만 한다는 것, AGENTS.md 규칙 셋과 CLAUDE.md `@AGENTS.md` 한 줄 안내, 강제 장치를 두지 않는다는 한 문장을 넣었다.
  - 결과: 다섯 단계 절마다 주체와 문서가 적혀 있다. 작성 순서는 버전 INTENT → DECISIONS → SPEC → PLAN 이다. 버전 종료에 태그·배포는 정하지 않는다고 적었다.
  - 검증: 다섯 단계 절의 존재와 단계마다 주체·문서를 읽어 확인했다. 파일 안의 상대 링크 9개(앵커 2개 포함)가 모두 실제 파일·절을 가리킨다. UTF-8 엄격 모드로 다시 읽어 오류 0건, 깨진 글자 0건을 확인했다. 이로써 Phase 1 에서 깨져 있던 DOCUMENTS 의 WORKFLOW.md 링크도 풀렸다.
  - 특이사항: 없음.

- **AGENTS.md·CLAUDE.md 작성** (2026-10-31)
  - 무엇을 했나: 루트 AGENTS.md 에 D-5 의 규칙 셋(사람이 정하고 묻는다 / 지난 버전 폴더 불변 / PROGRESS 기록)을 D-5 의 문장 그대로 적었다. 루트 CLAUDE.md 에는 `@AGENTS.md` 한 줄만 적었다.
  - 결과: AGENTS.md 에 규칙 셋이 있다. CLAUDE.md 는 한 줄이다.
  - 검증: AGENTS.md 에서 세 규칙을 찾았다. CLAUDE.md 의 줄 수가 1이고 내용이 `@AGENTS.md` 임을 확인했다. 두 파일을 UTF-8 엄격 모드로 다시 읽어 오류 0건을 확인했다.
  - 특이사항: 없음.

- **PROGRESS 갱신** (2026-10-31)
  - 무엇을 했나: 이 Phase 2 절과 작업 기록을 더했다.
  - 결과: Phase 2 기록이 있다.
  - 검증: 구성이 docs/templates/PROGRESS.md 와 같음을 읽어 확인했다.
  - 특이사항: reviewer 의 Phase 2 완료 조건 대조는 아직 받지 않았다.

- **reviewer 대조** (2026-10-31)
  - 무엇을 했나: reviewer 가 Phase 2 완료 조건을 대조했다(1회).
  - 결과: 고칠 것 없음.
  - 검증: reviewer 의 대조 1회(HERDR-DECISIONS D-013).
  - 특이사항: 없음.

### Phase 3 — 예시와 입구

상태: 완료

- **v0.1 문서 형식 대조** (2026-10-31)
  - 무엇을 했나: specs/v0.1/ 의 INTENT·DECISIONS·SPEC·PLAN 을 docs/DOCUMENTS.md 의 정의와 대조했다. 어긋난 INTENT.md 에 맨 위 인용 블록을 더하고 제목을 `# INTENT — project-workflow v0.1` 로 고쳤다. 네 문서 인용 블록의 상태를 "확정 (2026-10-31)" 로 바꿨다(HERDR-DECISIONS D-013). 결정·요구·Phase 의 내용은 바꾸지 않았다.
  - 결과: 다섯 문서 모두 맨 위 인용 블록이 있고, 제목이 `<문서명> — project-workflow v0.1` 형태이며, INTENT 절을 따로 둔 문서가 없다.
  - 검증: 문서마다 절 제목을 DOCUMENTS 의 절 구성과 대조했다. DECISIONS 의 결정 절과 미결 사항, SPEC 의 요구 절, PLAN 의 읽는 법과 Phase 절, PROGRESS 의 세 절이 정의와 같다. 내용이 DOCUMENTS 의 작성 기준(항목마다 절을 두고 풀어 쓴다 등)을 따르는지 읽어 확인했다. 다섯 문서를 UTF-8 엄격 모드로 다시 읽어 오류 0건을 확인했다.
  - 특이사항: 없음.

- **README 작성** (2026-10-31)
  - 무엇을 했나: 루트 README.md 를 썼다. 이 레포가 무엇인지를 루트 INTENT 의 문장으로 소개하고 INTENT.md 를 링크했다. README → docs/WORKFLOW.md → docs/DOCUMENTS.md → docs/templates/ 순서의 읽기 시작점을 문장으로 적었다. 예시 specs/v0.1/ 링크, 새 프로젝트는 WORKFLOW 의 "1. 신규 시작"부터라는 안내, docs/HERDR-*.md 는 운영 기록이며 가이드가 아니라는 문장(D-013), refs/ 는 원본 참고용이라는 문장을 넣었다.
  - 결과: README.md 가 있고 네 경로(docs/WORKFLOW.md·docs/DOCUMENTS.md·docs/templates/·specs/v0.1/)를 가리킨다.
  - 검증: README.md 의 상대 링크 9개가 모두 실제 파일·폴더를 가리킨다. 소개 문단을 루트 INTENT 와 대조해 어긋나지 않음을 확인했다. UTF-8 엄격 모드로 다시 읽어 오류 0건, 이모지 0건을 확인했다.
  - 특이사항: 없음.

- **PROGRESS 갱신** (2026-10-31)
  - 무엇을 했나: 이 Phase 3 절과 작업 기록을 더하고, Phase 2 의 reviewer 대조 결과와 완료 상태를 적었다.
  - 결과: Phase 2 상태가 완료로, Phase 3 기록이 있다.
  - 검증: 구성이 docs/templates/PROGRESS.md 와 같음을 읽어 확인했다.
  - 특이사항: reviewer 의 Phase 3 완료 조건 대조는 아직 받지 않았다.

- **reviewer 대조** (2026-10-31)
  - 무엇을 했나: reviewer 가 Phase 3 완료 조건을 대조했다(1회차).
  - 결과: PROGRESS 두 곳(남은 것 상태, 덮어쓴 지난 기록)을 지적했고 이번에 고쳤다(HERDR-DECISIONS D-015).
  - 검증: 2회차 대조 대기.
  - 특이사항: 2회차 대조 결과는 leader 가 확인 후 알려 준다.

- **reviewer 2회차 대조** (2026-10-31)
  - 무엇을 했나: 1회차 지적 2건 해소 확인.
  - 결과: 해소, 고칠 것 없음.
  - 검증: reviewer 2회차 대조.
  - 특이사항: 없음.

### Phase 4 — 검증

상태: 완료

- **링크·인코딩 검사** (2026-10-31)
  - 무엇을 했나: leader 가 refs/ 를 뺀 Markdown 19개를 검사했다.
  - 결과: 상대 링크 29개 중 깨진 것 0개, UTF-8 엄격 재읽기 오류 0건, U+FFFD 0건, 이모지 0건, 모지바케 패턴 0건.
  - 검증: leader 의 검사(HERDR-DECISIONS D-016).
  - 특이사항: 없음.

- **reviewer 가이드 시도** (2026-10-31)
  - 무엇을 했나: reviewer 가 README.md 와 docs/WORKFLOW.md·docs/DOCUMENTS.md·docs/templates/ 만으로 가상 프로젝트('폴더의 마크다운 파일 목록 CLI')의 v0.1 시작 뼈대를 만들어 봤다.
  - 결과: 막힌 곳 0건이라 재시도는 하지 않았다.
  - 검증: reviewer 의 시도(HERDR-DECISIONS D-017).
  - 특이사항: 뼈대는 파일이 아니라 답변 텍스트로 만들었다(D-016).

- **reviewer 대조** (2026-10-31)
  - 무엇을 했나: reviewer 가 Phase 4 완료 조건을 대조했다(1회).
  - 결과: 고칠 것 없음.
  - 검증: reviewer 대조.
  - 특이사항: 없음.

## 사용자 요청 작업

### refs/ 삭제 (2026-10-31)

- 요청: "이전 ref 에 project-workflow 는 더이상 필요가 없는 것 같습니다. 삭제해도 되나요?" / "네, 삭제하고 문서 정리해 주세요"
- 조치: leader 가 refs/project-workflow-v0.2(로컬 변경 없는 원본 클론, 커밋 8533a4e)를 삭제했다. README 의 refs/ 안내를 GitHub 원본 주소로 바꾸고, DECISIONS D-1 에 이후 변경을 덧붙였다. 작업 당시의 기록(INTENT·SPEC·PLAN·PROGRESS 의 "refs/ 제외" 등)은 지난 기록이라 그대로 두었다.
- 결과: refs/ 가 없다.
- 검증: 링크 검사: Markdown 19개, 상대 링크 29개 중 깨짐 0, UTF-8 오류 0. 가이드 문서(README·AGENTS·CLAUDE·docs/WORKFLOW·DOCUMENTS·templates)에 refs/ 언급 0건.
- 상태: 완료

## 버전 종료

- 사용자 종료 판단: 대기.
- 남은 것: 사용자의 결과 검토와 종료 판단.
