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
1. 콘텐츠는 'content/' 폴더 내 Markdown 파일에서 수정
2. 전역 설정은 'hugo.toml'에서 수정 (baseURL 등)
3. 수정 후:
\`\`\`bash
git add .
git commit -m "메시지"
git push origin main
\`\`\`
4. push 시 `.github/workflows/hugo-pages.yml`이 자동 실행되어 GitHub Actions가 빌드·배포 수행
5. 배포 상태 확인: https://github.com/juyeon777/assignment001-MyWebPage/actions
6. 반영 확인: https://juyeon777.github.io/assignment001-MyWebPage/

## 테마 출처 및 라이선스
- 테마명: Hugoplate
- 원본 저장소: https://github.com/zeon-studio/hugoplate
- 라이선스: [예: MIT License] — LICENSE 파일 참고
- 이 저장소의 콘텐츠(자기소개, 활동 내용)는 본인이 직접 작성했으며, 일부 텍스트는 AI(예: Claude/ChatGPT)의 도움을 받아 초안을 작성 후 직접 검토·수정함

## 제외 파일 (P55)
`.gitignore`로 다음 파일 제외: Hugo 빌드 결과물(`public/`, `resources/`), OS/IDE 임시파일(`.DS_Store`, `.vscode/` 등)