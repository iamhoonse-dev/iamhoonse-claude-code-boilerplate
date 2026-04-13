# 개발 플로우 셋업 설계

## 개요

iamhoonse-claude-code-boilerplate 프로젝트에 Superpowers 기반 개발 워크플로우와 GitHub 거버넌스를 셋업한다.
참고 프로젝트(iamhoonse-claude-code)의 개발 플로우를 범용 프로젝트에 맞게 선별 적용한다.

## 변경 사항

### 1. CLAUDE.md 강화

기존 내용(설정 구조)을 유지하면서 다음 섹션을 추가한다:

- **개발 워크플로우**: 5단계 Superpowers 워크플로우 정의
  1. Brainstorming (`superpowers:brainstorming`) — 요구사항 파악, 설계 옵션 탐색, 설계 문서 작성
  2. Planning (`superpowers:writing-plans`) — 설계 기반 구현 계획 수립, 태스크 분해
  3. Implementation (`superpowers:test-driven-development`, `superpowers:executing-plans`) — TDD 기반 구현
  4. Code Review (`superpowers:requesting-code-review`) — 구현 결과 검증, 품질 확인
  5. Branch Completion (`superpowers:finishing-a-development-branch`) — 머지, PR 생성, 또는 정리

- **브랜치 전략**: `git-convention` 플러그인이 자동 검증
  - main 보호, feat/<name>, fix/<name>, docs/<name>, chore/<name>

- **커밋 컨벤션**: `git-convention` 플러그인이 자동 검증, `commit-commands` 플러그인이 명령어 지원
  - Conventional Commits 형식: `<type>: <description>`
  - 타입: feat, fix, docs, chore, refactor

- **설정 구조**: settings.local.json.example 추가 안내

### 2. CONTRIBUTING.md 업데이트

기존 내용에 다음을 추가/수정한다:

- **개발 워크플로우** 섹션 신규 추가 (플러그인 관리 섹션 앞에 배치)
  - 5단계 Superpowers 워크플로우 상세 설명
- **PR 가이드라인** 수정
  - PR 제목에 Conventional Commits 형식 사용 안내
  - 기능 체크리스트 작성 안내
  - 워크플로우 체크리스트 안내
  - 참고 문서 링크 안내

### 3. .github/PULL_REQUEST_TEMPLATE.md (신규)

구조:
- 요약 (변경 사항 설명, Closes # 참조)
- 기능 체크리스트 (구현 기능/수정 사항 나열)
- 워크플로우 체크리스트 (5단계 Superpowers 체크)
- 참고 문서 (설계 문서, 구현 계획, 이슈 링크)

PR 제목은 Conventional Commits 형식을 따른다.

### 4. .github/ISSUE_TEMPLATE/ (신규 3종)

YAML 형식으로 작성:

1. **bug-report.yml**: 버그 설명, 재현 절차, 예상/실제 동작, 환경 정보
2. **feature-request.yml**: 문제 상황, 제안 솔루션, 대안
3. **documentation-improvement.yml**: 대상 문서, 현재 문제, 개선 제안

### 5. .claude/settings.local.json.example (신규)

권한 설정 예시 파일:
- WebFetch: raw.githubusercontent.com, api.github.com, docs.anthropic.com
- Bash: git add, git commit, git push

사용자는 이 파일을 `.claude/settings.local.json`으로 복사하여 사용한다.

## 변경하지 않는 것

- `.claude/settings.json` — 이미 플러그인 설정 완료
- `.gitignore` — settings.local.json.example은 git 추적 대상이므로 변경 불필요

## 대상 사용자

범용 프로젝트 사용자 (특정 기술 스택에 종속되지 않음)

## 제약 사항

- 마켓플레이스 특화 요소(marketplace registration, plugin-dev 스킬) 제외
- 테스트 프레임워크가 없는 프로젝트에서도 적용 가능한 워크플로우
- 이슈 템플릿은 범용적으로 작성 (특정 도메인 필드 없음)
