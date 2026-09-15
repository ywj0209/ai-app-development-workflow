# AI App Development Workflow

**Status:** Draft  
**Scope:** AI-assisted app and web product development workflow

---

## 1. Purpose

이 문서는 AI를 활용해 앱·웹 등의 소프트웨어 제품을 개발할 때 사용하는 공통 개발 Workflow를 정의한다.

목표는 두 가지 극단을 피하는 것이다.

```text
설계 없이 바로 구현
←──────────────→
구현 전에 모든 것을 상세 설계
```

이 Workflow는 그 중간에서 다음 원칙을 사용한다.

> **변경 비용이 큰 결정만 먼저 최소한으로 고정하고, 세부 결정은 실제로 필요한 시점까지 미룬다.**

이후 작은 Feature 단위로 다음 Loop를 반복한다.

```text
Plan
↓
Implement
↓
Verify
↓
Run
↓
Learn
↓
Update
```

이 문서는 **개발 방법과 단계**만 관리한다.

- 문서 작성 공통 규칙 → `DOCUMENTATION_RULES.md`
- 실제 문서 구조 → `templates/`
- AI 실행 지시 → `prompts/`
- 실제 적용 사례 → `examples/`
- 특정 제품의 결정 → 해당 Project Repository

---

## 2. Core Principles

모든 프로젝트는 다음 원칙을 기본으로 따른다.

1. 변경 비용이 큰 결정만 먼저 Baseline으로 고정한다.
2. 하나의 결정은 하나의 Owner 문서에서 관리한다.
3. 지금 필요하지 않은 결정은 `TBD`로 둘 수 있다.
4. MVP의 포함 범위뿐 아니라 제외 범위도 관리한다.
5. Implementation Backlog는 작은 구현 단위로 나눈다.
6. 모든 Feature를 프로젝트 시작 시 상세 설계하지 않는다.
7. Global Decision 변경은 해당 Owner Baseline에서 먼저 처리한다.
8. Implementer는 현재 Feature 범위를 임의로 확장하지 않는다.
9. 미래 요구사항을 위한 과설계를 하지 않는다.
10. 코드 생성만으로 `DONE` 처리하지 않는다.
11. 실제 실행에서 얻은 결과를 코드와 문서에 다시 반영한다.
12. AI 대화가 아니라 Repository 문서를 Source of Truth로 사용한다.

문서 책임과 중복 관리의 세부 규칙은 `DOCUMENTATION_RULES.md`를 따른다.

---

## 3. Workflow Overview

전체 Workflow는 네 단계로 구성된다.

```text
A. Project Baseline
   큰 결정 확정

B. Implementation Planning
   구현 단위·순서·개발 규칙 준비

C. Feature Planning Gate
   현재 Feature에 필요한 결정만 확정

D. Feature Development Loop
   구현 → 검증 → 실행 → 수정 → DONE
```

전체 흐름:

```text
Project Idea
↓
Project Baseline
↓
Implementation Backlog
↓
Project CLAUDE.md
↓
Next READY Item
↓
Feature Spec Needed?
├─ NO ───────────────────┐
└─ YES → Feature Planning
            ↓
      Baseline Impact
            ↓
            └────────────┐
                         ↓
                    IN_PROGRESS
                         ↓
                   Implementation
                         ↓
              Automated Verification
                         ↓
                    Diff Review
                         ↓
               Runtime Verification
                         ↓
                  Problem Found?
                 ↙              ↘
               YES              NO
                ↓                ↓
        Classify & Update       DONE
                ↓                ↓
             Re-verify       Next Item
```

---

## 4. Phase A — Project Baseline

### 4.1 Purpose

Baseline의 목적은 모든 세부 기능을 미리 설계하는 것이 아니다.

여러 Feature에 영향을 주고 나중에 변경 비용이 큰 **Global Decision**을 먼저 정하는 것이다.

대표적인 대상:

- MVP 목표와 범위
- 사용자 제품의 상위 구조
- 관리자·운영 구조
- Architecture
- 핵심 Data Entity와 관계
- 주요 State와 Lifecycle
- 중요한 권한 정책

