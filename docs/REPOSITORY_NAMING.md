# Repository Naming Convention

이 문서는 LafLabs Inc. GitHub Organization의 Repository 명명, 분류, 수명주기 및 메타데이터 기준을 정의합니다.

목표는 Repository 수가 늘어나도 이름만 보고 역할과 범위를 빠르게 이해할 수 있도록 하는 것입니다.

---

## 1. Core rules

모든 Repository 이름은 다음 원칙을 따릅니다.

- `kebab-case` 사용
- 영문 소문자 사용
- 의미 없는 약어 최소화
- 조직명 `laflabs` 또는 `laflabs-inc`를 반복하지 않음
- `new`, `old`, `final`, `v2`, `test2` 같은 임시 상태 표현 금지
- 구현 기술보다 Domain 또는 역할을 우선
- 지나치게 긴 이름 금지
- 이름은 가능한 한 2~4개의 단어로 제한

### Recommended

```text
laf-id
laf-pay
lafdock
identity-api
billing-worker
cloud-agent
infra-production
```

### Avoid

```text
LafID
laf_id
laflabs-laf-id
new-laf-id-api-v2
laf-id-backend-server-service
final-production-api
```

---

## 2. Product repositories

제품 자체를 대표하는 Repository는 제품의 공식 이름을 사용합니다.

```text
laf-id
laf-pay
lafdock
```

제품 Repository는 다음 중 하나일 수 있습니다.

- Monorepo
- Product shell
- Main application repository
- Product-level orchestration repository

제품 내부가 여러 서비스로 분리되더라도 무조건 제품 이름을 모든 Repository에 반복하지는 않습니다.

### Avoid

```text
laf-id-identity-auth-api
laf-id-user-account-api
laf-id-oauth-api-service
```

### Prefer

```text
identity-api
account-service
authorization-server
```

단, Organization 전체에서 이름 충돌 가능성이 높거나 제품 경계가 명확히 필요한 경우에만 Product prefix를 사용합니다.

---

## 3. Service repositories

서비스는 가능한 한 다음 형식을 사용합니다.

```text
<domain>-<role>
```

Examples:

```text
identity-api
billing-worker
notification-service
audit-service
cloud-agent
network-controller
```

### Preferred role suffixes

```text
api
service
worker
agent
controller
gateway
scheduler
processor
proxy
operator
```

불필요하게 여러 역할을 한 이름에 중첩하지 않습니다.

### Avoid

```text
identity-api-service
billing-background-worker-service
cloud-network-controller-agent
```

---

## 4. SDK repositories

SDK는 다음 형식을 사용합니다.

```text
<product-or-domain>-sdk-<language>
```

Examples:

```text
laf-id-sdk-typescript
laf-id-sdk-python
laf-pay-sdk-kotlin
lafdock-sdk-go
```

공식 Package 이름은 각 생태계의 표준을 따릅니다.

Examples:

```text
npm      @laflabs/identity
Python   laflabs-identity
Maven    io.laflabs.identity
Go       github.com/laflabs-inc/...
```

Repository 이름과 Package 이름은 반드시 동일할 필요는 없습니다.

---

## 5. Libraries

Library는 구현 기술보다 역할을 우선합니다.

```text
<domain>-<purpose>
```

Examples:

```text
oidc-toolkit
token-validator
http-signatures
audit-events
```

Organization 내부에서 범용으로 사용되더라도 무조건 `common`, `shared`, `utils` 같은 이름을 사용하지 않습니다.

### Avoid

```text
common
shared
utils
helpers
core
```

이런 이름은 시간이 지날수록 책임 범위가 무너질 가능성이 높습니다.

---

## 6. Infrastructure repositories

Infrastructure는 `infra-` prefix를 사용합니다.

```text
infra-<scope>
```

Examples:

```text
infra-production
infra-staging
infra-network
infra-observability
infra-shared
```

Terraform, Ansible, Kubernetes 등 특정 기술은 필요할 때만 suffix로 표현합니다.

Examples:

```text
infra-production
infra-network
infra-edge
```

Avoid:

```text
terraform-all
ansible-server
k8s-final
```

기술이 바뀌어도 Repository 역할이 유지되는 이름이 더 안정적입니다.

---

## 7. Deployment repositories

배포 전용 Repository가 필요한 경우 다음 형식을 사용합니다.

```text
deploy-<target>
```

Examples:

```text
deploy-laf-id
deploy-laf-pay
deploy-lafdock
```

단순 CI/CD 설정만 존재하는 경우 별도 Repository를 만들기보다 해당 서비스 Repository 또는 Infrastructure Repository에서 관리하는 것을 우선합니다.

---

## 8. Documentation repositories

제품 또는 시스템 문서는 다음 형식을 사용합니다.

```text
<product-or-domain>-docs
```

Examples:

```text
laf-id-docs
lafdock-docs
platform-docs
```

Organization 전체 개발 문서는 가능하면 `.github` 또는 별도의 `engineering-handbook` Repository로 통합합니다.

---

## 9. Specifications and standards

Protocol, Schema, Public Contract, Standard 문서는 다음 형식을 사용합니다.

```text
<domain>-spec
```

Examples:

```text
identity-spec
billing-spec
event-schema
api-guidelines
```

