# KBOP Platform Dev Guidelines

원활한 협업을 위해 이 문서를 작성했습니다.
문서를 수정하고 싶으면 PR을 올려주세요.

---

## 기술 스택

### 프론트엔드
| 항목 | 기술 |
|------|------|
| 프레임워크 | React 19 |
| 언어 | TypeScript |
| 빌드 | Vite |
| 스타일 | Tailwind CSS |
| 상태관리 | Zustand |
| 서버 상태 | TanStack Query |
| 폼 | React Hook Form + Zod |
| UI 컴포넌트 | Radix UI |
| IDE | VSCode |

### 백엔드 (Python)
| 항목 | 기술 |
|------|------|
| 언어 | Python 3.11 |
| IDE | VSCode |

### 백엔드 (Java) - 도입 예정
| 항목 | 기술 |
|------|------|
| 언어 | Java 25 LTS |
| 프레임워크 | Spring Boot 4.0.x |
| IDE | IntelliJ IDEA Ultimate |

### 인프라
| 항목 | 기술 |
|------|------|
| 클라우드 | 네이버 클라우드 |
| 클라우드 | AWS |
| DB | MSSQL |

---

## 브랜치 전략

`main`은 배포 브랜치, `develop`은 통합 브랜치입니다.
모든 작업은 `develop`에서 브랜치를 만들어 진행합니다.
```
main
└── develop
    ├── feat/...
    ├── fix/...
    ├── chore/...
    └── hotfix/...
```

| 타입 | 용도 |
|------|------|
| `feat/` | 새 기능 |
| `fix/` | 버그 수정 |
| `chore/` | 설정, 패키지, 문서 등 기능 무관 작업 |
| `hotfix/` | 운영 긴급 수정. main에서 직접 분기 |

### 명명 규칙
```
{타입}/{이슈번호}-{짧은설명}
```

이슈 번호 없으면 생략:
```
{타입}/{짧은설명}
```

- 소문자만 사용
- 단어 구분은 하이픈(-) 사용
- 설명은 30자 이내 권장

### 예시
```
feat/42-add-player-stats-api
feat/add-trackman-ingestion
fix/55-null-handling-player-id
fix/login-token-expire
chore/update-ruff-config
hotfix/prod-auth-timeout
```

---

## 커밋 규칙
```
{타입}: {설명}
```

| 타입 | 용도 |
|------|------|
| `feat` | 새 기능 |
| `fix` | 버그 수정 |
| `chore` | 설정, 패키지, 문서 등 기능 무관 작업 |
| `style` | 포맷팅 (코드 동작 무관) |

- 동사로 시작 (추가, 수정, 삭제)
- 마침표 없음
- 50자 이내

### 예시
```
feat: 플레이어 통계 API 추가
fix: 플레이어 ID null 처리 오류 수정
chore: ruff 0.4.1 업데이트
style: ruff 포맷 적용
```

---

## PR 규칙

작업이 끝나면 `develop` 대상으로 PR을 올립니다.
PR은 한 가지 목적만 담는 것을 원칙으로 합니다.

- approve 1인 이상 후 머지
- CI 통과 후 머지
- 머지 방식: Squash and merge
- 머지 후 작업 브랜치 삭제

> **Squash and merge란?**
> PR에 커밋이 여러 개 있어도 머지할 때 하나로 합쳐줍니다.
> develop 브랜치 히스토리가 깔끔하게 유지됩니다.

---

## 코드 스타일

포맷팅은 저장 시 자동 실행되도록 에디터를 설정해주세요.
설정 파일은 이 repo에서 받아 프로젝트 루트에 넣으면 됩니다.

### Python
- 포매터: ruff (format + lint 통합)
- 최대 줄 길이: 100자

설정 파일: [pyproject.toml](./pyproject.toml)
```bash
ruff format .
ruff check . --fix
```

### JavaScript / TypeScript
- 포매터: Prettier
- 들여쓰기: 2 spaces
- 최대 줄 길이: 100자
- 따옴표: single quote

설정 파일: [.prettierrc](./.prettierrc)
```bash
npx prettier --write .
```

### Java (도입 예정)
- Google Java Style Guide 기준
- 들여쓰기: 4 spaces
- 최대 줄 길이: 100자

---

## 온보딩 체크리스트

- [ ] GitHub `kbop-platform` org 초대
- [ ] Slack 워크스페이스 초대 
- [ ] NAS 드라이브 접근 설정
- [ ] IDE 설치
- [ ] Git 설정
```bash
git config --global user.name "본인 이름"
git config --global user.email "회사 이메일"
```

- [ ] SSH 키 등록: https://github.com/settings/keys
- [ ] 코드 스타일 설정 파일 적용 (.prettierrc, pyproject.toml)
- [ ] 첫 PR 올리기
