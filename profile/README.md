<div align="center">

# GitFolio

**GitHub 링크 하나로 AI가 포트폴리오를 자동 생성해주는 서비스**<br/>
**AI-powered portfolio generator — just drop your GitHub URL**

<br/>

![Status](https://img.shields.io/badge/status-in%20development-orange?style=flat-square)
![Next.js](https://img.shields.io/badge/Next.js-16-black?style=flat-square&logo=next.js)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3-06B6D4?style=flat-square&logo=tailwindcss)
![Gemini API](https://img.shields.io/badge/Gemini-API-4285F4?style=flat-square&logo=google)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

</div>

---

## 어떤 서비스인가요? / What is GitFolio?

개발자라면 포트폴리오가 필요하다는 걸 알면서도, 막상 만들려면 막막합니다.
이미 GitHub에 모든 작업물이 있는데 왜 또 정리해야 할까요?

**GitFolio는 GitHub 주소만 입력하면 AI가 프로필과 레포지토리를 분석해
자기소개 포트폴리오 페이지를 자동으로 만들고 공유 링크를 발급해줍니다.**

> Every developer needs a portfolio — but building one from scratch is a hassle.
> GitFolio analyzes your public GitHub profile and repositories using AI,
> then generates a shareable portfolio page automatically. No code, no design decisions.

---

## 주요 기능 / Features

| 기능 | 설명 |
|---|---|
| 🔍 GitHub 자동 분석 | 프로필, 레포지토리, README, 기술 스택을 자동 수집 |
| ✍️ AI 자기소개 생성 | Gemini API가 개발자 성향에 맞는 소개 문구를 작성 |
| 🎨 포트폴리오 자동 구성 | Hero · 기술 스택 · 프로젝트 카드 · Contact 섹션 자동 배치 |
| ✏️ 인라인 편집 | 생성된 내용을 바로 수정 가능 |
| 🔗 공유 링크 발급 | 고유 URL로 즉시 공유 (`/p/username`) |

---

## 사용 방법 / How It Works

```
1. github.com/username 주소 입력
2. AI가 GitHub 데이터 분석 (약 30~60초)
3. 포트폴리오 페이지 자동 생성
4. 내용 수정 후 링크 공유
```

---

## 기술 스택 / Tech Stack

**Frontend**
- [Next.js 16](https://nextjs.org/) (App Router)
- [TailwindCSS v3](https://tailwindcss.com/)
- [React 18](https://react.dev/)

**Backend**
- Next.js API Routes (별도 백엔드 서버 없음)
- [Gemini API](https://aistudio.google.com/) — 자기소개 · 프로젝트 설명 생성
- [GitHub REST API v3](https://docs.github.com/en/rest) — 공개 프로필 · 레포 수집

**Infrastructure**
- [Vercel](https://vercel.com/) — 배포 (GitHub push 시 자동 배포)

---

## 시작하기 / Getting Started

### 1. 레포지토리 클론
```bash
git clone https://github.com/GitFolio-dev/gitfolio-app.git
cd gitfolio-app
```

### 2. 패키지 설치
```bash
npm install
```

### 3. 환경변수 설정
```bash
cp .env.example .env.local
```
`.env.local` 파일을 열고 팀장(이승철)에게 받은 API 키를 입력하세요.

```env
GEMINI_API_KEY=받은_키_여기에_입력
```

### 4. 개발 서버 실행
```bash
npm run dev
```
브라우저에서 `http://localhost:3000` 열리면 성공이에요!

---

## 프로젝트 구조 / Project Structure

```
gitfolio-app/
├── app/
│   ├── page.tsx                  # 랜딩 · URL 입력 페이지
│   ├── generate/page.tsx         # 생성 진행 화면
│   ├── preview/[id]/page.tsx     # 미리보기 · 편집 페이지
│   ├── p/[slug]/page.tsx         # 공개 포트폴리오 페이지
│   └── api/
│       ├── analyze/route.ts      # GitHub 데이터 수집
│       └── generate/route.ts     # Gemini API 호출
├── components/
│   ├── portfolio/                # 포트폴리오 섹션 컴포넌트
│   └── ui/                       # 공용 UI 컴포넌트
└── lib/
    ├── github.ts                 # GitHub API 클라이언트
    └── gemini.ts                 # Gemini API 래퍼
```

---

## 팀원별 담당 파일 / Responsibilities

| 이름 | 역할 | 담당 파일 |
|---|---|---|
| 이승철 [@chulee-53](https://github.com/chulee-53) | 팀장 · Frontend | `app/page.tsx`, `app/preview/`, `app/p/`, `components/` |
| 김현 [@hrxlou](https://github.com/hrxlou) | 부팀장 · Backend | `lib/`, `app/api/` 전체 구조 설계 및 체킹 |
| 이동한 [@leedong0923](https://github.com/leedong0923) | Backend | `lib/github.ts`, `app/api/analyze/route.ts` |
| 이현학 [@hyunhak127](https://github.com/hyunhak127) | Backend | `lib/gemini.ts`, `app/api/generate/route.ts` |

---

## 로드맵 / Roadmap

**1주차**
- [ ] 랜딩 페이지 UI (이승철)
- [ ] GitHub API 연동 (이동한 · 김현)
- [ ] Gemini API 연동 (이현학 · 김현)

**2주차**
- [ ] 미리보기 페이지 UI (이승철)
- [ ] 두 API 연결 및 오류 처리 (김현)

**3주차**
- [ ] 공개 포트폴리오 페이지
- [ ] 전체 연결 테스트 · 버그 수정
- [ ] 베타 오픈

---

## 기여하기 / Contributing

1. `main` 브랜치에 직접 push는 금지입니다.
2. 기능 개발은 `feature/기능명` 브랜치에서 진행해 주세요.
3. PR 제출 시 팀장(이승철) 또는 부팀장(김현) 리뷰가 필요합니다.
4. 커밋 메시지는 [Conventional Commits](https://www.conventionalcommits.org/) 규칙을 따릅니다.

```
feat: 새로운 기능
fix: 버그 수정
docs: 문서 수정
style: 코드 포맷팅
refactor: 리팩토링
chore: 빌드 · 설정 변경
```

---

## 라이선스 / License

[MIT License](./LICENSE)

---

<div align="center">
  <sub>Built with Gemini API · GitHub REST API · Next.js</sub>
</div>
