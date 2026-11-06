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
