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
git add README.md
git commit -m "commit"
git branch -M main
git remote add origin https://github.com/moonjongjs/blue_typescript.git
git push -u origin main

```

3. GitHub Actions 워크플로우 만들기
