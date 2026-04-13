# Project Guide

이 프로젝트는 iamhoonse-claude-code 마켓플레이스와 공식 플러그인으로 사전 설정되어 있습니다.

## 개발 워크플로우

모든 기능 개발 및 버그 수정은 다음 5단계를 따릅니다:

1. **Brainstorming** (`superpowers:brainstorming`)
   - 요구사항 파악, 설계 옵션 탐색, 설계 문서 작성

2. **Planning** (`superpowers:writing-plans`)
   - 설계 기반 구현 계획 수립, 태스크 분해

3. **Implementation** (`superpowers:test-driven-development`, `superpowers:executing-plans`)
   - TDD 기반 구현 (RED → GREEN → REFACTOR)

4. **Code Review** (`superpowers:requesting-code-review`)
   - 구현 결과 검증, 품질 확인

5. **Branch Completion** (`superpowers:finishing-a-development-branch`)
   - 머지, PR 생성, 또는 정리

## 브랜치 전략

> `git-convention` 플러그인이 브랜치 네이밍을 자동으로 검증합니다.

- `main` 브랜치는 보호됩니다. 직접 push하지 마세요.
- 작업 브랜치는 다음 네이밍을 따릅니다:
  - `feat/<name>` — 새 기능 추가
  - `fix/<name>` — 버그 수정
  - `docs/<name>` — 문서 변경
  - `chore/<name>` — 기타 유지보수

## 커밋 컨벤션

> `git-convention` 플러그인이 커밋 메시지를 자동으로 검증하고,
> `commit-commands` 플러그인이 커밋 명령어를 지원합니다.

[Conventional Commits](https://www.conventionalcommits.org/) 형식을 사용합니다:

```
<type>: <description>
```

타입: `feat`, `fix`, `docs`, `chore`, `refactor`

## 설정 구조

- `.claude/settings.json` — 공유 설정 (마켓플레이스 등록, 플러그인 활성화)
- `.claude/settings.local.json` — 개인 설정 (git에서 제외됨)
- `.claude/settings.local.json.example` — 개인 설정 예시 (권한 설정 참고용)
