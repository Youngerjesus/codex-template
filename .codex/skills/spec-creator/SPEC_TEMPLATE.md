# Feature Specification: [기능 명칭] ([ID-예: 001-feature-name])

**Feature Branch**: `[branch-name]`
**Created**: [YYYY-MM-DD]
**Status**: Draft / In-Review / Approved

> **Notice**: [이 스펙과 관련된 전제 조건이나 타 스펙과의 경계, 혹은 히스토리에 대한 중요한 참고 사항을 적습니다.]
> reference-driven visual 작업이면 같은 패키지의 `reference-manifest.json` 과 `references/` 를 함께 정의하고, canonical screenshot / similarity / reference parity 상태를 이 스펙과 일치시킵니다.

---

## Clarifications

### Session [YYYY-MM-DD] (Updated)

| # | 주제 | 결정 사항 |
|---|------|-----------|
| Q1 | [질문/이슈] | [결정된 내용 및 아키텍처 방향] |
| Q2 | [질문/이슈] | [결정된 내용 및 아키텍처 방향] |

---

## User Scenarios & Testing *(mandatory)*

### User Story 1 - [사용자 스토리 제목] (Priority: P1)

**Acceptance Scenarios**:
1. **Given** [어떤 상황에서], **When** [사용자가 무엇을 하면], **Then** [결과가 어떻게 되어야 한다].
2. **Given** [어떤 상황에서], **When** [사용자가 무엇을 하면], **Then** [결과가 어떻게 되어야 한다].

### User Story 2 - [사용자 스토리 제목] (Priority: P1)

**Acceptance Scenarios**:
1. **Given** [어떤 상황에서], **When** [사용자가 무엇을 하면], **Then** [결과가 어떻게 되어야 한다].

---

## Requirements *(mandatory)*

### Functional Requirements
**EARS Syntax**: Requirements must follow `When [Trigger], If [Condition], the [System] Shall [Action]` structure to remove ambiguity.

**[대분류 1: 예-인증 및 보안]**
- **FR-001**: When [사용자가 로그인 요청을 보낼 때], If [인증 정보가 유효하지 않으면], the [시스템] Shall [401 Unauthorized 에러를 반환해야 한다].
- **FR-002**: When [Trigger], If [Condition], the [System] Shall [Action].

**[대분류 2: 예-데이터 처리]**
- **FR-003**: When [Trigger], If [Condition], the [System] Shall [Action].

---

## Success Criteria *(measurable)*

- **SC-001 ([핵심지표])**: [측정 가능하고 명확한 성공 기준]
- **SC-002 ([보안/성능])**: [측정 가능하고 명확한 성공 기준]

---

## Edge Cases

- **[엣지 케이스 1]**: [장애 상황이나 예외 발생 시의 시스템 대응 및 UI 피드백 방식]
- **[엣지 케이스 2]**: [장애 상황이나 예외 발생 시의 시스템 대응 및 UI 피드백 방식]

---

## Strategic Considerations & Risks

- **[고려사항/리스크 1]**: [아키텍처 설계 시 주의해야 할 점이나 외부 의존성 리스크]
- **[고려사항/리스크 2]**: [보안상 중요한 포인트나 향후 확장성을 고려한 제언]
