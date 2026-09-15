# Implementation Backlog

**Status:** Draft  
**Scope:** Implementation order, dependencies, and progress status

<!--
Primary Responsibility:
이 문서는 "다음에 무엇을 구현해야 하며, 현재 각 작업은 어떤 상태인가?"를 정의합니다.

작성 원칙:
- 구현 항목, 구현 순서, 의존성, 현재 상태를 관리합니다.
- Feature 상세 동작, 제품 정책, Architecture, Data Model을 이 문서에서 새로 정의하지 않습니다.
- Backlog Item은 가능한 한 한 번의 기획 → 구현 → 실행 → 수정 Loop 안에서 끝낼 수 있는 크기로 나눕니다.
- 구현 세부가 필요한 경우 해당 Feature Spec 또는 Owner 문서를 참조합니다.
-->

---

## 1. Backlog Scope

<!--
이 Backlog가 관리하는 프로젝트 또는 구현 범위를 작성합니다.
MVP 범위를 다시 정의하지 말고 필요한 경우 MVP_BASELINE.md를 참조합니다.
-->

### Project / Product

TBD

### Backlog Scope

TBD

### Related Baseline Documents

<!--
현재 Backlog 전체와 직접 관련된 Baseline만 작성합니다.
모든 프로젝트 문서를 나열하지 않습니다.
-->

- TBD

---

## 2. Status Definitions

<!--
Backlog Item의 상태는 아래 다섯 개만 사용합니다.
DONE의 상세 기준은 WORKFLOW.md를 따릅니다.
-->

| Status | Meaning |
|---|---|
| `TODO` | 구현 대상이지만 아직 다음 작업으로 시작할 준비가 되지 않은 상태 |
| `READY` | 필요한 선행 작업과 현재 단계의 전역 결정이 준비되어 다음 작업 후보가 될 수 있는 상태 |
| `IN_PROGRESS` | 현재 Feature Planning 또는 Implementation Loop가 시작된 상태 |
| `BLOCKED` | Dependency, 미확정 결정, 외부 조건 등으로 현재 진행할 수 없는 상태 |
| `DONE` | `WORKFLOW.md`의 Definition of Done을 충족한 상태 |

---

## 3. Milestones — Optional

<!--
여러 Backlog Item을 묶어 실제 End-to-End 가치 흐름을 관리할 필요가 있을 때만 작성합니다.
단순한 Feature 그룹이 아니라, 완료 시 어떤 사용자/운영 흐름이 처음부터 끝까지 동작하는지 기준으로 작성합니다.
필요하지 않으면 N/A 또는 Section 생략이 가능합니다.
-->

| Milestone | Outcome | Included Backlog IDs | Status |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 4. Implementation Backlog

<!--
이 문서의 핵심 Section입니다.

Column 기준:
- Order: 의도된 구현 순서. 우선순위가 바뀌면 수정할 수 있습니다.
- ID: 안정적인 Backlog Item 식별자. 특정 Prefix를 강제하지 않습니다.
- Item: 구현할 작은 Feature 또는 기술 Setup 작업의 이름입니다.
- Goal: 이 Item이 완료되면 무엇이 가능해지는지 짧게 작성합니다.
- Depends On: 먼저 완료되어야 하는 Backlog ID. 없으면 N/A.
- Status: TODO / READY / IN_PROGRESS / BLOCKED / DONE 중 하나만 사용합니다.
- Related Docs: 현재 Item과 직접 관련된 Owner 문서 또는 Feature Spec만 작성합니다.
- Notes: Blocker, 선행 결정 등 Backlog 관리에 필요한 짧은 정보만 작성합니다.

Feature 상세 Flow, Validation, Exceptions, UI Behavior, Acceptance Criteria, 구현 방법은 작성하지 않습니다.
-->

| Order | ID | Item | Goal | Depends On | Status | Related Docs | Notes |
|---|---|---|---|---|---|---|---|
| TBD | TBD | TBD | TBD | N/A | `TODO` | TBD | TBD |

### Backlog Item Size Check

<!--
각 Item은 가능한 한 한 번의 Feature Development Loop에서 완료할 수 있는 크기여야 합니다.

판단 기준:
"한 번의 기획 → 구현 → 실행 → 수정 사이클에서 끝낼 수 있는가?"

너무 크다면 더 작은 Backlog Item으로 나눕니다.
-->

TBD

### READY Check

<!--
READY로 변경하기 전 최소한 다음을 확인합니다.
- 필수 선행 Backlog가 완료되었는가?
- 현재 Item을 계획하는 데 필요한 Baseline이 존재하는가?
- 현재 알려진 Global Blocker가 없는가?
- Item 자체가 한 번의 개발 Loop에 적절한 크기인가?

Feature Spec 작성 완료를 READY의 필수조건으로 두지 않습니다.
READY Item을 선택한 뒤 Feature Spec 필요 여부를 판단합니다.
-->

TBD

### BLOCKED Notes

<!--
BLOCKED Item은 다음을 파악할 수 있어야 합니다.
- 무엇 때문에 막혔는가?
- 어떤 결정 또는 Dependency가 필요한가?
- 무엇이 해결되면 다시 진행할 수 있는가?

제품 정책이나 Architecture 결정을 Notes에서 직접 해결하지 말고 해당 Owner 문서를 참조합니다.
-->

TBD

---

## 5. TBD — Optional

<!--
Backlog 운영상 결정은 필요하지만 아직 현재 구현 순서에 영향을 주지 않는 항목만 작성합니다.
제품 정책, Architecture, Data Model Decision은 해당 Owner 문서의 TBD에서 관리합니다.
필요하지 않으면 N/A 또는 Section 생략이 가능합니다.
-->

| Decision | Why Deferred | Must Be Decided Before |
|---|---|---|
| TBD | TBD | TBD |

---

## 6. Review Checklist

- [ ] 각 Backlog Item이 한 번의 개발 Loop에 적절한 크기인가?
- [ ] 각 Item에 안정적인 ID가 있는가?
- [ ] 실제 구현 순서를 파악할 수 있는가?
- [ ] 필요한 Dependency가 명확한가?
- [ ] 각 Status가 `TODO / READY / IN_PROGRESS / BLOCKED / DONE` 중 하나인가?
- [ ] READY Item이 실제로 다음 작업 후보가 될 수 있는가?
- [ ] BLOCKED Item의 원인과 해제 조건을 파악할 수 있는가?
- [ ] DONE을 단순 코드 작성 완료로 처리하지 않았는가?
- [ ] 가능한 경우 핵심 End-to-End 흐름을 먼저 완성하는 순서인가?
- [ ] Feature 상세 동작을 Backlog에 작성하지 않았는가?
- [ ] MVP 범위나 제품 정책을 Backlog에서 새로 정의하지 않았는가?
- [ ] Architecture 또는 Data Model Decision을 Backlog에서 새로 정의하지 않았는가?
- [ ] Related Docs가 현재 Item에 필요한 문서만 참조하는가?
- [ ] Notes가 상세 Feature Spec처럼 길어지지 않았는가?
- [ ] 미래 Feature를 필요 이상으로 미리 세분화하지 않았는가?
