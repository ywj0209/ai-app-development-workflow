# User App Structure

**Status:** Draft  
**Scope:** User-facing product structure and high-level user flows

<!--
Primary Responsibility:
이 문서는 "사용자는 제품의 어떤 영역에서 무엇을 하고, 주요 영역 사이를 어떻게 이동하는가?"를 정의합니다.

작성 원칙:
- 사용자용 제품의 상위 IA와 주요 이용 흐름만 작성합니다.
- MVP 범위, Architecture, Data Model, Feature 상세 동작은 각 Owner 문서에 작성합니다.
- 특정 Navigation 방식이나 인증 상태를 모든 프로젝트에 강제하지 않습니다.
- 아직 결정할 필요가 없는 사항은 TBD로 둘 수 있습니다.
- 적용되지 않는 항목은 N/A로 표시합니다.
-->

---

## 1. Structure Scope

<!--
이 문서가 다루는 사용자용 제품 Surface를 작성합니다.
기술 Framework나 배포 방식이 아니라 사용자 경험의 범위를 기준으로 작성합니다.

예: Mobile App / Web App / Desktop App / User-facing Web + Mobile
-->

### Product Surface

TBD

### Scope Boundary

<!-- 이 문서가 다루는 사용자 영역과 다루지 않는 영역을 짧게 작성합니다. -->

TBD

---

## 2. Top-Level Information Architecture

<!--
사용자용 제품의 가장 큰 영역만 정의합니다.
세부 화면, Component, Feature 내부 단계까지 내려가지 않습니다.
-->

| Area | Purpose | Parent / Level |
|---|---|---|
| TBD | TBD | TBD |

---

## 3. Global Navigation

<!--
사용자가 주요 영역 사이를 이동하는 기본 Navigation 구조를 작성합니다.
특정 Navigation 방식(Bottom Tab, Sidebar 등)을 강제하지 않습니다.
해당 구조가 없는 제품은 N/A로 표시할 수 있습니다.
-->

### Navigation Pattern

TBD

### Primary Destinations

| Destination | Purpose | Entry Condition / Notes |
|---|---|---|
| TBD | TBD | TBD |

### Default Entry

TBD

---

## 4. Major Area Responsibilities

<!--
각 주요 영역이 무엇을 책임지는지 한 문장 수준으로 정의합니다.
Feature 상세 동작이나 UI 구성은 작성하지 않습니다.
-->

| Area | Primary Responsibility | Main User Intent |
|---|---|---|
| TBD | TBD | TBD |

---

## 5. Primary Entry Points

<!--
사용자가 주요 영역에 어떤 사용자 경험상의 경로로 진입하는지 정의합니다.
Deep Link URL, Routing 구현, 인증 코드 등 기술 세부사항은 작성하지 않습니다.
-->

| Entry Point | Destination | Purpose / Notes |
|---|---|---|
| TBD | TBD | TBD |

---

## 6. Core User Flows

<!--
여러 주요 영역이 연결되는 대표적인 상위 사용자 흐름만 작성합니다.
모든 Feature Flow를 나열하지 않습니다.
Feature 내부의 상세 동작은 해당 Feature Spec에서 정의합니다.
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

## 7. User State / Access State Flow

<!--
사용자 상태에 따라 상위 제품 흐름이 달라지는 경우에만 작성합니다.
예: Guest / Authenticated / Onboarding Required / Role-specific

인증 기술, Session 처리, RLS, 권한 검사 구현은 ARCHITECTURE_BASELINE.md의 책임입니다.
상태 구분이 없는 프로젝트는 N/A로 표시합니다.
-->

| User / Access State | Accessible Areas | High-Level Difference |
|---|---|---|
| TBD | TBD | TBD |

### State Transition Notes

<!--
상위 UX 관점에서 필요한 상태 전환만 작성합니다.
상세 State Machine이나 데이터 Lifecycle을 다시 정의하지 않습니다.
-->

TBD

---

## 8. TBD

<!--
결정은 필요하지만 현재 시점에는 확정할 필요가 없는 사용자 앱 상위 구조 결정만 작성합니다.
현재 구현을 막는 TBD는 관련 Feature 구현 전에 해결해야 합니다.
-->

| Decision | Why Deferred | Must Be Decided Before |
|---|---|---|
| TBD | TBD | TBD |

---

## 9. Review Checklist

- [ ] 이 문서가 다루는 Product Surface가 명확한가?
- [ ] Top-Level Information Architecture가 명확한가?
- [ ] Global Navigation 또는 N/A 여부가 명확한가?
- [ ] 각 주요 영역의 Primary Responsibility가 겹치지 않는가?
- [ ] 주요 Entry Point가 사용자 경험 관점에서 설명되어 있는가?
- [ ] 대표적인 Core User Flow가 상위 수준에서 설명되어 있는가?
- [ ] 필요한 경우 User / Access State에 따른 상위 흐름 차이가 정의되어 있는가?
- [ ] MVP 범위를 이 문서에서 다시 정의하지 않았는가?
- [ ] Architecture를 이 문서에서 정의하지 않았는가?
- [ ] Data Model을 이 문서에서 정의하지 않았는가?
- [ ] Feature 상세 동작이나 상세 UI까지 내려가지 않았는가?
- [ ] 다른 Owner 문서의 결정을 중복해서 작성하지 않았는가?
- [ ] 현재 구현을 막는 TBD가 남아 있지 않은가?
