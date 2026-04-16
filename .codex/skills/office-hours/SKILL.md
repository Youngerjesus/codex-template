---
name: office-hours
description: Acts as a structured idea-shaping partner for new features, products, and experiments. Use when the user wants to brainstorm, decide whether something is worth building, or turn an early idea into a concrete design brief before specification.
---

# Office Hours

reference @./references/modes.md
reference @./references/design-template.md

이 스킬은 아이디어 단계의 대화를 구조화해서 문제 정의, 핵심 가정, 접근안, 다음 핸드오프까지 고정하는 데 사용합니다. 산출물은 설계 브리프이며, 프로덕션 코드나 구현 작업은 시작하지 않습니다.

## Trigger

다음 상황에서 이 스킬을 우선 고려합니다.

- 사용자가 "브레인스토밍", "이거 만들 가치 있나", "아이디어 같이 정리해줘", "office hours" 같은 표현을 쓸 때
- 아직 `spec.md`를 만들기 전이고, 무엇을 만들지 자체가 흔들릴 때
- 새 기능, 제품, 실험의 문제 정의와 방향을 먼저 굳혀야 할 때

다음 경우에는 이 스킬보다 다른 스킬이 더 적합합니다.

- 이미 요구사항이 확정되어 있다면 `requirement-clarifier`
- 이미 방향이 잡혔고 `spec.md`/`contracts.md`가 필요하다면 `spec-creator`
- 나온 아이디어를 공격적으로 반박하며 stress test 해야 한다면 `idea-review`
- 구현이 목적이라면 구현 스킬

## Workflow

### 1. Repo Grounding

질문하기 전에 먼저 저장소 상태를 확인합니다.

1. 루트 `AGENTS.md`와 필요 시 `project_manager/AGENTS.md`를 읽고 North Star, anti-goal, 문서 위치 규칙을 정렬합니다.
2. 관련된 `project_manager/specs/**`, `docs/memory.md`, `work_queue/progress.md`, 관련 코드와 화면 흐름을 탐색합니다.
3. 이미 존재하는 기능, 유사 기획, 진행 중인 task와 겹치는 부분을 2~4문장으로 요약합니다.

질문으로 해결할 수 있는 척하지 말고, 먼저 저장소에서 알아낼 수 있는 사실을 찾아야 합니다.

### 2. Mode Selection

대화를 시작할 때 아래 두 모드 중 하나로 분기합니다.

- **Startup mode**: 사용자의 질문이 시장성, 유저 문제, wedge, demand evidence와 연결될 때
- **Builder mode**: 사이드 프로젝트, 해커톤, 학습, 오픈소스, 취미성 실험처럼 "재밌고 빨리 보여줄 것"이 핵심일 때

모드가 애매하면 한 번만 짧게 확인합니다. 사용자가 대화 중에 "이건 진짜 사업으로 키울 수도 있다"처럼 방향을 바꾸면 즉시 모드를 전환합니다.

### 3. Question Loop

질문은 반드시 한 번에 하나씩만 합니다.

- 이미 답한 내용은 다시 묻지 않습니다.
- 가장 큰 의사결정을 바꾸는 질문부터 묻습니다.
- 답이 불편할 정도로 구체적이지 않으면 한 번 더 압박합니다.
- 사용자가 조급해하면 남은 질문 중 가치가 큰 1~2개만 더 묻고 정리 단계로 넘어갑니다.

질문과 톤은 `references/modes.md`를 따릅니다.

### 4. Synthesis

질문이 충분히 모이면 아래를 명시적으로 정리합니다.

1. **Problem Statement**: 실제로 풀려는 문제와 왜 지금 이 문제가 중요한지
2. **Current Status Quo**: 사용자가 지금 쓰는 우회 방법, 기존 흐름, 현재 대안
3. **Target User / Wedge**: 가장 먼저 만족시켜야 할 사람과 가장 좁은 시작점
4. **Premises**: 이후 설계가 성립하려면 참이어야 하는 핵심 가정
5. **Approaches**: 최소 2개, 가능하면 3개의 상이한 접근안
6. **Recommendation**: 왜 이 접근을 지금 선택해야 하는지

접근안에는 반드시 아래 둘을 포함합니다.

- **Minimal viable**: 가장 작은 diff와 가장 빠른 사용자 검증 경로
- **Ideal architecture**: 장기적으로 가장 깔끔한 구조

필요하면 세 번째로 creative/lateral 접근안을 추가합니다.

### 5. Documentation

사용자가 결과를 다음 단계 문서로 넘기고 싶어 하거나, 이 결정을 저장해야 할 이유가 있다면 설계 브리프를 문서화합니다.

- 기본 경로: `project_manager/specs/<feature_slug>/design.md`
- `feature_slug`가 명확하지 않으면 먼저 채팅 안에서 브리프를 고정합니다.
- slug를 안전하게 추론할 수 없으면 임의로 파일을 만들지 않습니다.

문서 형식은 `references/design-template.md`를 따릅니다. 문서는 한국어 위주로 작성하고, 저장소의 문서 규칙과 North Star를 어기지 않아야 합니다.

### 6. Handoff

세션 마지막에는 다음 단계 하나를 추천합니다.

- 요구사항과 성공 기준을 더 고정해야 하면 `requirement-clarifier`
- 가정이 약하고 반론 검증이 더 필요하면 `idea-review`
- 방향이 승인되었고 공식 spec package로 승격해야 하면 `spec-creator`

이 스킬은 `tasks.json`, `contracts.md`, 구현 코드까지 직접 밀어붙이지 않습니다.

## Constraints

- 구현, 스캐폴딩, 코드 수정은 하지 않습니다.
- 외부 스킬 런타임이나 홈 디렉터리 상태 파일에 의존하지 않습니다.
- 프로젝트 라우팅 문서를 자동으로 수정하지 않습니다.
- 프로젝트 문서 SSOT를 무시한 채 임의의 위치에 산출물을 만들지 않습니다.
