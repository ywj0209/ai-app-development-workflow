# AI App Development Workflow — Common Documentation Rules

**File:** `DOCUMENTATION_RULES.md`  
**Status:** Active  
**Applies to:** `WORKFLOW.md`, `templates/`, `prompts/`, Project Repository의 주요 Markdown 문서

---

## 1. Purpose

이 문서는 AI App Development Workflow에서 작성되는 모든 주요 Markdown 문서의 공통 작성 규칙을 정의한다.

목표는 다음과 같다.

- 각 문서의 책임을 명확히 한다.
- 같은 결정을 여러 문서에 중복 작성하지 않는다.
- AI가 필요한 문서만 읽고 정확하게 작업할 수 있게 한다.
- 문서가 불필요하게 비대해지는 것을 방지한다.
- Workflow, Template, Prompt, Project 문서의 역할이 섞이지 않게 한다.

> **무엇을 개발할지는 Project 문서가, 어떻게 개발할지는 `WORKFLOW.md`가, 문서를 어떻게 작성할지는 이 문서가 관리한다.**

규칙 수준은 다음과 같이 사용한다.

- **MUST:** 반드시 지킨다.
- **SHOULD:** 특별한 이유가 없다면 지킨다.
- **MAY:** 프로젝트 특성에 따라 선택한다.

---

# 2. Core Rules

## 2.1 One Document, One Primary Responsibility — MUST

각 문서는 하나의 Primary Responsibility만 가진다.

```text
WORKFLOW.md                  → 개발 방법과 단계
MVP_BASELINE.md              → MVP 범위
ARCHITECTURE_BASELINE.md     → 시스템 구조와 경계
DATA_MODEL_BASELINE.md       → 핵심 데이터 의미와 관계
IMPLEMENTATION_BACKLOG.md    → 구현 순서와 상태
Feature Spec                 → 특정 Feature의 제품 동작
CLAUDE.md                    → Claude Code 행동 규칙
```

새 내용을 추가하기 전 확인한다.

> **이 내용이 정말 이 문서가 책임져야 할 결정인가?**

---

## 2.2 One Decision, One Owner — MUST

하나의 결정은 하나의 Owner 문서에서만 정의한다.

다른 문서에서 같은 결정이 필요하면 내용을 복사하지 않고 Owner 문서를 참조한다.

중복 작성은 문서 간 충돌의 주요 원인으로 본다.

---

## 2.3 Responsibility Beats Global Precedence — MUST

모든 문서에 적용되는 단순한 전역 우선순위를 만들지 않는다.

충돌이 발생하면 해당 결정의 Owner를 기준으로 판단한다.

항상 적용되는 경계:

- Feature Spec은 Baseline을 재정의할 수 없다.
- Prompt는 Workflow, Template, Project Owner 문서를 덮어쓸 수 없다.
- Example은 Source of Truth가 아니다.
- Template은 실제 Project 문서보다 우선하지 않는다.

---

## 2.4 Repository Is the Source of Truth — MUST

AI 대화나 기억을 확정된 사실의 Source of Truth로 사용하지 않는다.

```text
AI와 논의
↓
결정
↓
Owner Markdown 문서에 반영
↓
Git Repository에 저장
↓
구현
```

문서에 반영되지 않은 대화 내용은 확정된 프로젝트 결정으로 간주하지 않는다.

---

## 2.5 Write Only What Is Needed — MUST

현재 문서의 목적과 가까운 구현 단계에 필요하지 않은 내용을 미리 작성하지 않는다.

피해야 할 것:

- 아직 필요하지 않은 미래 기능
- 확인되지 않은 확장 요구사항
- 과도하게 상상한 예외 상황
- 구현 전에 정할 필요가 없는 함수명·변수명·파일명
- 미래를 위한 불필요한 추상화
- 다른 Owner 문서의 내용 반복

판단 기준:

> **이 내용이 지금 결정되지 않으면 현재 또는 가까운 다음 단계가 막히는가?**

