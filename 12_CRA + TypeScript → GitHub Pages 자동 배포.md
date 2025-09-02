# 12 CRA + TypeScript → GitHub Pages 자동 배포
1. package.json 수정
```json

 },
  "homepage": "https://moonjongjs.github.io/blue_typescript"
}
```
2. GitHub 저장소 준비

```bash
git init

git remote add origin https://github.com/moonjongjs/blue_typescript.git
$ git remote -v
origin  https://github.com/moonjongjs/blue_typescript.git (fetch)
origin  https://github.com/moonjongjs/blue_typescript.git (push)

git init
git config user.name 'moonjongjs'
git config user.email 'moonseonjog@naver.com'
git remote add origin https://github.com/moonjongjs/blue_typescript.git
git add .
git commit -m "commit"
git push origin master

```

3. GitHub Actions 워크플로우 만들기
```bash
mkdir .github
mkdir .github\workflows
notepad .github\workflows\deploy.yml
```

deploy.yml 파일 생성
```yml

name: Deploy CRA TypeScript app to GitHub Pages

# main 브랜치에 push될 때 실행
on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      # 1. 저장소 코드 가져오기
      - name: Checkout code
        uses: actions/checkout@v4

      # 2. Node.js 설치
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20   # 프로젝트 Node 버전에 맞춰 설정

      # 3. 의존성 설치
      - name: Install dependencies
        run: npm ci

      # 4. CRA 빌드 실행 (→ build/ 폴더 생성됨)
      - name: Build project
        run: npm run build

      # 5. GitHub Pages로 배포 (gh-pages 브랜치 자동 생성/업데이트)
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./build   # CRA는 build 폴더

```

4. 자동 배포 준비 완료!
```bash
git add .
git commit -m "commit Add GitHub Actions deploy workflow"
git push origin master

```

5. ✅ GitHub Actions 확인

GitHub 저장소 → Actions 탭 들어가면
지금 push한 워크플로우가 실행 중일 거예요.

녹색 체크 ✅ 뜨면 성공입니다.


6. 직접 실행 트리거
```bash
git add .
git commit -m "trigger deploy workflow"
git push origin master

```

6. 최종 배포 URL

https://moonJongjs.github.io/blue_typescript/
