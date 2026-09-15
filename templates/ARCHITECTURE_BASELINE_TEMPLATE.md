# Architecture Baseline

**Status:** Draft  
**Scope:** System architecture, component responsibilities, and execution boundaries

<!--
Primary Responsibility:
이 문서는 "이 시스템은 어떤 주요 구성 요소로 이루어지고, 각 구성 요소는 무엇을 책임지며,
서로 어떤 경계로 연결되고 어디에서 실행되는가?"를 정의합니다.

작성 원칙:
- 시스템의 주요 구성 요소와 전역 Architecture 경계만 작성합니다.
- MVP 범위, 사용자/관리자 IA, Data Model, Feature 상세 동작은 각 Owner 문서에 작성합니다.
- 특정 기술 스택이나 Provider를 모든 프로젝트에 강제하지 않습니다.
- 아직 결정할 필요가 없는 사항은 TBD로 둘 수 있습니다.
- 적용되지 않는 항목은 N/A로 표시합니다.
-->

---

## 1. Architecture Scope

<!--
이 Architecture Baseline이 다루는 시스템 범위를 작성합니다.
Feature 목록을 다시 작성하지 말고, 필요한 경우 다른 Owner 문서를 참조합니다.
-->

### System Scope

TBD

### Included Surfaces / Services

| Surface / Service | Included | Notes |
|---|---|---|
| TBD | TBD | TBD |

### Architecture Boundary

TBD

### Key Architecture Constraints

<!--
여러 Feature에 공통으로 영향을 주는 전역 Architecture 제약만 작성합니다.
세부 구현 규칙이나 코드 스타일은 작성하지 않습니다.
-->

- TBD

---

## 2. System Components

<!--
시스템을 구성하는 주요 Component를 정의합니다.
실제 프로젝트에서 필요한 Component만 작성합니다.

예시 범주:
User Client / Admin Client / Backend / Database / Auth Service / Worker / Scheduler / External API / Storage

위 예시는 가능한 범주일 뿐 기본 구성을 강제하지 않습니다.
-->

| Component | Responsibility | Technology / Provider | Runtime / Location |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 3. Component Responsibilities & Boundaries

<!--
각 Component가 무엇을 소유하고 무엇을 소유하지 않는지 정의합니다.
AI Implementer가 Feature마다 책임 위치를 임의로 바꾸지 않도록 전역 경계를 명확히 합니다.
-->

| Component | Owns | Does Not Own / Boundary |
|---|---|---|
| TBD | TBD | TBD |

---

## 4. Communication & Integration Boundaries

<!--
주요 Component 사이의 통신 관계를 정의합니다.
실제 Endpoint, Request Payload, 함수명 등 구현 세부사항은 작성하지 않습니다.
-->

| From | To | Purpose | Boundary / Rule |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 5. Authentication & Authorization Boundaries

<!--
인증과 권한에 대한 전역 Architecture 경계를 정의합니다.

이 Section에서 다룰 수 있는 내용:
- Authentication Owner
- Authorization Enforcement Location
- User / Admin Separation
- Role / Permission Boundary
- Trusted vs Untrusted Boundary

다음은 이 문서의 책임이 아닙니다.
- Login 화면 구성
- 특정 Feature의 접근 UX
- Role별 메뉴 표시 세부
- 구체적인 RLS SQL
- 구체적인 Permission Code
-->

| Concern | Owner / Enforcement Point | Architecture Rule |
|---|---|---|
| TBD | TBD | TBD |

---

## 6. Data & Storage Boundaries

<!--
Architecture 관점에서 Data가 어디에 저장되고 어느 Component가 접근 책임을 가지는지만 정의합니다.

이 Section에서는 다음을 정의하지 않습니다.
- Entity
- Field
- Relationship
- Business State
- Lifecycle
- SQL Type
- Index
- Migration

이러한 내용은 DATA_MODEL_BASELINE.md 또는 구현 단계의 책임입니다.
-->

| Storage / Data Service | Responsibility | Access Boundary |
|---|---|---|
| TBD | TBD | TBD |

---

## 7. Background Jobs / Automation / Async Execution — Optional

<!--
Background Task, Scheduler, Queue, Worker, Automation 등이 존재할 때만 작성합니다.
해당 구조가 없다면 N/A로 표시합니다.

이 Section에서는 실행 Trigger, Execution Owner, 상위 Responsibility만 정의합니다.
Cron 표현식의 세부 값, Function 이름, Retry 코드, Feature별 Business Rule은 작성하지 않습니다.
-->