### 4.2 Baseline Document Set

Workflow는 다음 문서를 기본 후보로 제공한다.

| 문서 | Primary Responsibility |
|---|---|
| `MVP_BASELINE.md` | MVP 목표와 포함·제외 범위 |
| `USER_APP_STRUCTURE.md` | 사용자용 제품의 상위 구조와 주요 흐름 |
| `ADMIN_STRUCTURE.md` | 관리자·운영 제품의 상위 구조와 주요 흐름 |
| `ARCHITECTURE_BASELINE.md` | 시스템 구성과 주요 기술 경계 |
| `DATA_MODEL_BASELINE.md` | 핵심 데이터의 의미·관계·State·Lifecycle |

모든 프로젝트가 모든 문서를 작성해야 하는 것은 아니다.

예를 들어 관리자 기능이 없다면 `ADMIN_STRUCTURE.md`를 생략할 수 있다.

기존 Baseline으로 관리하기 어려울 정도로 독립적이며 여러 Feature에 반복적으로 영향을 주는 Global Decision 영역이 있다면 추가 Baseline을 만들 수 있다.

새 문서를 만드는 기준은 `DOCUMENTATION_RULES.md`의 Document Creation Gate를 따른다.

### 4.3 Owner Rule

하나의 결정은 하나의 Owner 문서가 관리한다.

예:

```text
MVP 범위
→ MVP_BASELINE.md

사용자 제품 상위 구조
→ USER_APP_STRUCTURE.md

시스템 경계
→ ARCHITECTURE_BASELINE.md

핵심 Data 관계와 Lifecycle
→ DATA_MODEL_BASELINE.md
```

Feature Spec이나 다른 문서에서 같은 결정을 다시 정의하지 않는다.

### 4.4 TBD Rule

현재 구현에 필요하지 않은 결정은 `TBD`로 남길 수 있다.

`TBD`는 잘못된 상태가 아니라 불필요한 선행 결정을 피하기 위한 상태다.

다만 현재 Feature 구현에 필요한 `TBD`는 구현 전에 해결해야 한다.

### 4.5 Implementation Details Stay Out

제품 동작이나 Global Structure에 영향을 주지 않는 기술 세부사항은 Baseline에서 기본적으로 결정하지 않는다.

예:

- 함수명
- 변수명
- 파일명
- Component 내부 구조
- 구체적인 SQL 구현
- 작은 Local Refactor 방식

이러한 사항은 확정된 제품 동작과 Architecture를 지키는 범위에서 구현 단계에 결정한다.

---

## 5. Phase B — Implementation Planning

Baseline이 필요한 수준까지 준비되면 모든 Feature Spec을 만드는 대신 실제 구현 계획을 세운다.

### 5.1 Implementation Backlog

`IMPLEMENTATION_BACKLOG.md`는 다음을 관리한다.

- 무엇을 구현할 것인가
- 어떤 순서로 구현할 것인가
- 선행 작업은 무엇인가
- 현재 상태는 무엇인가

기본 상태:

```text
TODO
READY
IN_PROGRESS
BLOCKED
DONE
```

구체적인 작성 구조는 `IMPLEMENTATION_BACKLOG_TEMPLATE.md`가 관리한다.

### 5.2 Small Backlog Items

Backlog Item은 가능한 한:

> **한 번의 Planning → Implementation → Verification → Execution → Fix Loop에서 끝낼 수 있는 크기**

로 나눈다.

너무 크다면 더 작은 Feature 또는 Task로 분리한다.

### 5.3 End-to-End First

Backlog 순서는 단순히 기술적으로 편한 순서만으로 정하지 않는다.

가능하면 제품의 핵심 가치를 처음부터 끝까지 확인할 수 있는 **가장 단순한 End-to-End Flow**를 먼저 완성한다.

> 기능 수를 늘리는 것보다 핵심 가치가 실제로 동작하는 한 줄의 흐름을 먼저 만든다.

복잡한 자동화, 최적화, 편의 기능은 핵심 흐름이 작동한 뒤 추가하는 것을 기본으로 한다.

