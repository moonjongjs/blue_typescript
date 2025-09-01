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