아니라면 생략하거나 `TBD`로 둘 수 있다.

---

## 2.6 Global vs Local Decision — MUST

**Global Decision**
- 여러 Feature에 영향을 주거나 변경 비용이 큰 결정
- MVP 범위, 핵심 Entity, 주요 State/Lifecycle, Architecture, 주요 권한 정책 등
- 적절한 Baseline Owner에서 관리한다.

**Local Decision**
- 현재 Feature에만 영향을 주는 결정
- 특정 Validation, 예외 처리, Loading/Empty/Error 동작 등
- 해당 Feature Spec에서 관리한다.

Local 문서가 Global 결정을 새로 만들면 안 된다.

---

## 2.7 TBD / N/A / Optional — MUST

| 표기 | 의미 |
|---|---|
| `TBD` | 결정은 필요하지만 아직 결정하지 않음 |
| `N/A` | 해당 항목이 적용되지 않음 |
| `Optional` | 프로젝트 특성에 따라 선택적으로 사용 가능 |

빈 칸만 남겨 미결정인지, 미적용인지, 누락인지 알 수 없게 만들지 않는다.

현재 Feature 구현에 필요한 `TBD`는 구현 전에 해결한다.

---

# 3. AI Readability Rules

## 3.1 Structure for Retrieval — MUST

- 명확한 Heading을 사용한다.
- 하나의 Section에는 하나의 주제를 둔다.
- 중요한 규칙을 긴 문단 속에 숨기지 않는다.
- 흐름, 상태, 선택지는 표·목록·짧은 코드 블록을 우선한다.
- 같은 의미를 여러 표현으로 반복하지 않는다.
- 모호한 대명사 대신 실제 문서명과 개념명을 사용한다.

예:

```text
MVP 범위는 `MVP_BASELINE.md`를 따른다.
```

---

## 3.2 Context Minimum Principle — MUST

AI에게 매 작업마다 모든 문서를 읽히지 않는다.

현재 작업에 필요한 최소 Context만 제공한다.

```text
CLAUDE.md
+
현재 Feature 관련 Baseline
+
현재 Feature Spec
+
필요한 Backlog 정보
```

`WORKFLOW.md`는 상위 운영 매뉴얼이며 모든 Feature 구현 때 전체를 다시 읽게 하는 문서로 설계하지 않는다.

---

## 3.3 Document Length — MUST

문서 길이 자체보다 **중복과 탐색 가능성**을 우선한다.

다음 경우 축소 또는 분리를 검토한다.

- 서로 다른 Primary Responsibility가 섞였다.
- 같은 내용을 여러 Section에서 반복한다.
- 현재 작업과 무관한 내용을 AI가 계속 읽어야 한다.
- 일부 내용이 별도의 Owner를 갖는 편이 명확하다.

문서가 길어지면 다음 순서로 정리한다.

1. 중복 제거
2. 예시 축소
3. 작성 형식을 Template으로 이동
4. 실제 작업 지시를 Prompt로 이동
5. 필요한 사례는 문서 내부의 명시적 Non-normative Example로 최소화

중요한 규칙을 단순히 길이를 줄이기 위해 삭제하지 않는다.

---

## 3.4 Terminology Consistency — MUST

핵심 용어는 Repository 전체에서 동일하게 사용한다.

```text
Baseline
Owner
Source of Truth
Implementation Backlog
Feature
Feature Spec
Baseline Impact
Planner / Reviewer
Implementer
DONE
TBD
N/A
```

같은 개념을 여러 이름으로 혼용하지 않는다.

---

# 4. Markdown & Naming Rules

## 4.1 File Naming — MUST

기본 파일명:

```text
UPPER_SNAKE_CASE.md
```

Template:

```text
<NAME>_TEMPLATE.md
```

Prompt:

```text
<ACTION>_PROMPT.md
```

파일명만 보고 역할을 알 수 있어야 한다.

---

## 4.2 Heading & Style — SHOULD

기본 Heading:

