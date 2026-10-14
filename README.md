# [초급프로젝트(2분반)] 과제1 포트폴리오 사이트 제작

초급프로젝트 과제1.

## 사용 환경
- OS:
- Python:
- Hugo: 
- Theme: Hugoplate

## 설치 및 로컬 실행
\`\`\`bash
git clone https://github.com/juyeon777/assignment001-MyWebPage.git
cd assignment001-MyWebPage
hugo server -D
\`\`\`
로컬 확인: http://localhost:1313

## 콘텐츠 수정 및 재배포
1. 콘텐츠는 'content/' 폴더 내 Markdown 파일에서 수정
2. 전역 설정은 'hugo.toml'에서 수정 (baseURL 등)
3. 수정 후:
\`\`\`bash
git add .
git commit -m "메시지"
git push origin main
\`\`\`
4. push 시 `.github/workflows/[워크플로파일명].yml`이 자동 실행되어 GitHub Actions가 빌드·배포 수행
5. 배포 상태 확인: [Actions URL]
6. 반영 확인: [공개 사이트 URL]

## 테마 출처 및 라이선스
- 테마명: Hugoplate
- 원본 저장소: https://github.com/zeon-studio/hugoplate
- 라이선스: [예: MIT License] — LICENSE 파일 참고
- 이 저장소의 콘텐츠(자기소개, 활동 내용)는 본인이 직접 작성했으며, 일부 텍스트는 AI(예: Claude/ChatGPT)의 도움을 받아 초안을 작성 후 직접 검토·수정함

## 🙈 제외 파일 (P55)
`.gitignore`로 다음 파일 제외: Hugo 빌드 결과물(`public/`, `resources/`), OS/IDE 임시파일(`.DS_Store`, `.vscode/` 등)