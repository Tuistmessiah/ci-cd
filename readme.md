# Content

 - CSS/HTML/Fetch API content to know for quiz
 - How to setup a CI/CD

### 🧪 What You Should Understand to Score Well:
 - How HTML tags create structure.
 - How to link CSS to HTML.
 - The purpose of semantic tags: header, main, footer, etc.
 - Basic CSS properties for layout and color.
 - How Flexbox helps center or arrange elements.
 - The importance of classes (.box) and IDs (#header) in styling.
 - How to use `fetch` and handle its response

# HTML / CSS / Fetch API

### 🧠 Understanding the HTML and CSS (For Beginners)

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

### CSS Examples

🔹 ID Selector (`#id`)
```html
<p id="intro">Hello world</p>
```

```css
#intro {
  color: red;
}
```

🔹 Class Selector (`.class` with multiple elements)

```html
<p class="highlight">Important</p>
<div class="highlight">Also important</div>
```

```css
.highlight {
  font-weight: bold;
}
```

🔹 Tag Selector (`tagname`)

```html
<h1>This is a heading</h1>
```

```css
h1 {
  font-size: 24px;
}
```

🔹 Combination Selectors

Tag + Class

```html
<p class="notice">Note</p>
```

```css
p.notice {
  color: blue;
}
```

Tag + ID


```html
<div id="box" class="card"></div>
```

```css
div#box {
  border: 1px solid black;
}
```

🔹 Descendant vs Direct Child

Any descendant (`div p`)

```html
<div>
  <section><p>Descendant</p></section>
</div>
```

```css
div p {
  color: green;
}
```

Direct child only (`div > p`)

```html
<div>
  <p>Child</p>
  <section><p>Not matched</p></section>
</div>
```

```css
div > p {
  color: orange;
}
```

🔹 Flex vs Grid

Flex: layout in row or column

```html
<div class="flex-container">
  <div>1</div><div>2</div><div>3</div>
</div>
```

```css
.flex-container {
  display: flex;
  gap: 10px;
}
```

Grid: rows and columns

```html
<div class="grid-container">
  <div>A</div><div>B</div><div>C</div><div>D</div>
</div>
```

```css
.grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 5px;
}
```

🔹 Basic Form Example

```html
<form action="/submit" method="POST">
  <input type="text" name="username" placeholder="Your name">
  <input type="submit" value="Send">
</form>
```

 - ✅ Uses name → data is sent on submit
 - ❌ id alone does not send data

🔹 Basic index.html with JS + CSS

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Sample</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <h1>Hello</h1>
  <script src="script.js"></script>
</body>
</html>
```

🔹 CSS Class vs Inline Style

Class

```html
<p class="green-text">Hello</p>
```

```css
.green-text {
  color: green;
}
```

Inline

```html
<p style="color: green;">Hello</p>
```

 - ✅ Inline applies immediately
 - ❌ Not reusable; avoid in practice

CSS classes and inline styles both apply styles to HTML, but CSS classes are more efficient and maintainable. Classes are defined in a separate stylesheet or `<style>` block, promoting separation of content and presentation. They allow multiple elements to share styling, and changes to a class affect all elements using it, making updates easy. Inline styles, written directly in HTML with the `style` attribute, are useful for quick changes but are not reusable across pages and harder to manage. Overall, CSS classes are better for consistency, scalability, and clean code.


## JavaScript Fetch API

### 🌐 Understanding fetch() and REST API Calls

The `fetch()` function is the modern way to make HTTP requests in JavaScript. It's used to interact with REST APIs and retrieve data from servers.

### 📡 What fetch() Returns

The `fetch()` function returns a **Promise that resolves to a Response object**. This is important to understand:

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    // response is a Response object, not JSON data
    console.log(response.status); // HTTP status code
    console.log(response.ok); // boolean indicating success
    return response.json(); // Parse JSON data
  })
  .then(data => {
    // data is the parsed JSON object
    console.log(data);
  });
```

### 🔄 Steps to Handle JSON REST API Response

There are typically **3 main steps** required:

1. **Call fetch() with the endpoint URL**
2. **Call response.json() on the fetch response** 
3. **Use .then() to process the resulting data**

```javascript
// Step 1: Call fetch with URL
fetch('https://api.example.com/users')
  .then(response => {
    // Step 2: Parse JSON from response
    return response.json();
  })
  .then(data => {
    // Step 3: Process the data
    console.log(data);
    // Use the data (e.g., update DOM, store in variables)
  });
```

### 🛠️ Making REST Calls from JavaScript

The primary approach is using the **asynchronous fetch() function**:

```javascript
// GET request
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data));

// POST request
fetch('https://api.example.com/submit', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ name: 'John', age: 30 })
})
.then(response => response.json())
.then(data => console.log(data));
```

### 📝 Parsing JSON Response

The correct way to parse JSON from a fetch() response is using **response.json()**:

```javascript
fetch('https://api.example.com/data')
  .then(response => {
    // ✅ Correct way
    return response.json();
    
    // ❌ Incorrect ways:
    // response.getJSON() - doesn't exist
    // response.parse() - doesn't exist  
    // JSON.parse(response) - response is an object, not a string
  })
  .then(data => {
    // data is now a JavaScript object
    console.log(data);
  });
```

### 🧠 Key Points to Remember:

- `fetch()` returns a Promise → Response object
- Use `response.json()` to parse JSON data
- Always use `.then()` to handle the asynchronous response
- The Response object contains status, headers, and methods like `.json()`
- `response.json()` also returns a Promise, so you need another `.then()`


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