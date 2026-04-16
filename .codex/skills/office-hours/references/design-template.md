# Office Hours Design Template

`office-hours` 스킬이 설계 브리프를 파일로 남겨야 할 때 사용하는 최소 템플릿입니다.

- 기본 저장 경로: `project_manager/specs/<feature_slug>/design.md`
- 언어: 한국어 위주
- 목적: 구현 명세가 아니라 문제 정의와 방향 결정을 다음 단계 스킬로 넘기는 것

```md
# Design Brief: <title>

**Status**: Draft
**Mode**: Startup | Builder
**Related Spec Package**: `project_manager/specs/<feature_slug>/`

## Summary
- 무엇을 고민했고 어떤 방향을 추천하는지 3~5줄로 요약

## Problem Statement
- 실제로 풀고 싶은 문제
- 왜 지금 이 문제가 중요한지

## Target User And Situation
- 가장 먼저 만족시켜야 할 사람
- 그 사람이 놓인 상황과 현재 불편

## Current Status Quo
- 지금 쓰는 우회 방법, 기존 제품, 내부 운영 방식
- 왜 그것만으로는 부족한지

## Premises
- 이 설계가 성립하려면 참이어야 하는 핵심 가정
- 아직 검증되지 않은 가정은 명확히 표시

## Approaches Considered
### Approach A: <name>
- 요약
- 장점
- 단점
- 적합한 조건

### Approach B: <name>
- 요약
- 장점
- 단점
- 적합한 조건

### Approach C: <name> (optional)
- 의미 있게 다른 경로일 때만 작성

## Recommended Approach
- 지금 선택할 접근안
- 선택 이유
- 이번 단계에서 의도적으로 하지 않는 것

## Open Questions
- 아직 남아 있는 결정 사항
- 이후 검증해야 할 리스크

## Next Handoff
- 다음으로 연결할 스킬 또는 문서
- 예: `requirement-clarifier`, `idea-review`, `spec-creator`
```

## Writing Notes

- 과장된 비전 문구보다 실제 사용자와 실제 상황을 우선합니다.
- 구현 세부사항을 꾸며내지 않습니다.
- 아직 정해지지 않은 것은 미정으로 남기고, 검증해야 할 질문으로 바꿉니다.
- 문서를 읽은 다음 스킬이 바로 이어받을 수 있도록 추천 이유와 보류 이유를 같이 적습니다.
