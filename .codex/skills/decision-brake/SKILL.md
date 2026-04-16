---
name: decision-brake
description: General-purpose pre-execution review skill for stress-testing a proposed direction, decision, plan, or idea before committing to implementation. Use when the user wants a hard second pass on logical gaps, hidden risks, stronger alternatives, subtraction opportunities, or whether the proposal is solving the real problem.
---

# Decision Brake

reference @./references/review-lenses.md

이 스킬은 구현이나 문서 작성보다 먼저, "지금 가려는 방향이 진짜 맞나"를 빠르고 날카롭게 압박 검토하는 범용 리뷰 스킬입니다.
아이디어, 프로젝트 방향, 스펙, 아키텍처 선택, 운영 방식, 우선순위 결정처럼 실제로 시간을 쓰기 직전의 판단에 사용합니다.

기본 역할은 "심화 분석기"가 아니라 "방향성 브레이크"입니다.
먼저 현재 방향에 강한 제동을 걸고, 필요할 때만 심층 사고와 독립 리뷰를 추가합니다.

## Trigger

다음 상황에서 이 스킬을 우선 고려합니다.

- 사용자가 "한 번 브레이크 걸어줘", "이 결정의 허점을 봐줘", "리스크를 더 세게 봐줘", "내가 뭘 과하게 더하고 있나?", "이게 최선인지 의심해봐" 같은 요청을 할 때
- 사용자가 "이게 진짜 문제를 푸는지 봐줘", "심층 리뷰 해줘", "생각의 외주를 줘서 다시 봐줘", "깊게 생각해봐", "다른 시각까지 검토해줘", "독립된 다른 시각으로 검토해줘" 같은 요청을 할 때
- 이미 방향 초안은 있는데, 실행 전에 논리적 허점과 상대우위를 다시 보고 싶을 때
- 문서, 기능, 아키텍처, 프로세스 등 대상은 다르지만 의사결정 자체를 검토하려는 목적일 때

다음 경우에는 다른 스킬이 더 적합할 수 있습니다.

- 아직 문제 정의와 아이디어 발산이 더 필요하면 `office-hours`
- 아이디어 자체를 builder vs reviewer 토론으로 붙이고 싶으면 `idea-review`
- feature plan 문서를 founder-mode 로 재조정하려면 `plan-ceo-review`
- 요구사항을 명세로 잠가야 하면 `requirement-clarifier` 또는 `spec-creator`
- 코드 구현 후 허점, test gap, 회귀 위험을 보려면 `implementation-brake`
- 구현이 목적이면 구현 스킬

## Core Posture

- 목적은 동의나 격려가 아니라 의사결정 품질 향상입니다.
- 사용자가 제시한 해법을 전제로 깔지 않습니다. 문제와 해법을 분리해서 봅니다.
- "무엇을 더할까"보다 "무엇을 빼야 하나"를 먼저 검토합니다.
- 좋은 비판은 반드시 더 단순하거나 더 유연한 대안을 동반해야 합니다.
- 확신 없는 미온적 중간 결론보다, 조건부라도 명확한 권고를 냅니다.

## Roles

이 스킬은 아래 3개의 역할을 분리해서 사용합니다.

### 1. Base Decision Brake

메인 에이전트가 수행하는 기본 브레이크입니다.

- 짧고 강한 방향성 검토가 목적입니다.
- 검토의 중심은 "이 방향이 진짜 문제를 풀고 있는가"와 "더 단순한 대안이 있는가"입니다.
- 심층 사고법을 길게 나열하지 않고, 현재 결정에 가장 치명적인 약점을 먼저 겨냥합니다.

### 2. Decision-Brake Thinker

`decision-brake-thinker`는 심층 사고를 맡는 보조 에이전트입니다.

- reviewer 가 아니라 thinker 입니다.
- 제1원칙, 시스템사고, second-order, 역발상 같은 프레임으로 문제를 다시 모델링합니다.
- 최종 승인자가 아니라, 메인 판단을 더 깊게 만드는 분석 재료를 생산합니다.

### 3. Decision-Brake Reviewer

`decision-brake-reviewer`는 독립 검토를 맡는 전용 리뷰어입니다.

- 메인 `decision-brake`의 판단과 `thinker`의 심층 사고 결과를 검토합니다.
- 역할은 생각을 더 생산하는 것이 아니라, 이미 나온 판단과 사고의 약점, 과신, 누락을 압박 검토하는 것입니다.
- 독립된 반론과 더 나은 대안을 통해 브레이크를 강화합니다.

## Activation Policy

기본 흐름은 아래 순서를 따릅니다.

1. 메인 `decision-brake`가 먼저 1차 브레이크를 수행합니다.
2. 더 깊은 구조 분석이 필요하면 `decision-brake-thinker`를 추가합니다.
3. 독립 검토가 필요하면 `decision-brake-reviewer`를 추가합니다.

### When to add thinker

아래 신호가 보이면 `decision-brake-thinker`를 추가합니다.

- 기본 브레이크만으로는 판단 근거가 얕습니다.
- 문제 구조가 복합적이어서 다른 프레임으로 다시 봐야 합니다.
- 2차 효과, 시스템 상호작용, 장기 비용이 중요합니다.
- 문제 정의를 더 근본 단위로 다시 쪼개야 합니다.

