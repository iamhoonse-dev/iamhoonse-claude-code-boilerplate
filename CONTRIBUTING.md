# 기여 가이드

이 프로젝트에 기여해 주셔서 감사합니다! 아래 가이드라인을 참고해 주세요.

## 시작하기

1. 이 저장소를 **Fork** 합니다.
2. Fork한 저장소를 clone합니다:
   ```bash
   git clone https://github.com/<your-username>/iamhoonse-claude-code-boilerplate.git
   cd iamhoonse-claude-code-boilerplate
   ```
3. 작업용 브랜치를 생성합니다:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## 플러그인 관리

### 플러그인 추가

`.claude/settings.json`의 `enabledPlugins`에 항목을 추가합니다:

```json
{
  "enabledPlugins": {
    "plugin-name@marketplace-name": true
  }
}
```

플러그인 이름은 `플러그인명@마켓플레이스명` 형식을 따릅니다:
- 공식 마켓플레이스: `plugin-name@claude-plugins-official`
- 커스텀 마켓플레이스: `plugin-name@iamhoonse-claude-code`

### 플러그인 제거

`enabledPlugins`에서 해당 항목을 삭제하거나 값을 `false`로 변경합니다.

### 호환성 주의사항

새 플러그인을 추가할 때 기존 플러그인과의 충돌 여부를 확인해 주세요.
특히 Superpowers 플러그인과 워크플로우가 겹치는 플러그인(예: 자체 코드 리뷰, 디버깅, 계획 워크플로우를 제공하는 플러그인)은 충돌할 수 있습니다.

## 브랜치 전략

- `main` 브랜치는 보호됩니다. 직접 push하지 마세요.
- 작업 브랜치는 다음 네이밍을 따릅니다:
  - `feature/<기능명>` — 새 기능 추가
  - `fix/<수정내용>` — 버그 수정
  - `docs/<문서명>` — 문서 변경
  - `chore/<작업명>` — 기타 유지보수

## 커밋 컨벤션

[Conventional Commits](https://www.conventionalcommits.org/) 형식을 사용합니다:

```
<type>: <description>
```

### 타입

| 타입 | 용도 |
|-----|------|
| `feat` | 새 기능 추가 |
| `fix` | 버그 수정 |
| `docs` | 문서 변경 |
| `chore` | 빌드, 설정 등 기타 변경 |
| `refactor` | 리팩토링 (기능 변경 없음) |

### 예시

```
feat: enable playwright plugin
docs: update README plugin list
fix: correct marketplace source URL
chore: update gitignore patterns
```

## PR 가이드라인

### PR 작성 시 포함할 내용

- **변경 사항 요약**: 무엇을 왜 변경했는지
- **플러그인 변경 시**: 추가/제거한 플러그인과 사유
- **호환성 확인 여부**: 기존 플러그인과의 충돌 검토 결과

### 리뷰 프로세스

1. PR을 생성하면 리뷰어가 배정됩니다.
2. 리뷰 피드백이 있으면 반영 후 재요청합니다.
3. 승인 후 `main` 브랜치에 머지됩니다.
