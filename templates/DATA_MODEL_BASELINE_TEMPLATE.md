# Data Model Baseline

**Status:** Draft  
**Scope:** Core data meaning, relationships, states, and lifecycle

<!--
Primary Responsibility:
이 문서는 "이 제품에서 핵심 데이터는 무엇이며, 각각 무엇을 의미하고,
서로 어떤 관계를 가지며, 어떤 상태와 Lifecycle을 가지는가?"를 정의합니다.

작성 원칙:
- 핵심 데이터의 논리적 의미와 관계만 작성합니다.
- MVP 범위, 사용자/관리자 IA, Architecture, Feature 상세 동작은 각 Owner 문서에 작성합니다.
- SQL Type, Index, Constraint 구현, Migration, RLS SQL 같은 Physical Database 구현은 기본적으로 작성하지 않습니다.
- 아직 결정할 필요가 없는 사항은 TBD로 둘 수 있습니다.
- 적용되지 않는 항목은 N/A로 표시합니다.
-->

---

## 1. Data Model Scope

<!--
이 Data Model Baseline이 다루는 제품 데이터 범위를 작성합니다.
Feature 목록이나 Architecture 구조를 다시 작성하지 않습니다.
필요한 경우 다른 Owner 문서를 참조합니다.
-->

### Model Scope

TBD

### Included Domain

| Domain / Data Area | Included | Notes |
|---|---|---|
| TBD | TBD | TBD |

### Excluded / Deferred Domain

| Domain / Data Area | Status | Notes |
|---|---|---|
| TBD | TBD | TBD |

### Related Owner References

<!-- 필요한 경우 관련 Owner 문서만 참조하고 내용을 복사하지 않습니다. -->

- TBD

---

## 2. Core Entities

<!--
제품에서 독립적인 의미와 Lifecycle을 가지는 핵심 Entity를 정의합니다.

판단 기준:
- 이 데이터는 무엇을 나타내는가?
- 왜 독립적인 Entity여야 하는가?

단순히 화면 하나에 필요하다는 이유만으로 Entity를 만들지 않습니다.
미래 확장을 예상해 아직 필요하지 않은 Entity를 미리 추가하지 않습니다.
-->

| Entity | Meaning | Primary Responsibility / Purpose |
|---|---|---|
| TBD | TBD | TBD |

---

## 3. Core Fields

<!--
각 핵심 Entity에서 제품 의미상 중요한 Field만 정의합니다.

이 Section의 목적:
- 이 Field는 무엇을 의미하는가?
- 제품 동작상 반드시 존재해야 하는가?

다음은 기본적으로 작성하지 않습니다.
- SQL Type
- Database Default Expression
- ORM Annotation
- Column Index
- Physical Constraint 구현
-->

| Entity | Field | Meaning | Required / Optional | Notes |
|---|---|---|---|---|
| TBD | TBD | TBD | TBD | TBD |

---

## 4. Entity Relationships

<!--
핵심 Entity 사이의 논리적 관계를 정의합니다.
Database Foreign Key 구현을 미리 정의하는 것이 목적이 아닙니다.

관계 예시:
1:1 / 1:N / N:M / Optional / Required

Join Table 이름이나 Foreign Key Column 이름은 제품 의미상 필요하지 않다면 미리 고정하지 않습니다.
-->

| From Entity | Relationship | To Entity | Cardinality | Meaning |
|---|---|---|---|---|
| TBD | TBD | TBD | TBD | TBD |

---

## 5. Entity States

<!--
상태를 가지는 핵심 Entity만 작성합니다.

State는 여러 Feature에 공통으로 영향을 주는 Business State일 때 Baseline에서 관리합니다.
Loading, Selected, Modal Open 같은 UI State는 이 문서의 책임이 아닙니다.
-->

| Entity | State | Meaning | Terminal? |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

---

## 6. Lifecycle & State Transitions

<!--
핵심 Entity의 생성부터 종료까지 중요한 Lifecycle과 허용되는 상태 전환을 정의합니다.

이 Section이 답해야 하는 질문:
- 이 데이터는 어떻게 생성되는가?
- 어떤 주요 상태를 거치는가?
- 어떤 상태 전환이 가능한가?
- 언제 더 이상 활성 데이터가 아닌가?

