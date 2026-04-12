# 플러그인 추가 및 문서 작성 설계

## 개요

iamhoonse-claude-code-boilerplate 프로젝트에 git-convention, commit-commands 플러그인을 추가하고,
README.md와 CONTRIBUTING.md 문서를 새로 작성한다.

## 변경 사항

### 1. settings.json 플러그인 추가

`enabledPlugins`에 다음 두 항목을 추가한다:

- `git-convention@iamhoonse-claude-code`
- `commit-commands@claude-plugins-official`

### 2. README.md 신규 작성 (한국어)

구조:

- **프로젝트 제목 및 한 줄 소개**
- **소개**: 보일러플레이트의 목적, GitHub 템플릿 프로젝트임을 명시, "Use this template" 버튼 안내
- **빠른 시작**: 템플릿으로 새 저장소 생성 → clone → Claude Code에서 사용하는 흐름
- **플러그인 목록**: 마켓플레이스별 테이블 (공식 / 커스텀), 각 플러그인 역할 한 줄 설명
- **설정 구조**: settings.json, settings.local.json, CLAUDE.md 역할 설명
- **라이선스**

### 3. CONTRIBUTING.md 신규 작성 (한국어)

구조:

- **시작하기**: fork & clone 방법
- **플러그인 관리**: 추가/제거 방법, 이름 규칙(name@marketplace), 호환성 주의사항
- **브랜치 전략**: main 보호, feature/*/fix/* 네이밍
- **커밋 컨벤션**: Conventional Commits 형식, 예시
- **PR 가이드라인**: PR 작성 내용, 리뷰 프로세스

### 4. CLAUDE.md

현재 상태 유지 (변경 없음).

## 대상 사용자

오픈소스 기여자 (한국어 사용자 중심)

## 제약 사항

- 테스트 프레임워크 없음 (설정 파일 중심 프로젝트)
- Superpowers 플러그인과 충돌 가능한 플러그인은 enabledPlugins에 포함하지 않음
