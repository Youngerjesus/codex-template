---
name: implementation-brake
description: Post-implementation review skill for stress-testing a completed code change before calling it done. Use when code already exists and the user wants implementation-level gaps, regression risks, missing tests, rigidity, or unnecessary complexity identified and then fixed through tdd-workflow.
---

# Implementation Brake

reference @./references/review-lenses.md
reference @./references/fix-handoff.md

이 스킬은 이미 작성된 구현을 대상으로, "동작은 되는 것 같은데 진짜 안전하게 닫혔나"를 압박 검토하는 구현 전용 브레이크 스킬입니다.
기획/방향 검토가 아니라 코드, 테스트, 경계 조건, 회귀 위험, 불필요한 복잡도를 다시 보고, 기본적으로는 `tdd-workflow`를 통해 수정까지 이어갑니다.

## Trigger

다음 상황에서 이 스킬을 우선 고려합니다.

- 사용자가 "구현 허점 봐줘", "이 구현 브레이크 걸어줘", "코드 쪽에서 놓친 거 찾아줘", "구현 리뷰하고 바로 고쳐" 같은 요청을 할 때
- 구현은 끝났지만 ship 전에 correctness, regression, edge case, test gap 을 다시 압박 검토하고 싶을 때
- bounded feature, bugfix, refactor, review feedback 반영 뒤에 실제 구현 품질을 다시 확인하려고 할 때

다음 경우에는 다른 스킬이 더 적합할 수 있습니다.

- 방향 자체가 맞는지 의심되면 `decision-brake`
- 아직 무엇을 만들지 정하는 단계면 `office-hours`
- 구현 자체를 처음 시작하는 bounded code change 면 `tdd-workflow`
- 큰 멀티 마일스톤 구현 orchestration 이면 더 상위 planning 스킬

## Core Posture

- findings first 입니다. 칭찬보다 결함, 누락, 리스크를 먼저 냅니다.
- 리뷰는 실제 defect risk 중심이어야 합니다. 취향성 nitpick 은 지양합니다.
- 구현이 맞는지 판단할 때 코드와 테스트 증거를 함께 봅니다.
- accepted finding 은 가능한 빨리 `tdd-workflow`의 다음 failing test 로 환원합니다.
- broad cleanup 을 핑계로 scope 를 늘리지 않습니다.

## Workflow

### 1. Ground the implementation

먼저 아래를 짧게 고정합니다.

- 무엇을 구현한 것인지
- 어떤 동작/버그/리팩터링을 닫으려는 것인지
- 관련 코드 경계와 현재 테스트 상태가 무엇인지

필요하면 관련 diff, 테스트, 호출 경로를 읽고 현재 구현의 실제 shape 을 파악합니다.

### 2. Produce findings first

`references/review-lenses.md`를 참고해 현재 구현에서 중요한 렌즈만 사용합니다.

각 finding 은 아래를 포함해야 합니다.

- 무엇이 약한지
- 왜 실제 defect risk 인지
- 어떤 종류의 리스크인지
  - correctness
  - regression
  - edge case
  - test gap
  - maintainability
  - performance
  - security
  - architecture drift
- 무엇을 바꿔야 하는지

### 3. Decide what must be fixed now

finding 을 아래로 분리합니다.

- **must fix now**: ship 전에 닫아야 하는 결함 또는 test gap
- **can defer**: 지금 닫지 않아도 되는 개선 또는 cleanup

기본값은 보수적입니다. correctness, regression, missing failure-path coverage 는 defer 하지 않습니다.

### 4. Hand off into TDD repair

사용자가 review-only 를 명시하지 않았다면, must-fix finding 을 `references/fix-handoff.md` 규칙으로 `tdd-workflow`에 연결합니다.

핵심 원칙은 다음과 같습니다.

- finding 하나를 behavior 하나로 환원합니다.
- 가장 작은 failing test 를 먼저 씁니다.
- production code 는 red 확인 뒤에만 수정합니다.
- targeted test 후 관련 상위 스위트까지 다시 검증합니다.

### 5. Re-review after fixes

수정이 끝나면 다시 구현 검토 posture 로 돌아와 아래를 확인합니다.

- 원래 finding 이 실제로 닫혔는가
- 수정이 다른 리스크를 새로 만들지 않았는가
- broader verification 이 충분했는가

## Output Shape

응답은 아래 순서를 기본으로 합니다.

1. **Implementation under review**
2. **Findings**
3. **What must be fixed now**
4. **What can be deferred**
5. **Fix plan**
6. **Verification result**

판정은 반드시 아래 중 하나를 사용합니다.

- `[SHIP]`
- `[FIX BEFORE SHIP]`
- `[NEEDS REWORK]`

## Companion Agent

이 저장소에는 `implementation-brake-reviewer` 전용 에이전트를 둘 수 있습니다.

- 사용자가 독립된 implementation review pass 를 원하면 이 에이전트를 우선 사용합니다.
- 이 에이전트는 read-only 로 구현 결함과 test gap 을 찾는 데 집중합니다.
- 수정 단계는 이 에이전트가 직접 닫지 않고 `tdd-workflow` 흐름으로 넘깁니다.

## Constraints

- pre-implementation 의사결정 검토를 대신하지 않습니다. 그 경우 `decision-brake`를 사용합니다.
- review-only 가 아닌 이상 findings 보고에서 끝내지 않습니다.
- failing test 없는 무차별 patching 을 허용하지 않습니다.
- review cleanup 을 핑계로 큰 리팩터링을 밀어 넣지 않습니다.
