# 🔥 기여 가이드라인

Google Python Style Guide 한글 번역 프로젝트에 관심을 가져주셔서 감사합니다. 이 문서는 프로젝트에 기여하고자 하는 분들을 위한 가이드라인입니다.

## 🚀 기여 방법

### 1. 🔍 이슈 확인하기
- 새로운 번역을 시작하기 전에 먼저 [이슈](https://github.com/GideokKim/google-python-style-guide-kr/issues)를 확인해주세요.
- 진행하고자 하는 번역 작업이 이미 진행 중인지 확인합니다.
- 새로운 번역을 시작하려면 이슈를 생성하여 다른 기여자들에게 알려주세요.
- 버그 수정 등 다른 작업을 시작하려면 이슈를 생성하여 다른 기여자들에게 알려주세요.

### 2. ⚙️ 저장소 설정
1. 저장소를 포크(Fork)합니다.
2. 로컬에 클론(Clone)합니다:
   ```bash
   git clone https://github.com/[YOUR_USERNAME]/google-python-style-guide-kr.git
   ```
3. 업스트림 저장소를 추가합니다:
   ```bash
   git remote add upstream https://github.com/GideokKim/google-python-style-guide-kr.git
   ```

### 3. 🎯 작업 시작하기
1. 메인 브랜치를 최신 상태로 유지합니다:
   ```bash
   # upstream의 변경사항 가져오기
   git fetch upstream

   # 로컬 main 브랜치로 이동
   git checkout main

   # upstream의 변경사항을 로컬 main에 병합
   git merge upstream/main

   # 변경사항을 fork한 저장소에 반영
   git push origin main
   ```
2. 새로운 브랜치를 생성합니다:
   ```bash
   git checkout -b feature/translation-[섹션명]
   ```

### 4. 📖 번역 가이드라인

#### ✨ 기본 원칙
- 원문의 의미를 정확하게 전달하는 것을 최우선으로 합니다.
- 기술 용어는 가능한 한 한글로 번역하되, 필요한 경우 영문을 괄호 안에 병기합니다.
- 번역된 문장은 자연스러운 한국어로 읽힐 수 있도록 합니다.

#### 📚 용어 통일
- 프로젝트의 일관성을 위해 주요 용어는 이전에 번역된 내용을 참고하여 통일합니다.

#### 📁 파일 구조
- 번역본은 `google python style guide` 디렉토리 내에 위치합니다.
- 각 섹션별로 별도의 마크다운 파일을 생성합니다.
- 파일명은 영문 원문의 섹션명을 따릅니다.

### 5. 🖥️ 로컬 미리보기 설정 (MkDocs)
- 내가 작업한 내역을 확인하기 위해 로컬에서 GitHub Pages 미리보기를 확인하는 방법입니다.

```bash
# 1. Python 3 버전 확인
python3 --version

# 1 - 1. Python 3가 설치되어 있지 않다면 설치 (macOS 기준)
brew install python

# 2. 가상 환경 생성
python3 -m venv venv

# 3. 활성화
source venv/bin/activate  # zsh/bash 사용자

# 4. 의존성 설치
pip install -r requirements.txt

# 5. 서버 실행
mkdocs serve

# 6. 브라우저에서 확인
http://localhost:8000/google-python-style-guide-kr/

# 7. 서버 종료는 Ctrl+C

# 8. 가상 환경 비활성화
deactivate
```

### 6. 💬 커밋 메시지 작성
커밋 메시지는 다음 형식을 따릅니다:

```
docs: [섹션명] 번역 추가

- 번역한 내용에 대한 간단한 설명
- 특이사항이 있다면 추가 설명
```

### 7. 📤 Pull Request 제출
1. 작업한 브랜치를 푸시합니다:
   ```bash
   git push origin feature/translation-[섹션명]
   ```
2. GitHub에서 Pull Request를 생성합니다.
3. PR 설명에는 다음 내용을 포함합니다:
   - 번역한 섹션 또는 내용
   - 관련된 이슈 번호
   - 특별히 리뷰어가 확인해주었으면 하는 부분

### 8. 👀 리뷰 과정
- 다른 기여자들의 리뷰를 기다립니다.
- 리뷰어의 피드백에 따라 수정이 필요한 경우, 해당 내용을 반영합니다.
- 모든 리뷰가 완료되면 메인 브랜치에 머지됩니다.

## ❓ 질문이나 도움이 필요하다면?
- [이슈](https://github.com/GideokKim/google-python-style-guide-kr/issues)를 통해 질문해주세요.
- 프로젝트 관리자에게 직접 연락이 필요한 경우, 이슈에 @GideokKim을 멘션해주세요.

## ⚖️ 라이선스
이 프로젝트는 [Apache License 2.0](LICENSE)을 따릅니다. 기여하는 모든 내용은 이 라이선스를 따르게 됩니다. 