---

## 10. Templates

Template Repository는 다음 형식을 사용합니다.

```text
template-<purpose>
```

Examples:

```text
template-nextjs
template-fastapi
template-service
template-library
```

Template Repository에는 실제 Production Secret이나 고객 데이터가 포함되어서는 안 됩니다.

---

## 11. Experimental repositories

실험성 프로젝트는 다음 형식을 권장합니다.

```text
experimental-<name>
```

Examples:

```text
experimental-agent-runtime
experimental-memory-engine
experimental-edge-network
```

실험이 성공해 Production 수준으로 승격되면 안정적인 이름으로 새 Repository를 만들거나 명확한 migration을 수행합니다.

영구적으로 `experimental-` 상태를 유지하지 않습니다.

---

## 12. Archive and deprecated repositories

Repository 이름에 다음 suffix를 추가하지 않습니다.

```text
-old
-legacy
-deprecated
-archive
```

대신 GitHub의 Repository Archive 기능과 README 상단의 상태 표시를 사용합니다.

Example:

```text
> Status: Deprecated
> Replacement: `identity-api`
```

필요하면 Repository Topic 또는 Custom Property를 사용합니다.

---

## 13. Repository lifecycle

LafLabs Repository는 다음 Lifecycle 중 하나를 가집니다.

```text
experimental
active
maintenance
deprecated
archived
```

### experimental

실험 또는 검증 단계입니다.

- Production dependency로 사용하지 않는 것을 기본으로 함
- API 안정성 보장 없음
- 빠른 변경 허용

### active

현재 적극적으로 개발 및 운영합니다.

- Maintainer 존재
- Security update 수행
- CI 유지
- Issue 및 PR 관리

### maintenance

주요 기능 개발은 줄었지만 계속 지원합니다.

- Bug fix
- Security update
- Compatibility maintenance

### deprecated

대체 경로가 존재하거나 제거 예정입니다.

- README에 대체 Repository 또는 Migration 안내
- 신규 기능 개발 중단
- 필요한 Security fix만 수행

### archived

더 이상 유지하지 않습니다.

- Read-only
- 명확한 Archive 사유 기록
- Replacement가 있다면 연결

---

## 14. Repository description

Description은 한 문장으로 Repository의 목적을 설명합니다.

좋은 Description은 다음 질문에 답합니다.

> 이 Repository는 무엇이며, 왜 존재하는가?

### Good

```text
OpenID Connect and account infrastructure for the LafLabs ecosystem.
```

```text
Cloud control-plane service for LafDock compute resources.
```

### Avoid

```text
Backend
Main server
New project
LafLabs project
```

Description은 구현 기술보다 역할을 설명하는 것을 우선합니다.

---

## 15. Topics

Repository Topics는 검색과 분류를 위해 사용합니다.

Recommended topic categories:

### Organization

```text
laflabs
```

### Product

```text
laf-id
laf-pay
lafdock
```

### Domain

```text
identity
payments
cloud
infrastructure
authentication
billing
networking
```

### Technology

```text
fastapi
nextjs
kotlin
postgresql
redis
docker
```

기술 Topic은 실제 Repository와 직접 관련된 것만 사용합니다.

---

## 16. Visibility

Visibility는 목적에 따라 결정합니다.

### Public

- Open Source
- Public SDK
- Public specification
- Developer tool
- Documentation
- Community project

### Private

- Production infrastructure
- Internal service
- Security-sensitive system
- Customer-specific integration
- Internal operational tooling
- Business-sensitive source code

공개 여부는 Marketing보다 Security와 Maintenance 책임을 먼저 고려합니다.

---

## 17. Naming decision checklist

새 Repository를 만들기 전에 확인합니다.

- [ ] 기존 Repository와 역할이 중복되지 않는가?
- [ ] 새 Repository가 정말 필요한가?
- [ ] Monorepo 내부 Package로 충분하지 않은가?
- [ ] 이름이 기술보다 역할을 설명하는가?
- [ ] 이름이 2년 후에도 의미가 유지될 수 있는가?
- [ ] `common`, `shared`, `utils`, `core`처럼 책임이 모호하지 않은가?
- [ ] Product prefix가 정말 필요한가?
- [ ] 이름에 임시 상태나 Version이 들어가 있지 않은가?

---

## 18. Examples for LafLabs

### Product

```text
laf-id
laf-pay
lafdock
```

### Identity

```text
identity-api
authorization-server
identity-console
laf-id-sdk-typescript
laf-id-sdk-python
```

### Payments

```text
billing-api
payment-gateway
billing-worker
laf-pay-sdk-typescript
```

### Cloud

```text
cloud-api
cloud-agent
network-controller
lafdock-console
```

### Platform

```text
platform-api
notification-service
audit-service
developer-portal
```

### Infrastructure

```text
infra-production
infra-staging
infra-network
infra-observability
```

---

## 19. Exception policy

모든 규칙에는 예외가 있을 수 있습니다.

예외는 다음 조건을 만족해야 합니다.

1. 기존 생태계 표준 또는 외부 호환성 때문에 필요함
2. Repository 역할을 더 명확하게 설명함
3. 장기적인 유지보수성이 더 좋아짐

단순 취향을 이유로 Convention을 깨지 않습니다.
