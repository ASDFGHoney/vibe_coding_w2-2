# GitHub Actions & 자동화 설정

이 디렉토리는 프로젝트의 GitHub Actions 워크플로우와 자동화 설정을 포함합니다.

## 📁 구조

```
.github/
├── workflows/           # GitHub Actions 워크플로우
│   ├── test.yml        # 테스트 자동 실행
│   ├── pr-comment.yml  # PR 자동 댓글
│   ├── pr-assigner.yml # PR 자동 할당
│   ├── pr-labeler.yml  # PR 자동 라벨링
│   ├── pr-code-review.yml # PR 코드 리뷰
│   ├── issue-comment.yml # 이슈 자동 댓글
│   ├── issue-assigner.yml # 이슈 자동 할당
│   └── issue-labeler.yml # 이슈 자동 라벨링
├── ISSUE_TEMPLATE/     # 이슈 템플릿
│   ├── bug_report.md   # 버그 신고 템플릿
│   └── feature_request.md # 기능 요청 템플릿
├── pull_request_template.md # PR 템플릿
└── README.md          # 이 파일
```

## 🤖 GitHub Actions 워크플로우

### 1. 테스트 자동 실행 (test.yml)
- **트리거**: main 브랜치 push, PR 생성/업데이트
- **기능**: 
  - 백엔드 테스트 실행 (pytest)
  - 프론트엔드 테스트 실행
  - 코드 커버리지 보고서 생성
  - 의존성 캐싱으로 빌드 시간 단축

### 2. PR 자동 댓글 (pr-comment.yml)
- **트리거**: PR 생성, 업데이트
- **기능**:
  - PR 생성 시 환영 댓글 작성
  - 리뷰 체크리스트 제공
  - PR 정보 요약 (파일 변경 수, 브랜치 정보 등)
  - PR 업데이트 시 알림 댓글

### 3. PR 자동 할당 (pr-assigner.yml)
- **트리거**: PR 생성, 재오픈
- **기능**:
  - 변경된 파일 경로 기반 코드 소유자 자동 할당
  - PR 작성자를 담당자로 할당
  - 관련 개발자를 리뷰어로 할당
  - 할당 결과 댓글 작성

### 4. PR 자동 라벨링 (pr-labeler.yml)
- **트리거**: PR 생성, 업데이트
- **기능**:
  - PR 제목/내용 기반 라벨 자동 할당
  - 변경 파일 경로 분석으로 기술 스택 라벨링
  - 변경 규모에 따른 라벨링 (major/medium/minor)
  - 특별 파일 변경 감지 (dependencies, database 등)

### 5. PR 코드 리뷰 (pr-code-review.yml)
- **트리거**: PR 생성, 코드 업데이트
- **기능**:
  - 자동 코드 품질 분석
  - Python 코딩 컨벤션 체크
  - 테스트 파일 존재 여부 확인
  - 파일 크기 및 복잡도 분석
  - 코드 품질 점수 산출 및 피드백

### 6. 이슈 자동 댓글 (issue-comment.yml)
- **트리거**: 이슈 생성, 라벨 변경
- **기능**:
  - 이슈 타입별 맞춤 환영 메시지
  - 이슈 품질 체크리스트 제공
  - 라벨 변경에 따른 상태 업데이트 댓글
  - 처리 프로세스 안내

### 7. 이슈 자동 할당 (issue-assigner.yml)
- **트리거**: 이슈 생성, 라벨 할당
- **기능**:
  - 이슈 내용 키워드 분석으로 담당자 할당
  - 라벨 기반 전문가 할당
  - 긴급 이슈 시 팀 리더 추가 할당
  - 할당 근거 및 역할 설명 댓글

### 8. 이슈 자동 라벨링 (issue-labeler.yml)
- **트리거**: 이슈 생성, 편집
- **기능**:
  - 이슈 제목/내용 기반 타입 분류
  - 기술 스택 키워드 감지
  - 우선순위 자동 판단
  - 템플릿 사용 여부 확인
  - 품질 개선 제안

