# Exploratory Data Analysis: Errata and Code

Errata and runnable code for **Exploratory Data Analysis: Descriptive Analysis, Visualization, and Dashboard Design (with Code Snippets in Python)**, by Leandro Nunes de Castro (CRC Press, 2026).

- Website: https://lndecastro.github.io/EDA-Book
- Errata (PDF): [`book/EDA_Book_Errata_v1.0.pdf`](book/EDA_Book_Errata_v1.0.pdf)
- Notebooks: [`book/notebooks`](book/notebooks). Each notebook has an **Open in Colab** badge.

## Build the website locally

```bash
pip install "jupyter-book<2"
jupyter-book build book
```

The site is published to GitHub Pages by the workflow in `.github/workflows/deploy.yml` on every push to `main`.

## Reporting errors

Please [open an issue](https://github.com/lndecastro/EDA-Book/issues) with the page number and a short description.
