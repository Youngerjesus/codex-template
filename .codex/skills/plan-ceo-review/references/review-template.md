# Plan CEO Review Template

`plan-ceo-review`가 문서 산출물을 남길 때 사용하는 기본 템플릿입니다.

- 기본 경로: `project_manager/specs/<feature_slug>/plan_review.md`
- 목적: 구현 전에 전략/범위/리스크를 압축해서 남기는 것
- 언어: 한국어 위주

```md
# Plan Review: <feature title>

**Status**: Draft
**Mode**: Scope Expansion | Selective Expansion | Hold Scope | Scope Reduction
**Related Package**: `project_manager/specs/<feature_slug>/`

## Executive Summary
- 현재 계획의 강점과 가장 큰 리스크를 3~5줄로 요약
- 이번 리뷰의 핵심 권고안 1개

## What Already Exists
- 기존 코드, 문서, 흐름 중 재사용 가능한 것
- 이번 계획이 새로 만들지 않아도 되는 부분

## Premise Challenge
- 이 계획이 진짜 풀고 있는 문제
- proxy 문제 가능성
- 아무것도 안 했을 때의 결과

## Dream State Delta
| Current State | This Plan | 12-Month Ideal |
| --- | --- | --- |
| <state> | <delta> | <target> |

## Alternatives
### Approach A: <name>
- 요약
- 장점
- 단점
- 추천 여부

### Approach B: <name>
- 요약
- 장점
- 단점
- 추천 여부

### Approach C: <name> (optional)
- 의미 있게 다를 때만 작성

## Review Findings
### Architecture
- `CRITICAL GAP` / `WARNING` / `OK`

### Error And Rescue
- 어떤 흐름이 실패할 수 있는지
- 어떤 실패가 아직 silent 인지

### Security And Trust
- 권한, 입력, 민감정보, 내부 경계

### Data And Interaction Edge Cases
- nil, empty, error, stale, concurrent, mobile, back-button 등

### Tests
- 꼭 필요한 happy/failure/regression/hostile test

### Observability And Deploy
- 로그, 메트릭, rollout, rollback, post-deploy 확인

## Error & Rescue Registry
| Codepath | Failure Mode | Rescued? | User Sees | Logged? | Test? |
| --- | --- | --- | --- | --- | --- |
| <path> | <mode> | Y/N | <impact> | Y/N | Y/N |

## Not In Scope
- 이번 리뷰에서 의도적으로 제외한 항목과 이유

## Open Decisions
- 아직 사용자가 결정해야 하는 것
- 후속 리뷰로 넘길 질문

## Recommended Next Step
- `plan-eng-review`, `office-hours`, `idea-review`, `spec-creator` 중 하나
- 왜 이 단계가 다음이어야 하는지
```

## Writing Notes

- 체크리스트만 복사하지 말고, 이 기능에 실제로 해당하는 리스크만 적습니다.
- "에러 처리 필요" 같은 추상어를 쓰지 말고 어떤 실패인지 이름 붙입니다.
- `Not in scope`는 반드시 씁니다. 뺀 이유가 곧 제품 판단의 핵심입니다.
- 확장안이 승인되면 그 항목이 baseline 을 어떻게 바꾸는지 문서에 반영합니다.
