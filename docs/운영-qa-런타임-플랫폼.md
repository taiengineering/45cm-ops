# TAI 운영 QA 런타임 플랫폼

## 정의 문서 v1

---

# 1. 프로젝트 정의

TAI의 관제엔진은 더 이상 단순 Monitoring Engine이 아니다.

기존 Monitoring 시장은:

- Ping
- Uptime
- CPU
- Memory
- Log
- Trace

등의 기술 상태를 감시한다.

그러나 현실 운영팀의 실제 문제는:

```text
서비스가 실제로 동작하는가
```

이며,

더 큰 문제는:

```text
왜 문제가 발생했는지 모른다
```

이다.

따라서 TAI는 다음 방향으로 정의된다.

---

# 2. 핵심 정의

## TAI Watch Runtime

```text
AI 기반 Continuous Operational QA Runtime Platform
```

### 핵심 역할

- 실제 사용자 흐름을 24시간 반복 실행
- 운영 흐름을 지속적으로 검증
- 문제를 고객보다 먼저 발견
- Runtime Context를 수집
- 운영 의미를 해석
- 원인 추론을 지원
- 운영자 판단을 보조

---

# 3. 핵심 철학

## 3.1 QA가 본체다

기존 시장:

```text
Monitoring → Alert
```

TAI:

```text
Operational QA → Runtime Interpretation → Awareness
```

즉:

```text
QA 결과가 Truth Source
```

이다.

Monitoring은 QA 결과를 해석한 결과물이다.

---

## 3.2 사람 대신 반복 검증한다

운영자는 현재:

- 매일 결제 테스트
- 회원가입 테스트
- 메일 테스트
- 관리자 페이지 테스트

를 반복 수행한다.

TAI는 이를 Runtime으로 자동화한다.

---

## 3.3 고객보다 먼저 발견한다

목표:

```text
고객 문의 전에 먼저 발견
```

이다.

---

## 3.4 중요한 것은 “왜”다

기존 관제:

```text
결제 실패
```

TAI:

```text
최근 배포 이후
결제 callback timeout 증가
특정 모바일 환경 집중 발생
```

즉:

```text
운영 맥락 재구성
Operational Context Reconstruction
```

을 수행한다.

---

## 3.5 최종 판단은 인간이 한다

TAI는:

- 설명(Explain)
- 우선순위화(Prioritize)
- 가이드(Guide)
- 학습(Learn)

하지만:

```text
최종 책임과 판단은 인간 운영자
```

에게 남긴다.

---

# 4. 플랫폼 구조

---

# Layer 1 — Collection Runtime

## 역할

운영 흐름 Truth 수집.

## 입력 채널

### 1. External QA Runtime

실제 사용자처럼:

- 회원가입
- 로그인
- 결제
- 글쓰기
- 업로드
- 메일 확인

등 수행.

### 2. Runtime Script (Optional)

```html
<script src="tai-runtime.js"></script>
```

수집:

- JS error
- route change
- UX degradation
- browser runtime
- response timing

### 3. Runtime Event/Webhook (Advanced)

```http
POST /watch/events
```

수집:

- business event
- workflow event
- internal runtime

### 4. Future Runtime Sources

- APM
- OpenTelemetry
- Gateway
- Edge Runtime
- Browser Extension

---

# Layer 2 — Runtime Interpretation Engine

TAI 핵심 엔진.

## Situation

이벤트를 운영 상황으로 변환.

예:

```text
결제 실패 증가 상황
```

---

## Delta

상황 변화 추적.

- worsening
- recurring
- stabilizing
- resolved

---

## Attention

운영 우선순위 계산.

---

## Guidance

운영 대응 방향 생성.

---

## Learning

운영 경험 기억.

---

## Closure

운영자 최종 판단 기록.

---

# Layer 3 — Operational Projection

운영자 소비 구조 생성.

예:

```text
지금 가장 위험한 상황
오늘 확인해야 할 것
반복 재발 상황
```

---

# Layer 4 — Human Workflow

운영 UI/알림/이력.

- Dashboard
- Telegram
- Follow-up
- Resolution
- Operational Memory

---

# 5. Runtime Discovery

## 핵심 개념

고객이 QA 시나리오를 직접 만들지 않는다.

LLM Runtime Explorer가:

- 사이트 구조 탐색
- 메뉴 탐색
- 버튼 탐색
- flow 탐색

을 수행한다.

---

## 입력

고객 제공:

```text
URL
ID/PW
(optional) script
```

