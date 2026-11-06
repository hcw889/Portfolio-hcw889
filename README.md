# Portfolio : 홍채운

인프라 엔지니어를 꿈꾸는 대학생 홍채운의 개인 포트폴리오 사이트입니다. 2026 초급프로젝트 과제 1로 만들었습니다.

- 사이트: https://hcw889.github.io/Portfolio-hcw889/
- 저장소: https://github.com/hcw889/Portfolio-hcw889

## 사용한 테마와 라이선스

- 테마: [Vintage Web Hugo Theme](https://github.com/madebydia/vintage-web-hugo-theme) (제작: madebydia)
- 라이선스: MIT. 원본 저작권 고지는 [LICENSE](LICENSE)와 [site/themes/template/LICENSE](site/themes/template/LICENSE)에 그대로 두었습니다.
- 테마 원본 설명서: [site/themes/template/README.md](site/themes/template/README.md)
- 배포 준비: 수업에서 제공한 `prepare_github_pages.py`(버전 3.1)로 `site/` 폴더와 GitHub Actions 워크플로를 만들었습니다.

## 폴더 구조와 수정 위치

배포되는 사이트는 `site/` 폴더 하나입니다. 내용을 바꿀 때는 아래 파일을 고칩니다.

| 경로 | 역할 |
|---|---|
| `site/hugo.toml` | 사이트 제목, 언어, 메뉴, 소셜 링크, 표시 옵션 |
| `site/content/_index.md` | 홈 화면 본문 |
| `site/content/about.md` | 소개 페이지 (`/about/`) |
| `site/content/posts/` | 활동 글 (`/posts/글이름/`) |
| `site/static/images/` | 이미지. 글에서는 `/images/파일명`으로 씁니다 |
| `site/layouts/shortcodes/screenshot.html` | 이미지 파일이 있을 때만 그림을 보여 주는 숏코드 |
| `site/themes/template/` | 테마의 HTML 템플릿, CSS, JavaScript |
| `.github/workflows/hugo-pages.yml` | main에 push하면 실행되는 배포 워크플로 |
| `.github/pages_build.py` | Hugo 빌드와 배포 경로 보정을 하는 도우미 |

루트의 `layouts/`, `assets/`, `images/`, `exampleSite/`는 테마 원본 사본이며 배포에는 쓰이지 않습니다.

## 도구 버전

| 도구 | 버전 | 쓰는 곳 |
|---|---|---|
| Hugo Extended | 0.167.0 | GitHub Actions 빌드 (`.github/workflows/hugo-pages.yml`에서 지정) |
| Python | 3.12 (Actions) / 3.13.2 (로컬) | `.github/pages_build.py`, `prepare_github_pages.py` |
| Dart Sass | 1.105.0 | 워크플로가 함께 설치 (이 테마는 Sass를 쓰지 않음) |
| Node.js | 24 | 워크플로가 함께 설치 (이 테마는 npm 패키지가 없음) |
| Go | 1.27.1 | 워크플로가 함께 설치 |

## 빌드와 실행

### GitHub Actions (자동 배포)

main 브랜치에 push하면 `.github/workflows/hugo-pages.yml`이 Hugo를 설치한 뒤 아래 두 명령을 차례로 실행하고, 결과물 `public/`을 GitHub Pages에 배포합니다.

```bash
python .github/pages_build.py --dependencies
python .github/pages_build.py --build
```

`--build`는 `site/` 폴더에서 Hugo를 실행해 `public/`을 만들고, 사이트 안의 주소 앞에 `/Portfolio-hcw889/`를 붙이는 경로 보정을 합니다.

### 로컬 미리보기 (선택)

[Hugo 0.167.0 릴리스](https://github.com/gohugoio/hugo/releases/tag/v0.167.0)에서 Extended 버전(Windows는 `hugo_extended_0.167.0_windows-amd64.zip`)을 받아 `hugo.exe`가 있는 폴더를 PATH에 추가한 뒤 실행합니다.

```bash
cd site
hugo server --config hugo.toml,pages.json --baseURL http://localhost:1313/
```

브라우저에서 http://localhost:1313/ 을 엽니다. 로컬 미리보기는 배포 때의 경로 보정을 하지 않으므로, 최종 확인은 공개 사이트에서 합니다.

## 수정과 재배포

1. 위 "폴더 구조와 수정 위치" 표에서 바꿀 파일을 찾아 고칩니다. 소개 글은 `site/content/about.md`, 활동 글은 `site/content/posts/`, 메뉴와 제목은 `site/hugo.toml`입니다.
2. 바꾼 파일을 커밋하고 main에 push합니다.

   ```bash
   git add site/content/about.md
   git commit -m "content: 소개 페이지 수정"
   git push
   ```

3. 저장소의 [Actions 탭](https://github.com/hcw889/Portfolio-hcw889/actions)에서 "Deploy Hugo to GitHub Pages" 실행이 초록 체크(성공)가 될 때까지 기다립니다. 보통 1–2분 걸립니다.
4. 공개 사이트 https://hcw889.github.io/Portfolio-hcw889/ 를 Ctrl+F5(캐시 무시)나 시크릿 창으로 열어 바뀐 내용을 확인합니다.
5. 실행이 실패하면 Actions에서 실패한 단계의 로그를 열어 원인을 확인하고, 고친 뒤 다시 push합니다.
