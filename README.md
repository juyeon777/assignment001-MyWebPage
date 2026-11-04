# [초급프로젝트(2분반)] 과제1 포트폴리오 사이트 제작

초급프로젝트 과제1.

## 사용 환경

배포 워크플로(`.github/workflows/hugo-pages.yml`)와 같은 버전을 씁니다.

| 도구          | 버전                                                                |
| ------------- | ------------------------------------------------------------------- |
| Hugo Extended | 0.165.0 (`site/config/_default/module.toml` 기준 0.158.0 ~ 0.165.0) |
| Go            | 1.27.1 (Hugo 모듈 내려받기용)                                       |
| Node.js       | 24                                                                  |
| Python        | 3.12                                                                |
| Dart Sass     | 1.105.0                                                             |

Hugo는 반드시 **extended** 빌드여야 합니다. `hugo version` 출력에 `extended`가 있는지 확인하세요.

## 설치 및 로컬 실행

이 저장소의 Hugo 사이트는 저장소 루트가 아니라 **`site/`** 에 있습니다.
빌드는 `.github/pages_build.py`가 담당하며, Actions와 같은 스크립트를 로컬에서도 그대로 씁니다.

```bash
git clone https://github.com/juyeon777/assignment001-MyWebPage.git
cd assignment001-MyWebPage

# 1) 의존성 설치 (Hugo 모듈, npm 패키지, postcss/tailwind/pagefind)
python3 .github/pages_build.py --dependencies

# 2) 빌드 -> public/
SITE_BASE_URL=http://localhost:8000/ python3 .github/pages_build.py --build

# 3) 결과 확인
python3 -m http.server 8000 --directory public
```

로컬 확인: <http://localhost:8000>
배포 사이트: <https://juyeon777.github.io/assignment001-MyWebPage/>

## 콘텐츠 수정 및 재배포

### 수정할 파일 위치

| 바꿀 내용        | 파일                                             |
| ---------------- | ------------------------------------------------ |
| 홈 배너          | `site/content/english/_index.md`                 |
| 자기소개(About)  | `site/content/english/about/_index.md`           |
| 대표 활동 글     | `site/content/english/blog/post-1.md`            |
| 대표 활동 목록   | `site/content/english/blog/_index.md`            |
| 사이트 제목·언어 | `site/hugo.toml`                                 |
| 로고·푸터·SEO    | `site/config/_default/params.toml`               |
| 메뉴             | `site/config/_default/menus.en.toml`             |
| 소셜 링크        | `site/data/social.json`                          |
| 이미지           | `site/static/images/` (본문에서는 `/images/...`) |

배포 주소(`baseURL`)는 `.github-pages.json`과 `site/pages.json`이 관리하므로 직접 고치지 않습니다.

### 재배포 절차

```bash
git add .
git commit -m "수정 내용"
git push origin main
```

1. `main`에 push하면 `.github/workflows/hugo-pages.yml`이 자동 실행됩니다.
2. 배포 상태 확인: <https://github.com/juyeon777/assignment001-MyWebPage/actions>
3. 워크플로가 `build` → `deploy` 두 단계를 모두 통과하면 반영됩니다.
4. 공개 화면 확인: <https://juyeon777.github.io/assignment001-MyWebPage/>

변경이 바로 안 보이면 브라우저 캐시를 비우고 새로고침하세요.

## 테마 출처 및 라이선스
- 테마명: Hugoplate
- 원본 저장소: https://github.com/zeon-studio/hugoplate
- 라이선스: [예: MIT License] — LICENSE 파일 참고
- 이 저장소의 콘텐츠(자기소개, 활동 내용)는 본인이 직접 작성했으며, 일부 텍스트는 AI(예: Claude/ChatGPT)의 도움을 받아 초안을 작성 후 직접 검토·수정함

## 제외 파일 (P55)
`.gitignore`로 다음 파일 제외: Hugo 빌드 결과물(`public/`, `resources/`), OS/IDE 임시파일(`.DS_Store`, `.vscode/` 등)