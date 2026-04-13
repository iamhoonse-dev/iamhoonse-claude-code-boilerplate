# 플러그인 추가 및 문서 작성 구현 계획

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** settings.json에 git-convention, commit-commands 플러그인을 추가하고, README.md와 CONTRIBUTING.md를 신규 작성한다.

**Architecture:** 설정 파일 중심 프로젝트로, JSON 설정 변경 1건과 마크다운 문서 신규 작성 2건으로 구성. 테스트 프레임워크 없이 JSON 유효성 및 문서 구조를 수동 검증한다.

**Tech Stack:** JSON, Markdown

---

## 파일 구조

- Modify: `.claude/settings.json` — enabledPlugins에 2개 항목 추가
- Create: `README.md` — 프로젝트 소개, 빠른 시작, 플러그인 목록, 설정 구조
- Create: `CONTRIBUTING.md` — 기여 가이드 (플러그인 관리, 브랜치, 커밋, PR)

---

### Task 1: settings.json에 플러그인 추가

**Files:**
- Modify: `.claude/settings.json`

- [ ] **Step 1: enabledPlugins에 2개 플러그인 추가**

`.claude/settings.json`의 `enabledPlugins` 객체에 다음 2개 항목을 추가한다:

```json
{
  "enabledPlugins": {
    "superpowers@claude-plugins-official": true,
    "github@claude-plugins-official": true,
    "security-guidance@claude-plugins-official": true,
    "semgrep@claude-plugins-official": true,
    "microsoft-docs@claude-plugins-official": true,
    "explanatory-output-style@claude-plugins-official": true,
    "learning-output-style@claude-plugins-official": true,
    "git-convention@iamhoonse-claude-code": true,
    "commit-commands@claude-plugins-official": true
  },
  "extraKnownMarketplaces": {
    "iamhoonse-claude-code": {
      "source": {
        "source": "github",
        "repo": "iamhoonse-dev/iamhoonse-claude-code"
      }
    }
  }
}
```

- [ ] **Step 2: JSON 유효성 검증**

Run: `python3 -m json.tool .claude/settings.json > /dev/null && echo "Valid JSON"`
Expected: `Valid JSON`

- [ ] **Step 3: 커밋**

```bash
git add .claude/settings.json
git commit -m "feat: enable git-convention and commit-commands plugins"
```

---

### Task 2: README.md 작성

**Files:**
- Create: `README.md`

- [ ] **Step 1: README.md 파일 작성**

```markdown
# iamhoonse-claude-code-boilerplate

Claude Code를 위한 플러그인과 설정이 사전 구성된 보일러플레이트 템플릿입니다.

## 소개

이 프로젝트는 Claude Code 작업 환경을 빠르게 구성할 수 있도록 만들어진 **GitHub 템플릿 저장소**입니다.
자주 사용하는 플러그인과 마켓플레이스 설정이 미리 포함되어 있어, 새 프로젝트를 시작할 때 반복적인 설정 작업을 줄여줍니다.

GitHub에서 **"Use this template"** 버튼을 클릭하여 이 보일러플레이트 기반의 새 저장소를 바로 만들 수 있습니다.

## 빠른 시작

1. 이 저장소 페이지에서 **"Use this template"** → **"Create a new repository"** 를 클릭합니다.
2. 새 저장소 이름을 입력하고 생성합니다.
3. 생성된 저장소를 clone합니다:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```
4. Claude Code에서 프로젝트를 열면 사전 설정된 플러그인이 자동으로 활성화됩니다.

## 플러그인 목록

### 공식 마켓플레이스 (claude-plugins-official)

| 플러그인 | 설명 |
|---------|------|
| superpowers | 구조화된 개발 워크플로우 (브레인스토밍, TDD, 계획, 디버깅, 코드 리뷰) |
| github | GitHub 이슈 및 PR 연동 |
| security-guidance | 보안 가이드라인 제공 |
| semgrep | 정적 코드 분석 |
| microsoft-docs | Microsoft 공식 문서 참조 |
| explanatory-output-style | 설명적 출력 스타일 |
| learning-output-style | 학습 지향 출력 스타일 |
| commit-commands | 커밋 관련 명령어 |

### 커스텀 마켓플레이스 (iamhoonse-claude-code)

| 플러그인 | 설명 |
|---------|------|
| git-convention | Git 컨벤션 가이드 |

## 설정 구조

| 파일 | 역할 | Git 추적 |
|-----|------|----------|
| `.claude/settings.json` | 공유 설정 (마켓플레이스 등록, 플러그인 활성화) | O |
| `.claude/settings.local.json` | 개인 설정 (API 키, 로컬 환경 등) | X |
| `CLAUDE.md` | 프로젝트 가이드 (Claude Code 동작 지시) | O |

## 라이선스

MIT
```

- [ ] **Step 2: 문서 구조 확인**

README.md가 설계 문서의 모든 섹션을 포함하는지 확인한다:
- 프로젝트 제목 및 한 줄 소개 ✓
- 소개 (GitHub 템플릿 프로젝트 언급) ✓
- 빠른 시작 (템플릿 사용 흐름) ✓
- 플러그인 목록 (마켓플레이스별 테이블) ✓
- 설정 구조 ✓
- 라이선스 ✓

- [ ] **Step 3: 커밋**

```bash
git add README.md
git commit -m "docs: add README with project overview and plugin list"
```

---

### Task 3: CONTRIBUTING.md 작성

**Files:**
- Create: `CONTRIBUTING.md`

- [ ] **Step 1: CONTRIBUTING.md 파일 작성**

```markdown
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
```

- [ ] **Step 2: 문서 구조 확인**

CONTRIBUTING.md가 설계 문서의 모든 섹션을 포함하는지 확인한다:
- 시작하기 (fork & clone) ✓
- 플러그인 관리 (추가/제거, 이름 규칙, 호환성) ✓
- 브랜치 전략 (main 보호, 네이밍) ✓
- 커밋 컨벤션 (Conventional Commits, 예시) ✓
- PR 가이드라인 (작성 내용, 리뷰 프로세스) ✓

- [ ] **Step 3: 커밋**

```bash
git add CONTRIBUTING.md
git commit -m "docs: add CONTRIBUTING guide with plugin and PR guidelines"
```