---

## LLM Runtime Discovery

LLM이:

- 회원가입 흐름
- 결제 흐름
- 게시글 흐름
- 관리자 흐름

등을 추론.

---

## Scenario Candidate 생성

예:

```text
signup_flow
payment_flow
posting_flow
mail_flow
```

---

## 사용자 승인

```text
이 흐름들을 QA 대상으로 등록할까요?
```

---

## Runtime QA 실행

반복 실행.

---

# 6. Progressive Runtime Intelligence

고객 연결 수준에 따라 엔진 정확도가 증가한다.

## Level 1 — URL

가능:

- uptime
- response
- external QA

---

## Level 2 — Account

가능:

- login flow
- payment flow
- posting flow

---

## Level 3 — Runtime Script

가능:

- JS error
- real user issue
- browser runtime

---

## Level 4 — Event/Webhook

가능:

- internal workflow
- business runtime

---

## Level 5 — SDK/APM

가능:

- trace
- infra context
- queue/runtime insight

---

# 7. Runtime Safety Principles

고객 Runtime에 피해를 주면 안 된다.

## 원칙

### 1. Never Block Customer Runtime

고객 Runtime 차단 금지.

---

### 2. Fail Open

TAI Runtime 실패 시:

```text
고객 서비스 영향 0
```

---

### 3. Async Only

동기 요청 최소화.

---

### 4. Runtime Isolation

고객 Runtime과 격리.

---

### 5. External QA First

핵심 Truth는 외부 QA Runtime.

---

### 6. Script is Optional

Script는 강화 Telemetry일 뿐.

---

# 8. 제품 정의

## 기존 시장

```text
Monitoring Tool
```

---

## TAI 정의

```text
운영 QA Runtime Platform
```

또는

```text
AI 기반 24시간 운영 QA 플랫폼
```

---

# 9. 고객 가치

## 운영팀

```text
매일 직접 테스트하지 않아도 된다.
```

---

## 관리자

```text
고객보다 먼저 장애를 발견한다.
```

---

## 개발팀

```text
왜 그런 상황이 발생했는지 추적 가능하다.
```

---

## 기업

```text
운영 지식을 Runtime으로 축적한다.
```

---

# 10. 시장 포지션

TAI는:

- Ping Monitoring
- APM
- 단순 QA 자동화

가 아니다.

TAI는:

```text
Operational Runtime Intelligence
운영 런타임 해석 플랫폼
```

를 목표로 한다.

---

# 11. 현재 방향 결론

현재 플랫폼 방향은:

```text
Monitoring
→ QA
→ Runtime Interpretation
→ Operational Intelligence
```

로 정의된다.

그리고:

```text
엔진은 Runtime Truth를 생성하고,
TAI는 운영 의미를 해석한다.
```

---

# 12. 작업 계획 (Execution Plan)

---

# Phase 1 — Physical Separation

## 목표

관제 Runtime 독립 SaaS화.

## 작업

- Git repo 분리
- Railway service 분리
- Runtime contract 고정
- TAI Safe 외부 소비 구조 전환
- Internal import 제거

---

# Phase 2 — External QA Runtime

## 목표

실제 사용자 흐름 QA Runtime 구축.

## 작업

- Playwright runtime cluster
- scenario runtime object
- execution scheduler
- retry/timeout runtime
- result collector

---

# Phase 3 — LLM Runtime Discovery

## 목표

AI 기반 운영 흐름 자동 발견.

## 작업

- browser exploration runtime
- flow inference
- scenario candidate generation
- operator approval flow

---

# Phase 4 — Runtime Interpretation 강화

## 목표

왜 발생했는지 설명 가능한 수준 확보.

## 작업

- runtime context density 증가
- event correlation
- browser/runtime merge
- deployment correlation
- tenant impact analysis
- LLM explanation runtime

---

# Phase 5 — Operational Workflow

## 목표

운영 조직 Runtime 완성.

## 작업

- Telegram runtime
- escalation workflow
- approval flow
- follow-up runtime
- operational memory
- recurrence intelligence

---

# Phase 6 — Commercialization

## 목표

관제 SaaS 출시.

## CTA

```text
무료 운영 QA 1주일 체험
```

## 과금 구조

### Free
- External QA 기본

### Pro
- attention/guidance
- dashboard
- telegram

### Advanced
- runtime script
- browser runtime
- learning

### Enterprise
- webhook/APM
- runtime integration
- organization workflow
- advanced intelligence
