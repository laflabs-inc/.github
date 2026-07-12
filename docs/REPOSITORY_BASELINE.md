# Repository Baseline

새 Repository를 만들 때 사용하는 LafLabs 기본 체크리스트입니다.

## Required

- [ ] Repository 목적과 Owner가 명확하다.
- [ ] `README.md`가 존재한다.
- [ ] 적절한 `LICENSE`가 개별 Repository에 존재한다.
- [ ] Default branch가 `main`이다.
- [ ] Ruleset 또는 Branch Protection이 적용되어 있다.
- [ ] Security 기능이 목적에 맞게 활성화되어 있다.
- [ ] CI가 변경 사항을 검증한다.
- [ ] Secret이 Repository에 저장되지 않는다.

## Recommended

- [ ] CODEOWNERS
- [ ] Dependabot configuration
- [ ] Release strategy
- [ ] Deployment Environment separation
- [ ] ADR 또는 Architecture documentation
- [ ] Operational runbook for production systems
- [ ] Observability and rollback plan

## Repository-specific overrides

조직 기본값과 다른 동작이 필요하면 해당 Repository에 명시적으로 다음 파일을 둡니다.

```text
.github/ISSUE_TEMPLATE/
.github/PULL_REQUEST_TEMPLATE.md
CONTRIBUTING.md
SECURITY.md
SUPPORT.md
CODE_OF_CONDUCT.md
GOVERNANCE.md
```

개별 Repository의 요구가 조직 기본값보다 구체적이어야 하며, 단순 복제본을 만들지는 않는 것을 권장합니다.

## CODEOWNERS example

```text
# Default owner
* @laflabs-inc/platform

# Security-sensitive code
/auth/ @laflabs-inc/identity @laflabs-inc/security
/payments/ @laflabs-inc/payments @laflabs-inc/security
```

실제 Team이 생성되기 전에는 존재하지 않는 Team을 CODEOWNERS에 추가하지 마세요.
