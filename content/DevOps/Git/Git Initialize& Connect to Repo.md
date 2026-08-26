---
link:
  - "[[Git]]"
---
```bash
cd /path/to/your/empty-folder

git init

git branch -M main
git remote add origin <your-repo-url>

echo "# My Repository" > README.md

git add README.md
git commit -m "Initial commit"
git push -u origin main
```