# Vibe Coding W2-2 프로젝트

## 📋 프로젝트 개요
AI 채팅 시스템을 구현하는 프로젝트입니다.

## 🚀 기능
- 실시간 AI 채팅
- 백엔드 API 시스템
- 프론트엔드 인터페이스

## 🛠️ 기술 스택
- **Backend**: FastAPI, Python 3.11
- **Frontend**: Streamlit
- **AI**: OpenAI GPT 모델

## 📁 프로젝트 구조
```
vibe_coding_w2-2/
├── backend/          # 백엔드 API
├── frontend/         # 프론트엔드 UI
├── docs/            # 문서
└── .github/         # GitHub Actions 및 템플릿
```

## 🤖 GitHub Actions
이 프로젝트는 다음과 같은 자동화가 설정되어 있습니다:
- 자동 테스트 실행
- PR 자동 라벨링 및 할당
- 코드 리뷰 자동화
- 이슈 관리 자동화

## 📝 개발 가이드
1. 브랜치 생성: `git checkout -b feature/기능명`
2. 개발 및 테스트
3. 커밋: `git commit -m "[feat] 기능 설명"`
4. PR 생성

## 🧪 테스트 실행
```bash
# 백엔드 테스트
cd backend
pytest

# 프론트엔드 테스트
cd frontend
python -c "import app; print('OK')"
```

---
🎯 **테스트 PR**: GitHub Actions 자동화 테스트를 위한 수정입니다. 