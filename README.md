# Exploratory Data Analysis: Companion Site

Companion site with runnable code and updates for **Exploratory Data Analysis: Descriptive Analysis, Visualization, and Dashboard Design (with Code Snippets in Python)**, by Leandro Nunes de Castro (CRC Press, 2026).

- Website: https://lndecastro.github.io/EDA-Book
- Corrections and Clarifications (PDF): [`book/EDA_Book_Corrections_and_Clarifications.pdf`](book/EDA_Book_Corrections_and_Clarifications.pdf)
- Notebooks: [`book/notebooks`](book/notebooks). Each notebook has an **Open in Colab** badge.

## Build the website locally

```bash
pip install "jupyter-book<2"
jupyter-book build book
```

The site is published to GitHub Pages by the workflow in `.github/workflows/deploy.yml` on every push to `main`.

## Feedback

To report an issue or suggest an improvement, please [open an issue](https://github.com/lndecastro/EDA-Book/issues) with the page number and a short description.
