<div align="center">

# GitFolio

**GitHub 링크 하나로 AI가 포트폴리오를 자동 생성해주는 서비스**<br/>
**AI-powered portfolio generator — just drop your GitHub URL**

<br/>

![Status](https://img.shields.io/badge/status-in%20planning-blue?style=flat-square)
![Next.js](https://img.shields.io/badge/Next.js-14-black?style=flat-square&logo=next.js)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3-06B6D4?style=flat-square&logo=tailwindcss)
![Claude API](https://img.shields.io/badge/Claude-API-D97706?style=flat-square)
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
| ✍️ AI 자기소개 생성 | Claude API가 개발자 성향에 맞는 소개 문구를 작성 |
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
- [Next.js 14](https://nextjs.org/) (App Router)
- [TailwindCSS v3](https://tailwindcss.com/)
- [React 18](https://react.dev/)

**Backend**
- Next.js API Routes
- [Claude API](https://www.anthropic.com/) — 자기소개 · 프로젝트 설명 생성
- [GitHub REST API v3](https://docs.github.com/en/rest) — 공개 프로필 · 레포 수집

**Infrastructure**
- [Vercel](https://vercel.com/) — 배포
- [Upstash Redis](https://upstash.com/) — API 응답 캐싱

---

## 시작하기 / Getting Started

> 🚧 현재 개발 준비 단계입니다. 아래 가이드는 추후 업데이트됩니다.
> 🚧 Currently in planning phase. Setup guide will be updated soon.

```bash
# 레포지토리 클론
git clone https://github.com/gitfolio-dev/gitfolio-app.git
cd gitfolio-app

# 패키지 설치
npm install

# 환경변수 설정
cp .env.example .env.local
# .env.local에 ANTHROPIC_API_KEY 입력

# 개발 서버 실행
npm run dev
```

### 환경변수 / Environment Variables

```env
ANTHROPIC_API_KEY=your_claude_api_key
```

---

## 프로젝트 구조 / Project Structure

```
gitfolio-app/
├── app/
│   ├── page.tsx                 # 랜딩 · URL 입력
│   ├── generate/page.tsx        # 생성 진행 화면
│   ├── preview/[id]/page.tsx    # 미리보기 · 편집
│   ├── p/[slug]/page.tsx        # 공개 포트폴리오 페이지
│   └── api/
│       ├── analyze/route.ts     # GitHub 데이터 수집
│       └── generate/route.ts    # Claude API 호출
├── components/
│   ├── portfolio/               # 포트폴리오 섹션 컴포넌트
│   └── ui/                      # 공용 UI 컴포넌트
└── lib/
    ├── github.ts                # GitHub API 클라이언트
    └── claude.ts                # Claude API 래퍼
```

---

## 로드맵 / Roadmap

- [ ] GitHub 프로필 · 레포지토리 수집 API
- [ ] Claude API 연동 및 프롬프트 설계
- [ ] 포트폴리오 렌더러 UI
- [ ] 인라인 편집 기능
- [ ] 공유 링크 발급 및 공개 페이지
- [ ] Vercel 배포 자동화
- [ ] 베타 오픈

---

## 기여하기 / Contributing

현재 팀원을 모집 중입니다. 관심 있으시면 Issues 또는 아래 연락처로 문의해 주세요.

We're currently building the team. Feel free to open an issue or reach out directly.

1. `main` 브랜치에서 직접 push는 금지입니다.
2. 기능 개발은 `feature/기능명` 브랜치에서 진행해 주세요.
3. PR 제출 시 팀원 1인 이상의 리뷰가 필요합니다.
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

## 팀 / Team

| 역할 | 담당 |
|---|---|
| Fullstack / AI | [@chulee-53](https://github.com/chulee-53) |
| Frontend | — |
| Backend | — |

---

## 라이선스 / License

[MIT License](./LICENSE)

---

<div align="center">
  <sub>Built with Claude API · GitHub REST API · Next.js</sub>
</div>
