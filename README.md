# LafLabs Inc. — Organization Defaults

이 저장소는 LafLabs Inc.의 GitHub Organization 공통 프로필과 협업 기본값을 관리합니다.

## 포함 범위

- Organization Profile
- Default community health files
- Issue Forms
- Pull Request template
- Contribution and governance guidelines
- Security reporting policy
- Organization workflow templates
- GitHub Organization 운영 권장 설정 문서

> 이 저장소의 일부 파일은 GitHub의 **default community health files** 기능을 통해,
> 개별 저장소에 동일한 파일이 없을 때 조직 전체의 기본값으로 사용됩니다.

## 구조

```text
.
├── profile/
│   ├── README.md
│   └── assets/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── workflow-templates/
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── GOVERNANCE.md
├── SECURITY.md
├── SUPPORT.md
└── docs/
    ├── ORGANIZATION_SETUP.md
    └── REPOSITORY_BASELINE.md
```

## 운영 원칙

1. 조직 공통 기본값은 이 저장소에서 관리합니다.
2. 제품 또는 저장소 특화 정책은 해당 저장소에서 명시적으로 override합니다.
3. 보안 정책과 배포 정책은 편의보다 안전한 기본값을 우선합니다.
4. 자동화는 모든 저장소에 강제로 복사하지 않고, 표준 템플릿 또는 재사용 가능한 워크플로우로 관리합니다.
5. 조직이 성장해도 규칙을 이해하고 변경하기 쉬운 구조를 유지합니다.

---

© LafLabs Inc.
