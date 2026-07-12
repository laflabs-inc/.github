# Security Policy

LafLabs는 Security Vulnerability를 중요하게 다룹니다.

## Reporting a vulnerability

**보안 취약점을 공개 Issue, Discussion, Pull Request로 제보하지 마세요.**

가능한 경우 해당 Repository의 **Security** 탭에서 **Private vulnerability reporting** 또는 **Security Advisory** 기능을 사용해주세요.

보고 시 다음 정보를 포함하면 빠른 검토에 도움이 됩니다.

- 영향을 받는 Repository 또는 Product
- 영향을 받는 Version / Commit
- 취약점 유형
- 재현 절차
- 예상 영향
- Proof of Concept (필요한 최소 범위)
- 완화 또는 수정 아이디어가 있다면 관련 내용

## Sensitive data

다음 정보는 보고서에 불필요하게 포함하지 마세요.

- 실제 사용자 Credential
- Production Secret
- 불필요한 개인정보
- 제3자의 민감한 데이터

재현에 민감한 데이터가 필요하다면 가능한 한 최소화하거나 비식별화해주세요.

## Scope

이 기본 정책은 LafLabs Organization의 공개 Repository에 적용됩니다. 개별 Repository가 별도의 `SECURITY.md`를 제공하는 경우 해당 정책이 우선합니다.

Production Service, Managed Infrastructure, Identity, Payment 관련 제보는 각 서비스의 공식 Security Reporting Channel이 별도로 제공되는 경우 해당 채널을 우선 사용해주세요.

## Disclosure

LafLabs는 취약점의 위험도, 영향 범위, 수정 난이도를 검토한 뒤 적절한 공개 및 수정 절차를 결정합니다.

연구자에게 다음을 요청합니다.

- 수정 또는 완화가 완료되기 전에 취약점을 공개하지 않을 것
- 사용자 데이터에 접근하거나 파괴하지 않을 것
- 서비스 가용성을 고의로 저해하지 않을 것
- 필요한 최소 범위에서만 검증할 것

## Safe harbor

선의의 보안 연구가 이 정책의 범위와 관련 법규를 준수하는 경우, LafLabs는 해당 연구를 악의적인 활동으로 취급하지 않는 것을 원칙으로 합니다.

단, 이 정책은 법률 자문이나 포괄적인 법적 면책을 의미하지 않습니다.
