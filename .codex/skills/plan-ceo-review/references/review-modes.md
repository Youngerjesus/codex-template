# Plan CEO Review Modes

## 1. Scope Expansion

이 모드는 계획을 더 크게, 더 가치 있게 만들 기회를 찾는 모드입니다.

### Use When

- 사용자가 명시적으로 더 크게 보고 싶어 한다
- 현재 plan 이 너무 방어적이거나 local optimum 에 갇혀 있다
- 같은 구조 위에 2배 정도의 노력으로 10배 가치가 나올 여지가 있다

### Review Focus

- 10x version 은 무엇인가
- platonic ideal 은 어떤 사용자 경험인가
- 지금 같이 넣으면 product quality 를 끌어올릴 adjacent improvement 는 무엇인가
- 이 확장이 미래의 다른 기능을 위한 platform 이 되는가

### Guardrail

- 아이디어를 많이 내도 scope 는 자동으로 바꾸지 않는다
- 각 확장안은 독립적으로 승인받는다
- rejected 항목은 `Not in scope` 또는 TODO 후보로 남긴다

## 2. Selective Expansion

이 모드는 현재 scope 를 baseline 으로 유지하되, 유의미한 추가 기회를 cherry-pick 하는 모드입니다.

### Use When

- 기존 시스템 위의 기능 개선이다
- 현재 plan 자체는 괜찮지만 더 좋은 선택지가 숨어 있을 수 있다
- 사용자가 "hold scope but tempt me" 성격의 리뷰를 원한다

### Review Focus

- baseline plan 을 먼저 bulletproof 하게 만든다
- 그 다음 확장 기회를 후보군으로만 분리한다
- accepted cherry-pick 만 이후 섹션의 새로운 scope 로 반영한다

### Guardrail

- neutral posture 를 유지한다
- 확장 후보가 많아도 상위 몇 개만 제시한다
- baseline 안정성보다 확장 욕심을 앞세우지 않는다

## 3. Hold Scope

이 모드는 현재 범위를 고정한 채 계획의 결함과 누락을 제거하는 모드입니다.

### Use When

- bugfix, hotfix, 안정화 작업이다
- scope 자체보다 architecture, test, deploy safety 가 더 중요하다
- 이미 business decision 은 끝났고 execution risk 만 줄이면 된다

### Review Focus

- 구조 누락
- failure mode 와 rescue gap
- 보안, observability, rollback, test coverage
- 과도한 moving part 와 불필요한 abstraction 제거

### Guardrail

- 범위를 늘리거나 줄이지 않는다
- 전략 아이디어가 떠올라도 "후속 고려사항" 수준으로만 적고 기본 scope 는 유지한다

## 4. Scope Reduction

이 모드는 결과를 내는 최소 경로만 남기고 나머지를 잘라내는 모드입니다.

### Use When

- plan 이 과도하게 넓다
- 파일 수, 컴포넌트 수, delivery risk 가 비정상적으로 크다
- 핵심 outcome 대비 부차적 작업이 너무 많다

### Review Focus

- absolute minimum path
- must-ship-together 와 follow-up 으로 분리
- 추후 확장해도 되는 요소를 명확히 defer

### Guardrail

- reduction 자체가 목적이지, 몰래 scope 를 다시 넣는 것이 아니다
- 사용자 경험의 핵심 가치가 깨지면 reduction 이 아니라 plan rewrite 문제다

## Quick Defaults

- Greenfield 제품/기능: `Scope Expansion`
- 기존 기능 개선: `Selective Expansion`
- 버그/핫픽스: `Hold Scope`
- 과도한 refactor 또는 일정 압박: `Scope Reduction`
