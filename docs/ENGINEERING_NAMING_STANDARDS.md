# Engineering Naming Standards

이 문서는 Repository 외의 LafLabs 공통 기술 명명 규칙을 정의합니다.

## Repository

```text
kebab-case
```

Examples:

```text
identity-api
laf-id-sdk-python
infra-production
```

## Git branches

```text
feature/<short-description>
fix/<short-description>
refactor/<short-description>
docs/<short-description>
chore/<short-description>
security/<short-description>
```

## Environment variables

```text
UPPER_SNAKE_CASE
```

Examples:

```text
DATABASE_URL
REDIS_URL
OIDC_ISSUER
```

## Secrets

Secret 이름도 `UPPER_SNAKE_CASE`를 사용합니다.

Examples:

```text
DATABASE_PASSWORD
JWT_PRIVATE_KEY
CLOUDFLARE_API_TOKEN
```

Secret 이름에 실제 Secret 값을 포함하지 않습니다.

## Service identifiers

```text
kebab-case
```

Examples:

```text
identity-api
billing-worker
cloud-agent
```

## Deployment environments

표준 이름:

```text
development
staging
production
```

필요하면 다음을 추가할 수 있습니다.

```text
preview
sandbox
```

Avoid:

```text
dev2
prod-new
real-prod
final
```

## Docker images

권장:

```text
ghcr.io/laflabs-inc/<repository-or-service>
```

Examples:

```text
ghcr.io/laflabs-inc/identity-api
ghcr.io/laflabs-inc/cloud-agent
```

## GitHub Teams

```text
kebab-case
```

Examples:

```text
platform
identity
payments
cloud
security
```

Team은 단순 분류가 아니라 실제 책임과 권한 경계를 반영해야 합니다.

## Internal package names

각 생태계의 표준을 우선합니다.

### npm

```text
@laflabs/<package>
```

### Python

```text
laflabs-<package>
```

또는 import package:

```text
laflabs_<package>
```

### Maven / Gradle

```text
io.laflabs.<domain>
```

### Docker

```text
ghcr.io/laflabs-inc/<name>
```

## API naming

Public API는 구현 언어의 내부 명명보다 외부 일관성을 우선합니다.

권장:

- Resource noun 사용
- Stable URL 유지
- 구현 상세를 URL에 노출하지 않음
- Version은 필요할 때만 명시적 정책으로 관리

Avoid:

```text
/api/new-user-controller-v2
```

Prefer:

```text
/v1/users
```

## Database naming

기본 권장:

```text
snake_case
```

Examples:

```text
user_id
created_at
refresh_tokens
```

다만 ORM Convention과 기존 Schema가 있다면 일관성을 우선합니다.

## Event names

권장:

```text
<domain>.<entity>.<event>
```

Examples:

```text
identity.user.created
billing.payment.succeeded
cloud.instance.started
```

Event 이름은 발생한 사실을 표현합니다.

Avoid:

```text
create-user
payment-do
instance-process
```

## Final principle

Naming은 짧게 만드는 것이 목표가 아닙니다.

좋은 이름은:

- 역할을 설명하고
- 범위를 제한하며
- 시간이 지나도 의미가 유지되고
- 팀 전체가 동일하게 이해할 수 있어야 합니다.
