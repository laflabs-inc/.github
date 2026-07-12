# Contributing to LafLabs

LafLabs의 프로젝트에 기여해주셔서 감사합니다.

이 문서는 조직 전체의 기본 Contribution Guideline입니다. 개별 저장소에 별도의 `CONTRIBUTING.md`가 있다면 해당 문서가 우선합니다.

## 1. Before you start

변경을 시작하기 전에 다음을 확인해주세요.

- 동일한 Issue 또는 Pull Request가 이미 존재하는지 검색합니다.
- 큰 기능, Breaking Change, Architecture 변경은 구현 전에 Issue 또는 Discussion을 통해 방향을 합의합니다.
- Security Vulnerability는 공개 Issue로 등록하지 않습니다. `SECURITY.md`를 따릅니다.

## 2. Development principles

LafLabs는 다음 원칙을 우선합니다.

- **KISS** — 불필요한 복잡성을 만들지 않습니다.
- **YAGNI** — 현재 필요하지 않은 추상화와 기능을 미리 만들지 않습니다.
- **DRY** — 의미 있는 중복은 줄이되, 잘못된 추상화를 위해 억지로 합치지 않습니다.
- **SOLID** — 변경 가능성이 높은 경계를 명확하게 분리합니다.
- **Secure by default** — 보안을 선택 사항으로 두지 않습니다.
- **Readable over clever** — 영리한 코드보다 이해하기 쉬운 코드를 우선합니다.

## 3. Branches

권장 Branch Naming Convention:

```text
feature/<short-description>
fix/<short-description>
refactor/<short-description>
docs/<short-description>
chore/<short-description>
security/<short-description>
```

예:

```text
feature/oidc-session-management
fix/token-refresh-race
docs/api-authentication
```

장기간 유지되는 `develop` branch는 기본적으로 권장하지 않습니다. 가능한 경우 짧은 수명의 feature branch와 보호된 default branch를 사용합니다.

## 4. Commits

Commit은 하나의 논리적 변경 단위로 유지합니다.

권장 형식:

```text
<type>: <summary>
```

Types:

- `feat`
- `fix`
- `refactor`
- `docs`
- `test`
- `build`
- `ci`
- `chore`
- `security`

예:

```text
feat: add PKCE verification
fix: prevent duplicate refresh token rotation
docs: document identity provider flow
```

## 5. Pull Requests

Pull Request는 다음 원칙을 따릅니다.

- 변경 이유와 사용자 또는 시스템에 미치는 영향을 설명합니다.
- 관련 Issue가 있으면 연결합니다.
- 테스트 방법과 결과를 기록합니다.
- Breaking Change, Migration, Security Impact가 있으면 명확히 표시합니다.
- PR의 범위는 가능한 한 하나의 목적에 집중합니다.
- 단순 포맷 변경과 기능 변경을 불필요하게 섞지 않습니다.

Draft Pull Request는 초기 피드백이 필요할 때 사용합니다.

## 6. Testing

변경 유형에 따라 적절한 검증을 수행합니다.

최소 기준:

- 기존 테스트가 깨지지 않아야 합니다.
- 새 동작에는 가능한 경우 자동화된 테스트를 추가합니다.
- 인증, 결제, 권한, 데이터 마이그레이션은 실패 경로와 경계 조건을 검증합니다.
- UI 변경은 주요 viewport와 접근성 영향을 확인합니다.
- Infrastructure 변경은 rollback 방법을 고려합니다.

## 7. Security

다음 정보는 Commit, Issue, Pull Request, Screenshot, Log에 포함하지 않습니다.

- API Key
- Password
- Access Token / Refresh Token
- Private Key
- Session Secret
- Production Credential
- Customer Personal Data
- Internal-only Infrastructure Address

Secret이 노출되었다면 삭제만 하지 말고 **즉시 폐기 및 교체(rotation)** 해야 합니다.

## 8. Review

Review는 사람을 평가하는 과정이 아니라 변경을 검증하는 과정입니다.

Reviewer는 다음을 확인합니다.

1. 이 변경이 필요한가?
2. 더 단순한 방법이 있는가?
3. 유지보수 가능한가?
4. Security 또는 Privacy 영향이 있는가?
5. Failure Mode와 rollback이 고려되었는가?
6. 충분히 테스트되었는가?

## 9. Licensing

각 Repository의 License가 해당 프로젝트에 적용됩니다. Organization의 `.github` Repository는 개별 프로젝트의 License를 대신하지 않습니다.