### 5.4 Prepare Project Implementation Rules

첫 구현을 시작하기 전에 Project Repository에 `CLAUDE.md`를 준비한다.

`CLAUDE.md`는 `CLAUDE_TEMPLATE.md`를 기준으로 해당 프로젝트에서 Claude Code가 따라야 할 행동 규칙을 정의한다.

Workflow는 **언제 `CLAUDE.md`가 필요한지**를 정의한다.

실제 규칙 구조는 `CLAUDE_TEMPLATE.md`가 관리한다.

---

## 6. Phase C — Feature Planning Gate

`READY` Item을 선택했다고 항상 바로 구현하지 않는다.

현재 Item에 상세 Feature Planning이 필요한지 먼저 판단한다.

```text
READY Item
↓
Feature Spec Needed?
├─ NO  → Implementation
└─ YES → Feature Planning
          ↓
      Baseline Impact
          ↓
      Implementation
```

### 6.1 Feature Spec Required

다음과 같은 제품 결정이 필요한 경우 Feature Spec 작성을 기본으로 한다.

- 사용자 또는 관리자 행동
- State 변화
- Permission
- 입력 및 Validation
- 예외 처리
- 여러 화면 또는 Data의 연결
- 제품 정책 판단

Feature Spec의 실제 작성 구조는 `FEATURE_SPEC_TEMPLATE.md`가 관리한다.

### 6.2 Feature Spec May Be Skipped

제품 정책 판단이 거의 없는 단순 Setup 또는 명확한 기술 작업은 Feature Spec 없이 구현할 수 있다.

예:

- 프로젝트 기본 구조 생성
- 앱 기본 실행
- Package Manager 구성
- 이미 확정된 외부 서비스 연결
- 환경 설정

단순 작업처럼 보여도 새로운 제품 결정이 필요해지면 Feature Planning으로 돌아간다.

### 6.3 Current Feature Only

상세 기획은 현재 구현하려는 Feature에 필요한 범위까지만 한다.

다음 Backlog Item까지 미리 상세 설계하지 않는다.

### 6.4 Baseline Impact Check

Feature Planning 후 현재 계획이 기존 Global Decision에 영향을 주는지 확인한다.

기본 확인 대상:

```text
MVP Baseline
User Structure
Admin Structure
Architecture
Data Model
Additional Project Baselines
```

영향이 없다면 구현한다.

Global Decision 변경이 필요하면:

```text
Feature Planning
↓
Baseline Change Detected
↓
Stop Implementation
↓
Review Impact
↓
Product Decision
↓
Update Owner Baseline
↓
Update Current Feature Spec
↓
Implementation
```

Feature Spec이 Baseline을 암묵적으로 재정의해서는 안 된다.

---

## 7. Roles & Decision Rights

### 7.1 Planner / Reviewer

Planning은 특정 AI에 종속되지 않는다.

GPT, Claude 또는 다른 적절한 Planning Tool을 사용할 수 있다.

주요 역할:

- 제품 범위 논의
- Baseline 작성·검토
- Feature Planning
- 문서 충돌 검토
- Baseline Impact 판단
- 구현 결과 해석

어떤 AI가 제안했는지보다 **최종 결정이 올바른 Owner 문서에 기록되었는지**가 중요하다.

### 7.2 Implementer

기본 Implementer는 Claude Code다.

주요 역할:

- 실제 Repository 확인
- 코드 구현
- 필요한 Migration 및 Test 구현
- 프로젝트가 지원하는 검증 실행
- Diff 확인
- 구현 결과 보고

Implementer는 제품 결정자가 아니다.

### 7.3 Product Decisions

다음과 같은 결정은 Implementer가 임의로 변경하지 않는다.

- 새 Feature
- MVP 범위
- 중요한 제품 정책
- 핵심 State
- 핵심 Entity 및 관계
- Architecture
- 중요한 권한 정책
- Data Lifecycle
- 중요한 UX Flow

새로운 Product Decision이 필요하면 Planning 단계로 올린다.

### 7.4 Implementation Decisions

