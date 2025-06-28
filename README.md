# Tbilisi Hack Club - Notebook Viewer

![License: MIT](https://img.shields.io/badge/License-Unlicense-blue.svg) ![GitHub issues](https://img.shields.io/github/issues/tbilisihc/getting-started) ![GitHub forks](https://img.shields.io/github/forks/tbilisihc/getting-started) ![GitHub stars](https://img.shields.io/github/stars/tbilisihc/getting-started) ![Made with Love in Tbilisi](https://img.shields.io/badge/Made%20with%20%E2%9D%A4%EF%B8%8F-in%20Tbilisi-red)

A simple, modern, single-page website that dynamically fetches and renders Jupyter Notebooks (`.ipynb` files) from a GitHub repository. This project is designed to serve as a low-maintenance "Getting Started" guide or blog for the Tbilisi Hack Club.

![Tbilisi Hack Club Viewer Screenshot](https://placehold.co/600x400/f3f4f6/333333?text=Getting+Started)

---

## 🚀 How it Works

This website is a self-contained `index.html` file that uses vanilla JavaScript to:

1.  **Fetch Directory Contents:** On page load, it calls the GitHub API to get a list of all files in a specified folder within a public repository.
2.  **Build Navigation:** It filters for `.ipynb` files, formats their names into clean titles, and dynamically builds a navigation menu in the sidebar.
3.  **Render Notebooks:** When a user clicks on an article link, the site fetches the raw JSON content of the corresponding `.ipynb` file.
4.  **Display Content:** It then parses the notebook's cells:
    * **Markdown cells** are converted to HTML using [Marked.js](https://marked.js.org/).
    * **Code cells** are displayed in formatted blocks with syntax highlighting powered by [Highlight.js](https://highlightjs.org/).

The key advantage of this approach is that **content management is done entirely through Git**. To add, remove, or edit an article, you simply push changes to the notebooks folder in your repository. The website will update automatically.

## ⚙️ Setup & Configuration

This project is designed to be incredibly easy to set up. All you need to do is edit the configuration variables inside the `<script>` tag in the `index.html` file.

```html
<script type="module">
    // --- Configuration ---
    // IMPORTANT: Change these values to your GitHub repository details.
    const GITHUB_OWNER = 'tbilisihc'; // The GitHub username or organization
    const GITHUB_REPO = 'getting-started'; // The repository name
    const GITHUB_PATH = 'notebooks';  // The folder where .ipynb files are
    // -------------------

    // ... rest of the script
</script>
```

1.  **`GITHUB_OWNER`**: The username or organization that owns the repository (e.g., `tbilisihc`).
2.  **`GITHUB_REPO`**: The name of the repository containing the content (e.g., `getting-started`).
3.  **`GITHUB_PATH`**: The specific folder inside the repository where your `.ipynb` article files are located (e.g., `notebooks`).

**Important:** The target GitHub repository **must** be public for the GitHub API to be accessible without authentication.

## ✍️ How to Add Content

Adding a new article is as simple as adding a file to your GitHub repository.

1.  Create a new Jupyter Notebook (`.ipynb` file).
2.  Give it a descriptive name. You can use numbers at the beginning (e.g., `02 Getting Started.ipynb`) to control the order in which they appear on the site.
3.  Add the file to the folder specified in the `GITHUB_PATH` variable in your repository.
4.  Commit and push your changes.

The website will automatically pick up the new file and add it to the article list.

## 🛠️ Technologies Used

* **HTML5**
* **Tailwind CSS** - For modern, utility-first styling.
* **JavaScript (ESM)** - For all client-side logic.
* **Marked.js** - For parsing Markdown content.
* **Highlight.js** - For code syntax highlighting.
* **Octocat** - For GitHub logic

No build step or server is required. Just a web server to serve the static `index.html` file. It can be hosted easily on services like GitHub Pages.

## 📄 License

This project is open-source and available under the [Unlicense License](LICENSE).
