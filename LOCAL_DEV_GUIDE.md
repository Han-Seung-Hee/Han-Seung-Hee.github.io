# 로컬 개발 가이드

> Dev Container 대신 로컬 환경에서 개발하는 가이드입니다.

## 📋 사전 요구사항

- **Ruby 3.3+** (현재: 3.3.6)
- **Bundler** (현재: 2.5.22)
- **Git**

확인 방법:
```bash
ruby --version
bundler --version
```

## 🚀 시작하기

### 1단계: 의존성 설치
```bash
cd /Users/xorhd1222/WebstormProjects/Han-Seung-Hee.github.io
bundle install
```

### 2단계: 개발 서버 실행
```bash
bundle exec jekyll serve --livereload
```

**출력 예시:**
```
    Server running... press ctrl-c to stop.
      Auto-regeneration: enabled for '.'
      LiveReload address: http://127.0.0.1:35729
```

### 3단계: 브라우저에서 확인
```
http://localhost:4000
```

## 🔥 편리한 단축 명령어

빠른 실행을 위해 `tools/run.sh`에 다음 추가:

```bash
#!/bin/bash

# macOS에서 Jekyll 개발 서버 실행
cd "$(dirname "$0")/.."

echo "📦 의존성 확인..."
bundle check >/dev/null 2>&1 || bundle install

echo "🚀 Jekyll 서버 시작..."
echo "👉 http://localhost:4000"
echo ""

bundle exec jekyll serve --livereload
```

### 실행:
```bash
./tools/run.sh
```

## 📝 블로그 포스트 작성

### 새 포스트 생성
`_posts/YYYY-MM-DD-title.md` 형식으로 파일 생성:

```markdown
---
title: "포스트 제목"
date: 2024-02-06 09:00:00 +0900
categories: [카테고리]
tags: [태그1, 태그2]
---

## 본문 시작

마크다운으로 작성...
```

### 주의사항
- 날짜 형식: `YYYY-MM-DD HH:MM:SS +0900`
- 타임존: `+0900` (한국)
- 파일명: 날짜와 제목이 일치해야 함

## 🔄 실시간 업데이트

- **LiveReload** 활성화됨
- 파일 저장 시 자동 빌드 및 브라우저 새로고침
- `_config.yml` 수정 시는 서버 재시작 필요

## 🐛 문제 해결

### 포트 4000이 이미 사용 중인 경우
```bash
bundle exec jekyll serve --livereload --port 4001
```

### 의존성 재설치
```bash
bundle install --redownload
```

### 캐시 초기화
```bash
rm -rf .jekyll-cache _site
bundle exec jekyll serve --livereload
```

## 📱 모바일에서 테스트

로컬 네트워크에서 접근:
```bash
bundle exec jekyll serve --livereload -H 0.0.0.0
```

그 후 같은 네트워크의 다른 기기에서:
```
http://YOUR_MAC_IP:4000
```

## 🎯 배포 전 체크리스트

```bash
# 1. HTML 검증
bundle exec htmlproofer _site --disable-external

# 2. 빌드 확인
bundle exec jekyll build

# 3. 브라우저에서 모든 페이지 확인
# - Home, Categories, Tags, Archives, About
# - 각 포스트 링크 확인
# - 댓글 (Giscus) 로드 확인
```

## 📚 참고 링크

- [Jekyll 공식 문서](https://jekyllrb.com/docs/)
- [Chirpy 테마 가이드](https://github.com/cotes2020/jekyll-theme-chirpy/wiki)
- [Kramdown 마크다운 문법](https://kramdown.gettalong.org/syntax.html)

---

**마지막 수정**: 2026-02-06  
**상태**: ✅ 로컬 환경 완성