### When to add reviewer

아래 신호가 보이면 `decision-brake-reviewer`를 추가합니다.

- 되돌리기 어렵고 비용이 큰 의사결정입니다.
- 확증 편향, 매몰 비용, 강한 내부 확신 때문에 독립 검토가 필요합니다.
- 메인 판단이나 thinker 산출물에 과신 위험이 있습니다.
- 사용자가 독립된 다른 시각, delegated review, 2차 검토를 원합니다.

### Explicit user request rule

사용자가 심층 리뷰, 생각의 외주, 깊게 생각해봐, 다른 시각까지 검토해줘 같은 깊은 검토를 명시적으로 요청하면 `thinker + reviewer`를 모두 붙입니다.

예:

- "심층 리뷰 해줘"
- "생각의 외주를 줘서 봐줘"
- "깊게 생각해보고 다시 검토해줘"
- "다른 시각까지 붙여서 봐줘"

## Workflow

### 1. Ground the decision

먼저 지금 검토 대상이 무엇인지 짧게 고정합니다.

- 지금 결정하려는 것
- 이 결정을 지금 내리려는 이유
- 암묵적으로 전제한 사실 또는 제약

필요하면 저장소, 문서, 기존 코드에서 사실관계를 읽고 보강하되, 검토의 중심은 "판단"입니다.

### 2. Brake the direction

`references/review-lenses.md`의 기본 질문을 이용해 현재 방향을 압박 검토합니다.

특히 아래 질문을 우선합니다.

- 이 방향은 진짜 문제를 풀고 있는가, 아니면 proxy 문제를 풀고 있는가?
- 가장 큰 실패는 어디서 발생하는가?
- 지금 방향보다 단순한 대안이 있는가?
- 추가보다 제거가 더 좋은 해법은 없는가?
- 이 방향을 지금 고정할 근거가 충분한가?

### 3. Deepen if needed

`thinker`가 필요하면 심층 사고 프레임으로 문제를 다시 모델링합니다.

- thinker 는 문제 재정의, 구조적 상호작용, second-order cost, inversion 관점을 확장합니다.
- thinker 결과는 최종 결론이 아니라 메인 판단을 깊게 만드는 입력입니다.

### 4. Review if needed

`reviewer`가 필요하면 메인 판단과 thinker 결과를 독립 검토합니다.

- reviewer 는 새로운 분석기를 자처하지 않습니다.
- reviewer 는 이미 나온 판단과 심층 사고의 약점, 비약, 과신, 누락을 검토합니다.
- reviewer 는 더 단순하거나 더 안전한 대안을 제시할 수 있습니다.

### 5. Compare alternatives

최소 2개의 대안을 둡니다.

- **Current path**: 사용자가 지금 기울어 있는 방향
- **Leaner path**: 더 적은 가정, 더 적은 이동부품, 더 빠른 검증 경로

필요하면 세 번째 대안을 추가합니다.

- **More flexible path**: 지금은 약간 덜 완결적이어도 나중 선택지를 더 열어두는 경로

### 6. Recommend with a clear brake level

마지막에는 아래 중 하나로 판정합니다.

- `[PROCEED]`: 지금 방향이 충분히 타당함
- `[PROCEED WITH CHANGES]`: 핵심 수정 후 진행할 가치가 있음
- `[PAUSE]`: 중요한 가정, 리스크, 경직성이 정리되기 전까지 멈춰야 함
- `[STOP]`: 현재 방향은 문제 정의 또는 접근 자체를 다시 잡는 편이 나음

## Output Shape

응답은 아래 순서를 기본으로 합니다.

1. **Decision under review**
2. **What is probably wrong or weak**
3. **Risks and failure modes**
4. **Better alternatives**
5. **Recommendation**
6. **Brake level**

`thinker`를 사용했다면 아래를 짧게 덧붙입니다.

- **Thinker signal**

`reviewer`를 사용했다면 아래를 짧게 덧붙입니다.

- **Independent reviewer signal**

필요하면 마지막에 `Open questions`를 붙이되, 질문은 정말 방향을 바꾸는 것만 남깁니다.

## Companion Agents

이 저장소에는 아래 보조 에이전트를 둘 수 있습니다.

- `decision-brake-thinker`
- `decision-brake-reviewer`

사용 시 원칙은 다음과 같습니다.

- thinker 는 심층 사고를 맡습니다.
- reviewer 는 메인 판단과 thinker 결과를 검토합니다.
- 메인 에이전트는 thinker/reviewer 결과를 그대로 복붙하지 말고, 충돌 지점과 공통 결론을 종합해 최종 권고문으로 압축합니다.

코드가 이미 작성된 뒤 구현 수준의 허점을 찾는 요청은 이 스킬보다 `implementation-brake`에 더 가깝습니다.

## Constraints

- 기본 목적은 리뷰와 권고이지, 구현이나 스캐폴딩이 아닙니다.
- 대상이 문서가 아니어도 사용할 수 있어야 합니다.
- 기본 모드를 과도하게 무겁게 만들지 않습니다.
- thinker 는 reviewer 를 대체하지 않습니다.
- reviewer 는 thinker 를 대체하지 않습니다.
- 비판만 하고 끝내지 말고, 항상 더 나은 대안 또는 더 나은 질문을 남깁니다.