```markdown
# Document Title
## Major Section
### Subsection
```

`####` 이하가 반복해서 필요하면 문서 구조를 다시 검토한다.

작성 스타일:

- 문장은 짧고 직접적으로 작성한다.
- 한 문단에 하나의 핵심 주장만 둔다.
- 긴 산문보다 표와 목록을 우선한다.
- 불필요한 서론과 반복을 제거한다.
- `가능하면`, `적절히`, `필요한 경우`에는 가능하면 판단 기준을 함께 적는다.

---

## 4.3 Cross-Reference — MUST

다른 문서의 규칙이 필요하면 내용을 복사하지 않고 파일명을 명시한다.

```text
MVP 범위는 `MVP_BASELINE.md`를 따른다.
```

필요하면 Section까지 명시한다.

경로가 안정적이면 상대 경로 Markdown Link를 사용할 수 있다.

---

## 4.4 Example — MUST

Example은 규칙과 명확히 구분한다.

```text
Example:
```

또는:

```text
Non-normative Example:
```

Example에 포함된 기술, Entity, 상태, UI 구조를 범용 규칙처럼 표현하지 않는다.

---

## 4.5 Version & Metadata — MUST

중앙 Workflow Repository의 Version은 루트 `VERSION`과 `CHANGELOG.md`가 관리한다.

모든 파일에 별도 Version을 반복해서 넣지 않는다.

버전 추적이 유용한 Project Repository는 자신이 채택한 Workflow Version을 기록하는 것을 권장한다. 중앙 Workflow는 기록 위치나 형식을 강제하지 않는다.

필요한 경우 문서 상단에는 최소 Metadata만 둔다.

```markdown
**Status:** Draft
**Scope:** ...
```

---

# 5. Document-Type Boundaries

| 문서 종류 | 소유하는 것 | 소유하지 않는 것 |
|---|---|---|
| `WORKFLOW.md` | 개발 방법, 단계, 진입/종료 조건, 역할 경계, Verification/DONE 상위 규칙, Feedback Loop | Template 상세 항목, 실제 Prompt 문구, 특정 Project 기능·기술 |
| `templates/` | 실제 Project 문서의 구조와 작성 항목 | 새로운 Workflow 정책, 특정 서비스 값 |
| `prompts/` | 기존 Workflow와 Project 문서를 현재 단계에서 AI가 실행하도록 하는 지시 | 새로운 제품 정책, 새로운 Workflow 정책 |
| Project 문서 | 해당 프로젝트의 실제 확정 결정 | 범용 Workflow 자체 |

## 5.1 Template 추가 규칙 — MUST

- 특정 서비스 값으로 미리 채우지 않는다.
- Owner 책임을 명확히 한다.
- 필요한 경우 `N/A` 또는 생략 가능 여부를 표시한다.
- 다른 Baseline 내용을 복사하도록 요구하지 않는다.
- 작성 안내가 필요하면 Markdown HTML Comment를 사용할 수 있다.

```markdown
<!-- 이번 MVP에서 명시적으로 제외하는 범위를 작성한다. -->
```

## 5.2 Prompt 추가 규칙 — MUST

Prompt에는 최소한 다음을 명확히 한다.

- 현재 작업 목적
- 읽어야 할 문서
- 현재 Scope
- 변경하면 안 되는 영역
- 사용자 결정이 필요한 경우의 처리
- 결과물 또는 보고 형식

Prompt가 Owner 문서와 충돌하면 Prompt를 수정한다.

## 5.3 Project 문서 추가 규칙 — MUST

- Template을 프로젝트의 실제 결정으로 채운다.
- 빈 Template을 Source of Truth로 취급하지 않는다.
- Project-specific 결정을 중앙 Workflow Repository에 넣지 않는다.
- Feature Spec에서 Baseline을 재정의하지 않는다.
- 구현 중 확정된 중요한 결정은 올바른 Owner 문서에 반영한다.

---

# 6. Verification & Change Rules