확정된 제품 동작과 Baseline을 변경하지 않는 구현 세부사항은 Implementer가 Repository를 보고 결정할 수 있다.

예:

- 함수명
- 변수명
- 파일명
- 작은 함수 분리
- Component 내부 구조
- 동일 동작을 만드는 구체적인 구현 방식
- 작은 Local Refactor
- 필요한 최소 Test 구조

---

## 8. Phase D — Feature Development Loop

### 8.1 Start

작업을 시작하면:

```text
READY
↓
IN_PROGRESS
```

로 변경한다.

기본적으로 하나의 Feature Loop를 완료한 뒤 다음 Feature로 이동한다.

병렬 구현이 필요하다면 프로젝트에서 독립적인 Workstream을 명시적으로 정의해야 한다.

### 8.2 Minimum Required Context

Implementer에게 매번 모든 Project 문서를 읽히지 않는다.

기본 Context:

```text
CLAUDE.md
+
현재 Feature 관련 Baseline
+
현재 Feature Spec
+
필요한 Backlog 정보
```

현재 작업에 직접 필요하지 않은 문서를 불필요하게 Context에 포함하지 않는다.

### 8.3 Implement Current Scope Only

Implementer는 현재 Backlog Item의 Scope만 구현한다.

다음 Feature를 미리 구현하지 않는다.

미래 확장을 이유로 불필요한 Entity, Infrastructure, Layer 또는 Refactor를 추가하지 않는다.

### 8.4 Automated Verification

구현 후 Repository가 실제로 지원하는 검증을 실행한다.

예:

```text
Build
Typecheck
Lint
Test
```

검증 상태는 `DOCUMENTATION_RULES.md`의 정의를 따른다.

```text
PASS
FAIL
NOT_RUN
BLOCKED
```

실행하지 않은 검증을 `PASS`로 처리하지 않는다.

### 8.5 Diff Review

구현 후 Repository Diff를 확인한다.

최소 확인 대상:

- 요청하지 않은 파일 변경
- 현재 Scope 밖의 구현
- 다음 Feature 선행 구현
- 핵심 Entity의 임의 추가
- Architecture의 임의 변경
- 불필요한 추상화
- 관련 없는 Refactor
- Secret 또는 민감한 값 포함

### 8.6 Runtime Verification

사용자에게 보이거나 실제 Runtime에서 동작하는 Feature는 가능한 실제 환경에서 핵심 Scenario를 확인한다.

목적은 두 가지다.

```text
구현이 실제로 동작하는가?
+
기획한 동작 자체가 적절한가?
```

필요한 환경이 없어 실행하지 못한 경우 성공으로 추정하지 않는다.

- 단순 미실행 → `NOT_RUN`
- 외부 조건 등으로 수행 불가 → `BLOCKED`

현재 Feature의 핵심 Scenario 검증이 필수인데 `FAIL`, `NOT_RUN` 또는 `BLOCKED` 상태라면 기본적으로 `DONE` 처리하지 않는다.

프로젝트가 예외적인 완료 기준을 사용해야 한다면 해당 Project 문서에서 명시적으로 정의한다.

---

## 9. Problem Handling & Definition of Done

### 9.1 Implementation Problem

기획은 맞지만 코드가 잘못된 경우다.

```text
Code Fix
↓
Verification
↓
Runtime Verification
```

### 9.2 Feature Planning Problem

현재 Feature의 제품 동작이 잘못되었거나 충분히 정의되지 않은 경우다.

```text
Review Feature Spec
↓
Make Required Decision
↓
Update Feature Spec
↓
Update Code
↓
Re-verify
```

### 9.3 Baseline Problem

문제가 현재 Feature보다 상위의 Global Decision에 영향을 준다면 해당 Owner Baseline까지 올라간다.

```text
Problem
↓
Determine Impact Level
↓
Find Owner
↓
Update Owner Baseline
↓
Update Related Feature Documentation
↓
Update Code
↓
Re-verify
```

### 9.4 Definition of Done

Implementer의 “구현 완료” 보고만으로 `DONE` 처리하지 않는다.

기본 완료 조건:

