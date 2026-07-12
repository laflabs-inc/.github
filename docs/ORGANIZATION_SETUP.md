# LafLabs GitHub Organization Setup

이 문서는 `.github` Repository만으로 강제할 수 없는 GitHub Organization 설정을 정리합니다.

## 1. Repository creation

권장 기본값:

- Default branch: `main`
- Repository visibility: 목적에 따라 명시적으로 선택
- Repository deletion / transfer: Owner 또는 제한된 관리자만
- Forking of private repositories: 업무 필요성이 있을 때만 허용
- Repository creation permission: 초기에는 Owner 중심, 팀 확장 후 정책화

## 2. Rulesets

중요 Repository에는 Branch Protection보다 Organization Rulesets를 우선 검토합니다.

권장 `main` baseline:

- Direct push 제한
- Pull Request required
- Required approvals: 최소 1명
- Dismiss stale approvals when new commits are pushed
- Require conversation resolution
- Require status checks
- Block force pushes
- Block branch deletion

Identity, Payment, Production Infrastructure처럼 위험도가 높은 Repository:

- Required approvals: 2명 이상 검토
- CODEOWNERS review 요구
- Deployment Environment approval
- 더 강한 status check와 release control

> 초기 1인 조직에서는 모든 규칙을 과도하게 강제하면 스스로 작업을 막을 수 있습니다.
> 현재 인원에 맞게 최소 보호를 적용하고, 팀이 늘면 approval 수와 CODEOWNERS를 강화하세요.

## 3. Security baseline

가능한 범위에서 다음을 활성화합니다.

- Dependency graph
- Dependabot alerts
- Dependabot security updates
- Secret scanning
- Push protection
- Private vulnerability reporting
- Code scanning / CodeQL for supported repositories

특히 Laf ID, Laf Pay, LafDock control-plane 관련 Repository는 우선순위를 높입니다.

## 4. Actions policy

권장 원칙:

- `GITHUB_TOKEN` default permission은 가능한 한 read-only
- Workflow별로 필요한 permission만 명시
- Production 배포는 GitHub Environment 사용
- Production secret을 일반 Repository secret과 분리
- Third-party Action은 신뢰 가능한 Publisher만 사용
- 중요 Workflow는 가능하면 Commit SHA pinning 정책 검토
- Self-hosted runner는 Public Repository의 untrusted PR과 분리

## 5. Teams and ownership

조직이 커질 때 권장 Team 예시:

```text
@laflabs-inc/platform
@laflabs-inc/identity
@laflabs-inc/payments
@laflabs-inc/cloud
@laflabs-inc/security
```

Team은 이름만 만들지 말고 실제 책임 경계와 Repository 권한에 연결해야 합니다.

## 6. Repository properties

Repository 수가 늘면 Custom Properties를 사용해 분류하는 것을 권장합니다.

예시:

- `service_tier`: critical / standard / experimental
- `data_classification`: public / internal / confidential / restricted
- `owner_team`: identity / payments / cloud / platform
- `lifecycle`: active / maintenance / deprecated / archived

이 값은 향후 Ruleset, Security Policy, 운영 자동화의 기준으로 활용할 수 있습니다.

## 7. Environments

Production 배포에는 Environment를 사용합니다.

예:

```text
development
staging
production
```

`production` 권장:

- Required reviewers
- Environment-specific secrets
- Deployment branch/tag restriction
- 가능하면 OIDC 기반 Cloud authentication

## 8. Releases

권장:

- Semantic Versioning을 사용하는 Library/SDK는 `vMAJOR.MINOR.PATCH`
- Release Note 자동화 또는 표준화
- Artifact와 Source의 provenance 검토
- Breaking Change를 Release Note 상단에 명시

## 9. Audit and access review

조직이 성장하면 정기적으로 다음을 검토합니다.

- Organization Owners
- Outside collaborators
- Dormant accounts
- Personal Access Tokens and GitHub Apps
- Deploy keys
- Repository admin 권한
- Production Environment reviewer
- Self-hosted runner access

최소 권한 원칙을 유지하고, 더 이상 필요하지 않은 권한은 제거합니다.