## 🏷️ 라벨 시스템

### PR 라벨
- `feature` - 새로운 기능 추가
- `bugfix` - 버그 수정
- `enhancement` - 기능 개선
- `documentation` - 문서 관련
- `refactoring` - 코드 리팩토링
- `testing` - 테스트 관련
- `urgent` - 긴급 수정
- `breaking-change` - 브레이킹 체인지

### 이슈 라벨
- `bug` - 버그 신고
- `feature` - 새로운 기능 요청
- `enhancement` - 기능 개선
- `question` - 질문
- `documentation` - 문서 관련
- `good-first-issue` - 초보자 적합
- `help-wanted` - 도움 필요
- `priority: high/medium/low` - 우선순위

### 기술 스택 라벨
- `backend` - 백엔드 관련
- `frontend` - 프론트엔드 관련
- `database` - 데이터베이스 관련
- `testing` - 테스트 관련
- `deployment` - 배포 관련
- `security` - 보안 관련

## 👥 팀 멤버 설정

현재 자동 할당 시스템에서 사용하는 팀 멤버:
- `team-leader` - 전체 프로젝트 관리
- `backend-lead` - 백엔드 기술 리드
- `frontend-lead` - 프론트엔드 기술 리드
- `devops-lead` - 인프라 및 배포
- `qa-lead` - 품질 관리 및 테스트
- `security-lead` - 보안 전문가

> ⚠️ **설정 필요**: 실제 GitHub 사용자명으로 업데이트해야 합니다.

## 📋 템플릿 사용법

### 이슈 생성 시
1. GitHub에서 "New Issue" 클릭
2. 적절한 템플릿 선택 (버그 신고 또는 기능 요청)
3. 템플릿의 모든 섹션을 작성
4. 이슈 생성 시 자동으로 라벨링 및 할당 진행

### PR 생성 시
1. PR 생성 시 자동으로 템플릿이 적용됨
2. 모든 체크리스트 항목 검토
3. 관련 이슈 번호 연결
4. 테스트 결과 및 스크린샷 첨부

## ⚙️ 커스터마이징

### 팀 멤버 변경
각 워크플로우 파일에서 팀 멤버 정보를 수정:
```yaml
const teamMembers = {
  'your-github-username': ['keyword1', 'keyword2'],
  // ...
}
```

### 라벨 커스터마이징
GitHub 저장소 설정에서 라벨을 추가/수정한 후, 워크플로우에서 라벨명 업데이트

### 트리거 조건 변경
각 워크플로우의 `on:` 섹션에서 트리거 조건 수정 가능

## 🔧 문제 해결

### 워크플로우가 실행되지 않는 경우
1. GitHub Actions 권한 확인
2. 워크플로우 파일 YAML 문법 확인
3. 저장소의 Actions 탭에서 오류 로그 확인

### 자동 할당이 작동하지 않는 경우
1. 팀 멤버 사용자명이 정확한지 확인
2. 저장소 권한 설정 확인
3. GitHub token 권한 확인

### 라벨링이 부정확한 경우
1. 키워드 매칭 규칙 조정
2. 라벨 존재 여부 확인
3. 수동으로 라벨 수정 후 학습

## 📈 모니터링

GitHub Actions 실행 현황은 저장소의 "Actions" 탭에서 확인 가능:
- 워크플로우 실행 성공/실패 현황
- 실행 시간 및 로그
- 사용량 및 비용 (프라이빗 저장소의 경우)

## 🚀 향후 개선 사항

- [ ] 코드 커버리지 임계값 설정
- [ ] 슬랙/이메일 알림 연동
- [ ] 자동 배포 파이프라인 추가
- [ ] 보안 스캔 자동화
- [ ] 성능 테스트 자동화 