## 6.1 Avoid Hidden Assumptions — MUST

모호한 지시만 남기지 않는다.

나쁜 예:

```text
적절한 검증을 실행한다.
```

좋은 예:

```text
Repository에 실제 존재하는 Build, Typecheck, Lint, Test 등
현재 Feature에 필요한 검증을 실행한다.
```

프로젝트마다 달라지는 실제 명령어까지 범용 문서에서 강제하지 않는다.

---

## 6.2 Verification Status — MUST

| 상태 | 의미 |
|---|---|
| `PASS` | 실제 실행했고 성공 |
| `FAIL` | 실제 실행했고 실패 |
| `NOT_RUN` | 실행하지 않음 |
| `BLOCKED` | 실행하려 했지만 외부 조건 등으로 수행 불가 |

실행하지 않은 검증을 추정으로 `PASS` 처리하지 않는다.

---

## 6.3 Change Discipline — MUST

결정이 바뀌면 해당 Owner 문서를 먼저 수정한다.

변경 후 확인한다.

- 새 중복이 생기지 않았는가
- 다른 문서의 책임을 침범하지 않았는가
- 새 `TBD`가 현재 구현을 막지 않는가
- 관련 Template 또는 Prompt도 실제로 수정되어야 하는가

---

## 6.4 Workflow Version Discipline — MUST

**Project-specific Change**
→ 해당 Project Repository만 수정

**Reusable Workflow Change**
→ 중앙 Workflow Repository 수정 후보

Workflow 변경이 확정되면 필요한 경우:

```text
WORKFLOW / Template / Prompt 수정
↓
CHANGELOG.md 업데이트
↓
VERSION 업데이트
```

새 Workflow Version을 기존 Project에 자동 적용하지 않는다.

---

# 7. Document Creation Gate

새 Markdown 문서를 만들기 전에 다음을 확인한다.

1. 기존 Owner 문서로 처리할 수 없는가?
2. 독립적인 Primary Responsibility가 있는가?
3. 여러 기존 문서의 내용을 단순히 모으는 문서는 아닌가?
4. 이 문서가 실제 Workflow에 필요한가?
5. AI가 이 문서를 별도로 읽어야 할 이유가 있는가?

명확한 이유가 없다면 새 문서를 만들지 않는다.

---

# 8. Document Review Checklist

## Responsibility
- [ ] Primary Responsibility를 한 문장으로 설명할 수 있는가?
- [ ] 다른 Owner 문서의 결정을 재정의하지 않는가?

## Scope
- [ ] 현재 목적에 필요한 내용만 있는가?
- [ ] 미래 세부사항을 과도하게 결정하지 않았는가?
- [ ] Global / Local Decision이 올바른 문서에 있는가?

## Duplication
- [ ] 같은 규칙을 다른 문서에서 반복하지 않는가?
- [ ] 필요한 경우 Owner 문서를 참조하는가?

## AI Readability
- [ ] Heading만 훑어도 구조를 이해할 수 있는가?
- [ ] 중요한 규칙이 긴 문단에 묻혀 있지 않은가?
- [ ] 핵심 용어가 일관적인가?
- [ ] 불필요한 Context를 AI에게 요구하지 않는가?

## State & References
- [ ] `TBD`, `N/A`, `Optional`을 올바르게 사용했는가?
- [ ] 현재 구현을 막는 `TBD`가 남아 있지 않은가?
- [ ] 다른 문서를 참조할 때 파일명이 명확한가?
- [ ] Example을 규칙처럼 표현하지 않았는가?

---

# 9. Final Principle

모든 문서를 작성할 때 먼저 다음 세 가지를 확인한다.

```text
이 내용은 지금 필요한가?
↓
이 결정의 Owner는 어디인가?
↓
AI가 이 문서를 읽었을 때 오해 없이 행동할 수 있는가?
```

> **문서의 목표는 많은 정보를 기록하는 것이 아니라, 필요한 결정을 올바른 위치에 명확하게 남기는 것이다.**