버튼 클릭, API 호출, 화면 동작 같은 Feature 세부 구현은 작성하지 않습니다.
-->

| Entity | From | To | Meaning / Condition |
|---|---|---|---|
| TBD | TBD | TBD | TBD |

### Lifecycle Overview — Optional

```text
TBD
↓
TBD
↓
TBD
```

---

## 7. Common Metadata

<!--
여러 핵심 Entity에서 공통으로 필요한 제품 의미가 있는 Metadata만 정의합니다.

예시 범주:
Created Time / Updated Time / Source / Owner / Created By / Published Time

Template이 특정 Metadata를 필수로 강제하지 않습니다.
Database Framework가 자동으로 제공한다는 이유만으로 기술 Metadata를 전부 나열하지 않습니다.
-->

| Metadata | Meaning | Applies To |
|---|---|---|
| TBD | TBD | TBD |

---

## 8. Data Ownership / Source — Optional

<!--
데이터의 생성 주체나 Source가 여러 Feature에 공통으로 영향을 주는 경우에만 작성합니다.

예시 범주:
User-created / Admin-created / External API / Automated

어느 Database나 Storage에 저장되는지는 ARCHITECTURE_BASELINE.md의 책임입니다.
필요하지 않으면 N/A로 표시합니다.
-->

| Entity / Data | Source / Owner | Meaning / Boundary |
|---|---|---|
| TBD | TBD | TBD |

---

## 9. Global Data Rules — Optional

<!--
여러 Feature에 공통으로 영향을 주는 논리적 데이터 불변조건이 있는 경우에만 작성합니다.

예:
- 특정 관계는 반드시 하나만 존재해야 한다.
- 특정 데이터는 특정 상태에서만 의미가 있다.
- 하나의 Entity는 특정 Parent에 반드시 속해야 한다.

Database Constraint 구현 방법은 작성하지 않습니다.
Feature 하나에만 필요한 Validation은 해당 Feature Spec에서 관리합니다.
-->

| Rule | Applies To | Meaning |
|---|---|---|
| TBD | TBD | TBD |

---

## 10. TBD

<!--
결정은 필요하지만 현재 시점에는 확정할 필요가 없는 Data Model Decision만 작성합니다.
현재 Feature 구현에 필요한 Data Model TBD는 구현 전에 해결해야 합니다.
-->

| Decision | Why Deferred | Must Be Decided Before |
|---|---|---|
| TBD | TBD | TBD |

---

## 11. Review Checklist

- [ ] Data Model Scope가 명확한가?
- [ ] Core Entity가 제품 의미를 기준으로 정의되어 있는가?
- [ ] 각 Entity의 책임을 한 문장으로 설명할 수 있는가?
- [ ] Core Field의 의미가 명확한가?
- [ ] 필요 이상의 미래 Field를 미리 만들지 않았는가?
- [ ] Entity Relationship과 Cardinality가 필요한 수준으로 정의되어 있는가?
- [ ] Business State와 UI State를 구분했는가?
- [ ] 각 State의 의미가 명확한가?
- [ ] 필요한 Lifecycle과 State Transition이 정의되어 있는가?
- [ ] Common Metadata가 제품 의미상 필요한 것만 포함하는가?
- [ ] 필요한 경우 Data Ownership / Source가 명확한가?
- [ ] Feature별 Validation을 Global Data Rule로 올리지 않았는가?
- [ ] MVP 범위를 이 문서에서 다시 정의하지 않았는가?
- [ ] 사용자/관리자 IA를 이 문서에서 다시 정의하지 않았는가?
- [ ] Architecture의 Storage / Access Boundary를 이 문서에서 다시 정의하지 않았는가?
- [ ] SQL Type, Index, Constraint 구현, Migration 등 Physical Database 구현까지 내려가지 않았는가?
- [ ] API, Query, Feature 상세 동작을 이 문서에서 정의하지 않았는가?
- [ ] 현재 필요하지 않은 Entity나 관계를 미래 확장을 위해 미리 만들지 않았는가?
- [ ] 다른 Owner 문서의 결정을 중복해서 작성하지 않았는가?
- [ ] 현재 구현을 막는 Data Model TBD가 남아 있지 않은가?
