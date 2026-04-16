---
name: plan-ceo-review
description: Reviews a feature plan in founder-mode. Use when the user wants to rethink scope, challenge premises, test ambition, or pressure a plan toward a sharper product strategy before implementation.
---

# Plan CEO Review

reference @./references/review-modes.md
reference @./references/review-template.md

이 스킬은 구현 전 계획을 제품/전략 관점에서 다시 검토하는 리뷰 스킬입니다. 목표는 계획을 승인하는 것이 아니라, 문제 정의와 범위를 다시 생각해 더 좋은 제품 방향으로 밀어 올리거나, 반대로 과한 범위를 잘라내는 것입니다.

이 스킬은 코드를 작성하지 않습니다. 필요할 때 문서를 갱신하더라도 범위는 `project_manager/specs/<feature_slug>/plan_review.md`와 관련 기획 문서 정리에 한정합니다.

## Trigger

다음 상황에서 이 스킬을 우선 고려합니다.

- 사용자가 "더 크게 생각해봐", "이 정도로 충분히 야심차나?", "strategy review", "scope 다시 보자", "이 plan 맞나?"라고 할 때
- `design.md`, `plan.md`, `tasks.md`, `spec.md`는 있는데 방향 자체에 확신이 없을 때
- 구현 전에 scope expansion, selective expansion, hold scope, scope reduction 중 어떤 기조로 갈지 결정해야 할 때

다음 경우에는 다른 스킬이 더 적합할 수 있습니다.

- 문제 정의가 아직 흐리면 `office-hours`
- 아이디어 자체를 찢어보는 논쟁이 목적이면 `idea-review`
- 요구사항/계약 명세를 고정해야 하면 `requirement-clarifier` 또는 `spec-creator`
- 아키텍처/테스트 중심 검토면 차후 `plan-eng-review`

## Core Posture

- 리뷰의 목적은 "좋아 보입니다"가 아니라, 더 직접적인 문제 정의와 더 좋은 사용자 결과를 찾는 것입니다.
- 범위를 늘리거나 줄이는 판단은 절대 묵시적으로 하지 않습니다. 사용자가 명시적으로 승인한 범위만 새 기준이 됩니다.
- 드림 빌드와 현실 빌드를 분리해서 보여줍니다. 둘을 섞어 흐리지 않습니다.
- 구체성이 부족한 문장은 통과시키지 않습니다. "더 좋아진다"가 아니라 무엇이, 누구에게, 어떻게 좋아지는지 적습니다.

## Workflow

### 1. System Audit

먼저 저장소와 현재 계획 문서를 읽고 사실관계를 고정합니다.

1. 루트 `AGENTS.md`와 필요 시 `project_manager/AGENTS.md`를 읽습니다.
2. 관련 `project_manager/specs/<feature_slug>/` 아래의 `design.md`, `plan.md`, `tasks.md`, `spec.md`, `contracts.md`, `review.md`, `plan_review.md`를 탐색합니다.
3. `docs/memory.md`, `docs/design/memory.md`, 관련 코드, 최근 진행 로그를 읽어 현재 시스템 상태와 중복 위험을 파악합니다.
4. 이미 존재하는 흐름, 재사용 가능한 구조, 과거 retry/review에서 반복된 문제를 짧게 요약합니다.

`office-hours`가 남긴 `design.md`가 있으면 문제 정의와 접근안의 1차 SSOT로 취급합니다. 없다면 현재 `spec.md`/`plan.md`를 기준으로 리뷰하되, 문제 정의가 흐리면 먼저 그 사실을 명시합니다.

### 2. Mode Selection

리뷰는 반드시 아래 네 모드 중 하나로 고정합니다.

- **SCOPE EXPANSION**: 더 큰 제품 기회를 적극적으로 제안하고, 확장 항목을 사용자가 하나씩 승인하게 합니다.
- **SELECTIVE EXPANSION**: 현재 범위를 baseline 으로 두고, 추가 기회를 후보로만 제시합니다.
- **HOLD SCOPE**: 범위를 유지한 채 리스크, 누락, edge case, observability 를 강화합니다.
- **SCOPE REDUCTION**: 핵심 사용자 가치만 남기고 나머지를 잘라냅니다.

사용자가 명시하지 않았다면 아래 기본값으로 제안합니다.

- 신규 사용자 기능: `SELECTIVE EXPANSION`
- 큰 신기능, 사업 방향 전환: `SCOPE EXPANSION`
- 버그 수정, 핫픽스, 구현 정합성 점검: `HOLD SCOPE`
- 과도한 diff, 일정 압박, refactor fatigue: `SCOPE REDUCTION`

### 3. Step 0 Review

본 리뷰를 시작하기 전에 아래 네 가지를 반드시 정리합니다.