```text
Implementation Complete
+
Required Verification Complete
+
Diff Reviewed
+
Required Runtime Scenario Verified
+
Discovered Problems Resolved
+
Required Documentation Synchronized
```

필수 검증에 해결되지 않은 `FAIL` 또는 `BLOCKED`가 남아 있으면 기본적으로 `DONE`이 아니다.

조건이 충족되면:

```text
IN_PROGRESS
↓
DONE
```

으로 변경하고 다음 Backlog Item으로 이동한다.

---

## 10. Documentation, Git & Feedback

### 10.1 Repository Source of Truth

확정된 결정은 AI 대화에만 남기지 않는다.

```text
Discuss
↓
Decide
↓
Update Owner Document
↓
Implement
```

새 AI 대화나 새로운 Coding Agent Session은 이전 채팅 기억보다 Repository 문서를 기준으로 프로젝트를 이해한다.

### 10.2 Change Ownership

변경이 생기면 해당 결정의 Owner만 우선 수정한다.

동일한 내용을 여러 문서에 복사하지 않는다.

세부 규칙은 `DOCUMENTATION_RULES.md`를 따른다.

### 10.3 Git

확정된 문서와 구현 코드는 Git Repository에서 함께 관리한다.

```text
Decision
↓
Documentation Update
↓
Implementation
↓
Verification
↓
Diff Review
↓
Commit
```

Git을 통해 다음을 추적할 수 있어야 한다.

- 어떤 결정이 언제 변경되었는가
- 어떤 Feature가 언제 구현되었는가
- 문서와 코드가 어떻게 함께 변경되었는가

### 10.4 Feedback Loop

개발은 다음과 같은 일방향 과정이 아니다.

```text
Planning
↓
Documentation
↓
Implementation
↓
Execution
↓
Problem / Learning
↓
Decision
↓
Documentation or Code Update
↓
Re-execution
```

Baseline은 전체 구조를 안정적으로 유지한다.

Feedback Loop는 실제 경험을 통해 세부사항을 계속 정확하게 만든다.

---

## 11. Workflow Evolution

### 11.1 Project Problem vs Workflow Problem

프로젝트에서 문제를 발견했다고 모두 중앙 Workflow에 반영하지 않는다.

판단 기준:

> **다른 프로젝트에서도 같은 문제가 반복될 가능성이 높은가?**

특정 제품에만 해당하면:

```text
Project Repository 수정
```

여러 프로젝트에서 반복될 개발 방식의 문제라면:

```text
Workflow Repository 개선 후보
```

로 본다.

### 11.2 Workflow Update

재사용 가능한 개선이 확정되면 문제의 Owner에 따라 수정한다.

```text
개발 방법
→ WORKFLOW.md

문서 작성 규칙
→ DOCUMENTATION_RULES.md

문서 구조
→ templates/

AI 실행 지시
→ prompts/

Claude Code 행동 규칙
→ CLAUDE_TEMPLATE.md
```

필요한 변경을 완료한 뒤:

```text
CHANGELOG.md
↓
VERSION
```

을 갱신한다.

### 11.3 Existing Projects

새 Workflow Version을 기존 Project에 자동 적용하지 않는다.

기존 Project는 필요한 변경만 검토 후 선택적으로 적용한다.

각 Project Repository는 **자신이 채택한 Workflow Version을 식별할 수 있어야 한다.**

구체적인 기록 방식은 Project 시작 관련 Template에서 정의한다.

---

## 12. Final Operating Rule

이 Workflow의 전체 운영 원칙은 다음과 같다.

```text
큰 결정만 먼저 고정
↓
작은 Backlog 작성
↓
현재 Feature만 필요한 만큼 기획
↓
Baseline Impact 확인
↓
현재 Scope만 구현
↓
검증 + Diff + 실제 실행
↓
문제의 Owner를 찾아 수정
↓
DONE
↓
다음 Feature
```

> **충분한 구조를 먼저 만들되, 실제 구현 전에 모든 것을 결정하지 않는다.  
> 작은 Feature를 빠르게 구현하고 실행하면서 제품과 문서를 함께 정확하게 만든다.**
