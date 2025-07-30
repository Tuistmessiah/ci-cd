# Content

 - CSS/HTML content
 - How to setup a CI/CD

## 🌐 CI/CD Public Website Template

This project is a minimal example of serving static HTML/CSS/JS via GitHub Pages, using GitHub Actions for CI/CD. Ideal for learning or quickly putting a simple site online.

##📁 Project Structure
```bash
/public         # Static site files (index.html, style.css, script.js, etc.)
/__tests__      # Optional: Jest test files
package.json    # Node.js project with test command
.github/workflows/ci-cd.yml   # GitHub Actions CI/CD pipeline
```

## 🚀 How to Deploy Your Static Site Online (via GitHub Actions)

✅ 1. Set Up Your Project
Create a GitHub repo and clone it.

Add your static site inside a /public folder:

```pgsql
public/
  ├── index.html
  ├── style.css
  └── script.js
```
Run:

```bash
npm init -y
npm install --save-dev jest
```

Create a simple test inside __tests__/ if needed (example below).

🛠️ 2. Add GitHub Actions Workflow
Create a file at .github/workflows/ci-cd.yml with the following:

```yaml
name: CI + CD - Deploy Public Folder

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Setup GitHub Pages
        uses: actions/configure-pages@v5

      - name: Upload public folder
        uses: actions/upload-pages-artifact@v1
        with:
          path: public

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## ⚙️ 3. Enable GitHub Pages
Go to your repository:

Settings > Pages

Source = `GitHub Actions`

GitHub will display your live URL (e.g., https://yourusername.github.io/reponame)

## 🧪 Optional: Sample Test (Jest)
Inside __tests__/example.test.js:

```js
test('sample test', () => {
  expect(2 + 2).toBe(4);
});
```