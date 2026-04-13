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
