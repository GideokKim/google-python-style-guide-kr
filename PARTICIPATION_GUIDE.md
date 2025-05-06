# 📕 Google python guide 번역 프로젝트 참여 가이드

<aside>
<img src="https://www.notion.so/icons/thought_orange.svg" alt="https://www.notion.so/icons/thought_orange.svg" width="40px" /> Google Python Style Guide 번역 프로젝트는 Python 개발자들에게 도움이 되는 스타일 가이드를 제공하기 위해 Google Python Style Guide를 한국어로 번역하는 프로젝트입니다.

</aside>

<aside>
<br />

**✅Link**

- **사전 등록(구글폼)**: [Google python style guide 번역 용어 수집](https://forms.gle/4ynzEmGWZcnFW9nUA)
- **사전 조회 (Google 스프레드시트)**: [Google Python Style Guide 사전](https://docs.google.com/spreadsheets/d/1OzuoyIpy9bl3KRxMETcVuEOyO0_nL4ip4kMIurU-UVM/edit?usp=sharing)
- **사전 조회 (웹 문서)**: [Google Python Style Guide 사전](https://docs.google.com/spreadsheets/d/e/2PACX-1vRRD6I_ELlSzmkNvfn-JVvTjIVbX91RA4g82AjYUogsvuoLLspPqO4PEKZrSwDUuTDgFwxkk1gSA1eW/pubhtml?gid=1120400211&single=true)
- [기여 방법(CONTRIBUTING.md)](https://github.com/GideokKim/google-python-style-guide-kr/blob/main/CONTRIBUTING.md)

</aside>

<br />

# 🔭 프로젝트 참여 방법

### 1️⃣ 번역할 섹션 선택하기

- Github Issue 목록에서 원하는 Issue를 선택합니다.
- 프로젝트 관리자(기덕님)에게 Assignee로 지정받아 작업을 시작합니다.

### 2️⃣ 번역 진행 및 사전 확인

- 번역을 진행하기 전에 [사전](https://docs.google.com/spreadsheets/d/e/2PACX-1vRRD6I_ELlSzmkNvfn-JVvTjIVbX91RA4g82AjYUogsvuoLLspPqO4PEKZrSwDUuTDgFwxkk1gSA1eW/pubhtml?gid=1120400211&single=true)을 확인하여 기존 번역 용어와의 일관성을 유지합니다.
- 번역할 때 스타일 가이드를 참고하고, 자연스럽고 명확한 표현을 사용합니다.
- 번역한 용어가 새로운 경우, **[Google python style guide 번역 용어 수집](https://forms.gle/4ynzEmGWZcnFW9nUA)** 을 통해 사전에 추가합니다.

### 3️⃣ PR(Pull Request) 제출하기

- 번역이 완료되면, [CONTRIBUTING.md](https://github.com/GideokKim/google-python-style-guide-kr/blob/main/CONTRIBUTING.md)문서를 참고하여 PR을 진행합니다.
- PR 설명란에는 다음 내용을 포함해야 합니다.
  - 번역한 섹션 (표기 : Resolve [번역한 섹션])
  - 구글폼 작성 여부 (`O / X`), 사전 등록 여부 (`O / X`)
  - 번역에 대한 간단한 설명 (선택)
  - 특이사항 기재 (선택)
    - 검토 요청 사항
    - 괄호 내 원문 표현 ex) 표기(annotation)

**👉 PR 설명란 내부 다시 한 번 확인!**

```
[필수]
- Resolve [Translation] 2.6 Nested/Local/Inner Classes and Functions #16
- 구글폼 작성 여부 : o / 사전 확인 여부 : o

[선택]
- 번역한 내용에 대한 간단한 설명
- 특이사항이 있다면 추가 설명 ex) 괄호로 원어 표기
```

### 4️⃣ 리뷰어 검토 후 피드백 반영

- PR이 제출되면, Gemini Code Assist와 리뷰어가 검토를 진행합니다.
- Gemini Code Assist과 리뷰어의 피드백을 반영한 후 다시 업데이트합니다.
- 리뷰 완료 후 승인되면 최종 번역본으로 Merge됩니다.

<br />

# 📖 번역 스타일 가이드

### ✅ 번역 원칙

- 용어는 **일관되게 사용**하고, 기존에 번역된 내용과 [사전](https://docs.google.com/spreadsheets/d/e/2PACX-1vRRD6I_ELlSzmkNvfn-JVvTjIVbX91RA4g82AjYUogsvuoLLspPqO4PEKZrSwDUuTDgFwxkk1gSA1eW/pubhtml?gid=1120400211&single=true)을 참고하여 동일한 표현을 유지합니다.
- 다른 기여자의 파일도 참고를 위해 별도 확인 바랍니다.
- 코드 부분은 원문을 유지하며, 백틱(`)을 사용해 표현합니다.

👉 [자세한 번역 스타일 가이드 확인](./gemini/styleguide.md)

### ✅ [Google python style guide 번역 용어 수집](https://forms.gle/4ynzEmGWZcnFW9nUA)

1. 하나의 폼에는 하나의 용어만 입력 가능합니다.
2. 원문의 용어와 번역한 용어를 별도로 작성합니다.

<br />

# 📌 사전 및 용어 관리

- 번역된 용어는 [사전](https://docs.google.com/spreadsheets/d/e/2PACX-1vRRD6I_ELlSzmkNvfn-JVvTjIVbX91RA4g82AjYUogsvuoLLspPqO4PEKZrSwDUuTDgFwxkk1gSA1eW/pubhtml?gid=1120400211&single=true)에서 확인할 수 있습니다.
- 새로운 용어를 추가할 경우 [Google python style guide 번역 용어 수집](https://forms.gle/4ynzEmGWZcnFW9nUA) 을 통해 등록해주세요.

<br />

**소중한 기여에 감사드립니다!** 😊

---

_최종 업데이트: 2025년 3월 5일_
