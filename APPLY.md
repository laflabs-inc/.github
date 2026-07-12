# 적용 방법

이 폴더의 내용물을 `laflabs-inc/.github` Repository 루트에 그대로 업로드하세요.

## 적용 전 확인

1. `profile/assets/`의 Light/Dark SVG가 GitHub 테마에서 의도대로 보이는지 확인
2. `SECURITY.md`에 향후 공식 Security Contact가 생기면 추가
3. `workflow-templates/`의 Node/Python version을 각 Repository 정책에 맞게 조정
4. Organization Settings에서 Rulesets와 Security 기능은 별도로 설정
5. Issue Form의 자동 Label은 중앙 템플릿에서 일부러 지정하지 않음
   - Repository마다 Label이 없으면 자동 적용되지 않기 때문
   - 조직 공통 Label 체계를 정한 뒤 추가하는 것을 권장

## 주의

- `.github` Repository는 Public이어야 대부분의 default community health file이 조직 전체에 적용됩니다.
- 개별 Repository에 같은 파일이 있으면 개별 파일이 우선합니다.
- 개별 Repository에 `.github/ISSUE_TEMPLATE` 폴더 내용이 하나라도 있으면 중앙 Issue Template 폴더는 fallback되지 않습니다.
- `workflow-templates/`는 자동 실행되지 않습니다. 새 Workflow 생성 화면에서 조직 템플릿으로 선택해 각 Repository에 복사하는 용도입니다.
