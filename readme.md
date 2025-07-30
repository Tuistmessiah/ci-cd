# Content

 - CSS/HTML content to know for quizz
 - How to setup a CI/CD

# HTML / CSS

## 🧠 Understanding the HTML and CSS (For Beginners)

This project contains a basic static webpage designed using HTML and CSS. Studying the structure and styles here will help you prepare for any web basics test, including those related to layout, elements, and styling principles.

## 📄 HTML: The Structure of the Page

The HTML file (`index.html`) is the skeleton of your webpage. It uses tags to define the different parts of the content. Here's what you should know:

Key Elements Used:
 - `<!DOCTYPE html>`: Declares the document as HTML5.
 - `<html>`: The root element of the page.
 - `<head>`: Contains metadata like the page `<title>` and link to CSS.
 - `<body>`: Everything visible to the user goes here.

Inside the <body>:

 - `<header>`: Usually holds the logo or top navigation.
 - `<main>`: The main content area. You’ll typically use:
   - `<section>`: A part of the page, often with a heading.
   - `<h1>`, `<h2>`...: Headings (bigger = more important).
   - `<p>`: Paragraphs.
   - `<ul>`, `<li>`: Lists.
   - `<button>` or `<a>`: Clickable elements.
 - `<footer>`: Content at the bottom of the page.

Example:

```html
<main>
  <h1>Welcome</h1>
  <p>This is a simple page.</p>
</main>
```

## 🎨 CSS: The Design of the Page

CSS (Cascading Style Sheets) controls how the HTML looks. It’s linked in the <head> of the HTML:

```html
<link rel="stylesheet" href="style.css">
```

Basic CSS Concepts Used:

 - Selectors (`h1`, `.class`, `#id`): Tell the browser what to style.
 - Colors and Fonts:
   - color: Changes text color.
   - background-color: Changes background.
   - font-family, font-size: Control typography.
 - Box Model:
   - padding: Space inside the element.
   - margin: Space outside the element.
   - border: The edge around an element.

 - Flexbox:
   - Used for responsive layouts (auto-adjust to screen size).
   - display: flex, justify-content, and align-items are important properties.

Example:

```css
body {
  background-color: #f0f0f0;
  font-family: Arial, sans-serif;
}

h1 {
  color: #333;
  text-align: center;
}
```

## 🧪 What You Should Understand to Score Well:
 - How HTML tags create structure.
 - How to link CSS to HTML.
 - The purpose of semantic tags: header, main, footer, etc.
 - Basic CSS properties for layout and color.
 - How Flexbox helps center or arrange elements.
 - The importance of classes (.box) and IDs (#header) in styling.



# CI/CD

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