| Job / Execution Type | Trigger | Execution Owner | High-Level Responsibility |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 8. Shared Core / Module Boundaries — Optional

<!--
여러 App 또는 Service가 존재하고 실제 공유 경계가 필요한 경우에만 작성합니다.
미래 확장을 이유로 Shared Package나 공통 Layer를 선행 설계하지 않습니다.
필요하지 않다면 N/A로 표시합니다.
-->

| Shared Boundary | Used By | Owns | Must Not Own |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 9. Key Execution Flows

<!--
Architecture적으로 중요한 대표 실행 경로만 작성합니다.
Component 간 실행 경계를 보여주는 것이 목적입니다.

다음은 작성하지 않습니다.
- 사용자 Feature 상세 Flow
- Business Validation
- Business State 변경 규칙
- 화면 이동
-->

### Flow 1 — TBD

```text
TBD
↓
TBD
↓
TBD
```

### Flow 2 — Optional

N/A

---

## 10. Deployment & Runtime Boundaries

<!--
각 주요 Component가 어디에서 실행·배포되는지 상위 수준에서 정의합니다.
세부 CI/CD Script나 배포 명령은 작성하지 않습니다.
-->

| Component | Runtime / Deployment Target | Responsibility / Notes |
|---|---|---|
| TBD | TBD | TBD |

---

## 11. External Services & Dependencies

<!--
Architecture에 영향을 주는 중요한 외부 Service와 책임 경계만 정의합니다.
모든 Package나 Library를 나열하지 않습니다.

예시 범주:
Authentication Provider / Payment Provider / AI Service / Email Provider / External Data API / Cloud Storage
-->

| External Service | Purpose | Called By | Boundary / Dependency |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 12. Architecture Constraints

<!--
여러 Feature에 공통으로 적용되어 Implementer가 반드시 따라야 하는 전역 Architecture 제약만 작성합니다.
Template이 특정 Constraint를 기본값으로 강제하지 않습니다.
실제 프로젝트에서 결정된 Constraint만 작성합니다.
-->

| Constraint | Reason / Boundary |
|---|---|
| TBD | TBD |

---

## 13. TBD

<!--
결정은 필요하지만 현재 시점에는 확정할 필요가 없는 Architecture Decision만 작성합니다.
현재 Feature 구현에 필요한 Architecture TBD는 구현 전에 해결해야 합니다.
-->

| Decision | Why Deferred | Must Be Decided Before |
|---|---|---|
| TBD | TBD | TBD |

---

## 14. Review Checklist

- [ ] Architecture Scope와 Boundary가 명확한가?
- [ ] 주요 System Component가 명확한가?
- [ ] 각 Component의 Responsibility가 겹치지 않는가?
- [ ] Frontend / Backend / Service 경계가 필요한 수준으로 정의되어 있는가?
- [ ] Component 사이의 Communication Boundary가 명확한가?
- [ ] Authentication / Authorization의 Owner와 Enforcement Point가 명확한가?
- [ ] 필요한 Data / Storage 접근 경계가 명확한가?
- [ ] Background Job / Automation이 있다면 Trigger와 Execution Owner가 명확한가?
- [ ] Shared Core를 실제 필요 없이 선행 설계하지 않았는가?
- [ ] 주요 Key Execution Flow가 Component 경계 중심으로 설명되어 있는가?
- [ ] Deployment / Runtime 위치가 필요한 수준으로 정의되어 있는가?
- [ ] 중요한 External Service의 역할과 Dependency Boundary가 명확한가?
- [ ] 여러 Feature에 공통인 Architecture Constraint가 필요한 수준으로 정의되어 있는가?
- [ ] MVP 범위를 이 문서에서 다시 정의하지 않았는가?
- [ ] 사용자/관리자 IA를 이 문서에서 다시 정의하지 않았는가?
- [ ] Data Model, Business State, Lifecycle을 이 문서에서 다시 정의하지 않았는가?
- [ ] Feature 상세 동작이나 API 상세까지 내려가지 않았는가?
- [ ] 함수명, 파일명, Endpoint명 등 코드 수준 구현 세부를 불필요하게 고정하지 않았는가?
- [ ] 미래 확장을 위한 불필요한 Infrastructure를 선행 설계하지 않았는가?
- [ ] 다른 Owner 문서의 결정을 중복해서 작성하지 않았는가?
- [ ] 현재 구현을 막는 Architecture TBD가 남아 있지 않은가?