1. **Premise challenge**: 이 계획이 진짜 문제를 푸는지, 아니면 proxy 문제를 푸는지
2. **Existing leverage**: 기존 코드/문서/흐름 중 무엇을 그대로 활용할 수 있는지
3. **12-month ideal**: 지금 계획이 1년 뒤의 이상적인 시스템으로 가는 길인지
4. **Alternatives**: 최소 2개의 대안과 추천안

대안은 아래 둘을 반드시 포함합니다.

- **Minimal viable**: 최소 diff, 최소 moving part
- **Ideal architecture**: 가장 일관되고 장기적으로 확장 가능한 형태

필요하면 세 번째 creative/lateral 대안을 추가합니다.

### 4. Mode-Specific Review

세부 규칙은 `references/review-modes.md`를 따릅니다.

- `SCOPE EXPANSION`: 10x version, platonic ideal, delight opportunity 를 발굴합니다.
- `SELECTIVE EXPANSION`: baseline 을 고정한 뒤 cherry-pick 가능한 확장만 분리합니다.
- `HOLD SCOPE`: 범위를 늘리지 않고 구조, 리스크, 테스트, 운영 가능성을 강화합니다.
- `SCOPE REDUCTION`: core outcome 만 남기고 나머지를 defer 합니다.

확장 또는 축소가 필요해도 사용자 승인 전에는 문서 scope 를 바꾸지 않습니다.

### 5. Review Sections

아래 항목을 빠뜨리지 말고 검토합니다. 단, 과도한 의식이나 부수 절차를 늘리지 말고 현재 저장소 맥락에 맞게 압축해서 작성합니다.

1. **Architecture**: 컴포넌트 경계, 데이터 흐름, 상태 변화, 재사용성
2. **Error and rescue**: 어떤 흐름이 어떻게 실패할 수 있고, 사용자와 운영자가 무엇을 보게 되는지
3. **Security and trust**: 입력 검증, 권한 경계, 민감 데이터, 내부용 경로 오남용
4. **Data and interaction edge cases**: nil/empty/error/stale/concurrent path 와 UI edge case
5. **Quality and complexity**: 중복, 과설계, 누락된 defensive logic, naming clarity
6. **Tests**: happy path, failure path, hostile edge case, regression scope
7. **Performance**: query, payload size, retry amplification, background work, bottleneck
8. **Observability**: logs, metrics, traces, operational proof
9. **Deployment and rollback**: migration safety, rollout order, rollback path, post-deploy checks
10. **Long-term trajectory**: 6-12개월 뒤 debt, path dependency, reversibility
11. **Design and UX**: 사용자 화면이 관련되면 IA, state coverage, mobile, accessibility, trust

모든 섹션에서 중요한 누락은 다음 세 가지 레이블 중 하나로 정리합니다.

- **CRITICAL GAP**: 구현 전에 닫지 않으면 실패 가능성이 큰 문제
- **WARNING**: 계획 단계에서 정리하는 편이 좋은 문제
- **OK**: 현재 계획으로도 충분히 설명되거나 커버된 항목

### 6. Questions and Decisions

질문은 한 번에 하나씩만 합니다.

- 진짜 trade-off 가 있을 때만 사용자에게 묻습니다.
- obvious fix 면 질문하지 말고 권고안으로 적습니다.
- 각 질문은 "무엇이 문제인지", "선택지", "추천안"이 분명해야 합니다.
- 확장/축소 제안은 각각 독립된 결정으로 다룹니다.

### 7. Documentation Output

리뷰 결과를 저장해야 하거나 기존 spec package 가 이미 존재한다면 다음 문서를 사용합니다.

- 기본 산출물: `project_manager/specs/<feature_slug>/plan_review.md`
- 관련 기획 방향까지 바뀌면 `design.md`와 `plan.md` 업데이트 필요성을 같이 명시합니다.
- 임의의 홈 디렉터리 로그나 별도 CEO 플랜 저장소는 사용하지 않습니다.

`plan_review.md`에는 다음을 반드시 포함합니다.

- Mode selected
- What already exists
- Not in scope
- Dream state delta
- Error & rescue registry
- Failure modes registry
- 권고안과 열린 결정 사항

상세 형식은 `references/review-template.md`를 따릅니다.

### 8. Handoff

리뷰가 끝나면 다음 액션 하나를 추천합니다.

- 전략이 정리됐고 구현 명세를 더 잠가야 하면 `plan-eng-review` 또는 `spec-creator`
- 아직 문제 정의가 흔들리면 `office-hours`
- 반론 검증이 더 필요하면 `idea-review`

## Constraints

- 구현, 스캐폴딩, 코드 수정은 하지 않습니다.
- 외부 런타임이나 홈 디렉터리 아티팩트에 의존하지 않습니다.
- 프로젝트 라우팅 문서나 글로벌 설정 파일을 자동으로 수정하지 않습니다.
- 현재 저장소의 spec package 규칙을 벗어난 임의 위치에 리뷰 산출물을 만들지 않습니다.
