# How to use the notebooks

## In the browser (no installation)

1. Open a notebook and click **Open in Colab** (the badge at the top, or the rocket icon on this site).
2. Run the first cell (**Setup**). It installs any missing packages and downloads the data files that the chapter needs.
3. Run the listings in order. Some listings reuse data loaded by an earlier one.

## On your computer

```bash
git clone https://github.com/lndecastro/EDA-Book.git
cd EDA-Book
pip install -r requirements.txt
jupyter lab book/notebooks
```

## Two versions of each listing

- **Book version:** the code as printed in the book, with the corrections and clarifications applied.
- **Print-quality version:** shown where the printed figures used extra formatting (font sizes, figure size). It also saves the figure as an SVG file.

## Data

Most datasets are downloaded from their sources: the UCI Machine Learning Repository (through the `ucimlrepo` package), scikit-learn, seaborn, Plotly, NLTK and NetworkX. Files that are not available from a stable public source are in the [`data`](https://github.com/lndecastro/EDA-Book/tree/main/data) folder of the repository.

Random examples now use a fixed seed (`np.random.seed(42)`), so your results will match the notebooks. They may differ slightly from the numbers printed in the book, which were produced without a seed.
