# 보안 정책

## 지원 버전

최신 릴리스만 보안 수정을 받습니다. 문제가 확인되면 새 버전으로 수정본을 배포합니다.

## 취약점 신고

공개 이슈로 올리지 말고 [비공개 신고 페이지](https://github.com/Faavilla/yuginong-theme/security/advisories/new)에서 신고해 주세요. 저장소의 **Security** 탭에서 **Report a vulnerability**를 눌러도 됩니다. 신고하려면 GitHub에 로그인해야 합니다.

다음 내용을 함께 적어 주시면 확인이 빠릅니다.

- 영향을 받는 버전(태그)
- 재현 방법
- 예상되는 영향

## 배포 방식

- GitHub Releases로만 배포합니다. VS Code 마켓플레이스 등 다른 곳에 올라온 같은 이름의 확장은 이 저장소에서 배포한 것이 아닙니다.
- `.vsix`는 사람이 직접 올리지 않습니다. `v*` 태그가 푸시되면 GitHub Actions가 해당 커밋에서 빌드해 릴리스에 첨부합니다.
- 릴리스는 불변(immutable)으로 게시되므로, 게시 후에는 첨부 파일과 태그를 바꿀 수 없습니다.

## 내려받은 파일 확인

[GitHub CLI](https://cli.github.com/)로 릴리스와 내려받은 `.vsix`가 게시된 그대로인지 확인할 수 있습니다.

```bash
gh release verify v<버전> --repo Faavilla/yuginong-theme
gh release verify-asset v<버전> yuginong-theme-<버전>.vsix --repo Faavilla/yuginong-theme
```

웹에서는 릴리스 페이지 제목 아래에 **Immutable** 표시가 있는지 확인하면 됩니다.

## 범위

이 확장은 색상 테마(JSON)만 담고 있으며 실행되는 코드가 없습니다. 다음과 같은 문제를 신고 대상으로 봅니다.

- 릴리스 파일이 이 저장소의 소스와 다르게 빌드되었거나 변조된 경우
- 릴리스 워크플로(`.github/workflows/release.yml`)의 취약점
