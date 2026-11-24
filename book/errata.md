# Corrections and Clarifications to the First Printing

**Version 1.2, November 2026.** Applies to the first printing. Page numbers refer to the printed book.

{download}`Download the corrections and clarification file as a PDF <EDA_Book_Errata.pdf>`

There are 68 entries in five categories. Within each category the entries are in page order; the IDs (E01–E68) follow the page order of the whole list and are used in the notebooks, where each corrected listing is marked with its ID.

- **[Corrections](#corrections)** (33): Statements, values or formulas that need correction.
- **[Clarifications](#clarifications)** (9): Text that is correct but imprecise, incomplete, or easy to misread.
- **[Notation](#notation)** (5): Symbols changed for consistency.
- **[Code updates](#code-updates)** (6): Changes to code listings and their printed outputs.
- **[Editorial](#editorial)** (15): Typos, misspelled names, and labels.

(corrections)=
## Corrections

Statements, values or formulas that need correction.

| ID | Page | Location | Printed | Correction |
|---|---|---|---|---|
| <a id="e07"></a>**E07** | 14 | Sec. 1.4.1 | "In the early 1950s, Norbert Wiener (1950) coined the term cybernetics". | "In 1948, Norbert Wiener coined the term cybernetics." Delete the reference Wiener (1950), which is not cited elsewhere. |
| <a id="e08"></a>**E08** | 26 | Table 2.4 | Qualitative data described as "Non-statistical", "Subjective" and "Semi- or Unstructured". | Delete these three rows. Categorical data can be structured, objectively recorded and analyzed statistically (e.g., frequency tables, contingency tables, chi-square). |
| <a id="e10"></a>**E10** | 27 | Sec. 2.3.4 | "static (stationary) or dynamic (non-stationary)". | Delete "(stationary)" and "(non-stationary)". A (weakly) stationary time series has a constant finite mean and variance, and an autocovariance that depends only on the lag; this is not the same as data that do not change. |
| <a id="e12"></a>**E12** | 55 | Table 3.2 | Cumulative Frequency (%) for (13.32, 16.65] and (16.65, 19.98]: 55.32 and 40.81. | 30.56 and 55.32. In Code 3.2, value_counts() sorts by frequency, so add .sort_index() before cumsum(): ftable = pd.cut(SShape, fbins).value_counts().sort_index(). |
| <a id="e18"></a>**E18** | 67 | Table 3.5 | Geometric and harmonic means: Existence "Always"; Geometric mean sensitivity "Low". | Existence: "Positive values (equals 0 if any value is 0)" (geometric mean) and "Non-zero values" (harmonic mean). Sensitivity to outliers: "Low (large values); high (values near zero)" (both means). |
| <a id="e19"></a>**E19** | 68–69 | Code 3.8 output and Sec. 3.2.2.1 | Geometric and harmonic means reported and interpreted for temp (°C), ISI and rain (which contain zeros). | Remove the geometric and harmonic means for temp, which is in °C (interval scale). For the zero-containing variables ISI and rain, omit these summaries here. Close mean and median values are consistent with, but do not prove, symmetry. |
| <a id="e21"></a>**E21** | 71 | Sec. 3.2.3.6 | CV "is presented as the percentile ratio" and "is useful … when the mean … is close to zero". | "The CV is the ratio of the standard deviation to the mean, often expressed as a percentage. It is meaningful for ratio-scale data with a positive mean, and becomes unstable and uninformative when the mean is close to zero." |
| <a id="e22"></a>**E22** | 71 | Table 3.6 | CV: "suitable for data with a mean close to zero". | "Dimensionless; for ratio-scale data with a positive mean; unstable when the mean is close to zero." |
| <a id="e23"></a>**E23** | 72 | Sec. 3.2.4.1 | "A coefficient of variation (CV) equals to 6.08 is a relatively high value. A CV greater than 1 usually indicates high variability", and the conclusion of "a high coefficient of variation". | Code 3.9 already multiplies by 100, so the computed ratio is 6.08%, not 6.08; interpreting it as relative variability requires a meaningful ratio scale. Delete the threshold sentence and change the conclusion to "… a low coefficient of variation". Likewise, the variance does not indicate a wide spread: most values lie close to the mean, with a few low values. |
| <a id="e25"></a>**E25** | 74 | Sec. 3.2.5.2, last para. | Boxplot "highlighting the minimal and maximal values of the distribution in the extremes of the whiskers". | "… highlighting the quartiles in the box, with whiskers extending to the most extreme values that are not outliers and the outliers plotted as individual points." Figure 3.4b shows two such points below the lower whisker. |
| <a id="e27"></a>**E27** | 76 | Sec. 3.2.7, Eq. (3.21) | Eq. (3.21) called "the n-th moment"; "The mean and variance are known as raw moments, and the skewness and kurtosis … are known as standardized moments." | "The r-th standardized moment, μᵣ, of a frequency distribution is given by: [Eq. (3.21) with r] … The mean is the first raw moment, E[x], and the variance is the second central moment, E[(x − μ)²]; the skewness and kurtosis discussed in this section are the third and fourth standardized moments." |
| <a id="e31"></a>**E31** | 77 | Sec. 3.2.7.1, after Eq. (3.23) | "The Pearson first skewness coefficient ranges over the interval [−1,1], where −1 means a perfect negative linear relationship …". | Replace with: "A positive value means that the mean exceeds the mode, which commonly occurs in unimodal right-skewed distributions; a negative value means the reverse. The coefficient is not restricted to [−1, 1] and is not a correlation coefficient." |
| <a id="e32"></a>**E32** | 77–78 | Code 3.11 and its output; Figure 3.5 | The "First Skewness Coefficient" is computed as (mean − midpoint)/std, giving −1.67 (right skew) and 1.81 (left skew); the figures plot the midpoint although the caption and text refer to the mode. | The midpoint is not the mode. For continuous data, the mode can be estimated as the peak of a kernel density estimate; (mean − mode)/s is then positive for the right-skewed and negative for the left-skewed illustrative sample. Corrected code (with a fixed random seed) and figures are in the online notebooks. |
| <a id="e35"></a>**E35** | 79 | Eq. (3.25) | "For a sample with n values" but the formula uses N; m₄ called "the fourth standardized moment". | Replace N with n and write the unadjusted sample excess kurtosis as γ₂ = m₄/m₂² − 3, where mᵣ = (1/n) Σ (xᵢ − x̄)ʳ; m₄ is the fourth central moment (not the fourth standardized moment). pandas uses a bias-corrected version of this estimator (see E38). |
| <a id="e40"></a>**E40** | 82 | Last para. of Sec. 3.2.7 | "For n = 1 there is the first moment, which corresponds to the z-score; n = 2 corresponds to the distribution variance …" | "For a distribution with finite, positive variance, the first and second standardized moments equal 0 and 1; when they exist, the third and fourth give the skewness and the kurtosis." A z-score standardizes a single observation, not a moment. |
| <a id="e41"></a>**E41** | 82 | Sec. 3.3, para. 1 | The exponential distribution listed among those that "have a normal shape depending on their parameters". | Delete "and the exponential distribution". The exponential is always strongly right-skewed (skewness 2) whatever its parameter. The t and chi-squared (many degrees of freedom), log-normal (small σ) and beta (equal, large parameters) distributions can approximate a normal shape. |
| <a id="e42"></a>**E42** | 89 | Sec. 3.4.2.4, Eq. (3.34) | The test "assumes that the variables being compared are independent"; n is "the total number of objects" but indexes the sum over cells. | "It tests the null hypothesis that the two variables are independent (the observations themselves are assumed to be independent)." Sum over the c cells of the contingency table (i = 1, …, c); n denotes the total number of objects. |
| <a id="e43"></a>**E43** | 89 | Eq. (3.35) | V = φc = (χ²/n) / min(k − 1, r − 1). | V = √[ (χ²/n) / min(k − 1, r − 1) ]. Code 3.16(b) already includes the square root, so the printed values are correct. |
| <a id="e46"></a>**E46** | 89 | Sec. 3.4.2.6 | The PBCC is described as "a nonparametric measure". | The PBCC is Pearson’s correlation with one variable coded 0/1. Computing it does not require normality; the assumptions for significance testing are a separate issue. Delete "nonparametric". |
| <a id="e47"></a>**E47** | 89 | Eq. (3.36) | p and q defined as numbers of data points in groups 1 and 2. | p is the proportion of data points in group 1, q = 1 − p the proportion in group 2, and s is the standard deviation of x computed with divisor n. |
| <a id="e48"></a>**E48** | 89 | Sec. 3.4.2.6, last para. | "an increase in the continuous variable implies that the binary variable increases". | "When r_pb is positive, the mean of x is higher in group 1 than in group 2, and when r_pb is negative, it is lower." |
| <a id="e49"></a>**E49** | 90 | Sec. 3.4.3, last para. | "the KRCC was determined from χ²". | "Cramér’s V was determined from χ²". |
| <a id="e51"></a>**E51** | 92–93 | Code 3.16(b) output and text | χ² printed as "Chi-Square Correlation Coefficient"; PBCC = 0.46 described as "a strong positive correlation". | χ² is a test statistic, not a correlation coefficient, and grows with n; label it "Chi-square statistic". For r_pb = 0.46: with malignancy coded 1, patients with malignant masses have a higher mean age than those with benign masses in this sample (a moderate association by common conventions). |
| <a id="e52"></a>**E52** | 93 | Sec. 3.4.3.1, para. 1 | "area" has "a weak positive correlation with all other variables … ranging from 0.01 to 0.1". | "near-zero correlations with all other variables, ranging from −0.08 to 0.10". |
| <a id="e54"></a>**E54** | 99 | Sec. 3.6.3, Exercise 2 | "For the “temp” variable … include the values of the geometric and harmonic means in the graph". | Ask for the trimmed and weighted means instead; the geometric and harmonic means do not apply to temperature in °C. |
| <a id="e56"></a>**E56** | 142–143 | Sec. 5.1.2 and Code 5.1 | Whiskers described as going "from the box to the minimal and maximal values", while points beyond Q3 + 1.5 × IQR are also shown as outliers; Code 5.1 names the fences upper_whisker and lower_whisker. | With the usual rule, each whisker ends at the most extreme observation within its fence (Q1 − 1.5 × IQR or Q3 + 1.5 × IQR). Observations beyond a fence are plotted individually; a whisker reaches the min (or max) when there are no observations beyond that fence. Rename the variables upper_fence and lower_fence. |
| <a id="e57"></a>**E57** | 145 | Sec. 5.1.2, last para. | "The position of the median (Q2) within the boxplot gives an idea of the spread of the middle 50% of the values." | "… gives an idea of the symmetry of the middle 50% of the values; the length of the box (IQR) shows their spread." |
| <a id="e58"></a>**E58** | 146 | Sec. 5.1.3 | "outliers appear out of the violin body". | "…and extreme values appear as long, narrow tails of the violin body." With default settings, every observation lies inside the violin, so outliers cannot appear outside it. |
| <a id="e59"></a>**E59** | 147 | Sec. 5.1.3, last para. | A value "significantly smaller than the lower whisker … was not small enough to be marked as an outlier". | "Note that there is one sepal length value for the Iris-virginica species that lies well below the others: it is marked as an outlier (open circle) in the boxplot, and it falls within the lower tail of the violin." Figure 5.5 is correct as printed. |
| <a id="e61"></a>**E61** | 190 | Sec. 6.1.3, para. 2 | Wind speed and mean pressure averages near their minima said to suggest "drier weather with few wind blows"; standard deviation as a percentage of the mean for temperature (°C); the impossible pressures (−3.042 and 7,679.333 hPa) described as possibly invalid. | Replace from "The “humidity” follows…" to the end of the paragraph with: "The “humidity” follows a similar trend, while the “wind_speed” average is closer to its minimal value than to its maximal one. In terms of dispersion, “humidity” has a standard deviation of about 28% of its mean, and “wind_speed” of about 67%. The mean pressure, however, ranges from −3.042 to 7,679.333 hPa: nine values lie outside 950–1,050 hPa, and seven of them are physically impossible. These are reading or entry errors and are treated as missing from here on. After this treatment, the mean pressure varies in [991.4, 1,023.0] hPa, with a mean of 1,008.3 hPa and a standard deviation of 7.4 hPa. Let us now perform a visual analysis of the series." Table 6.2 is correct as printed (raw data). |
| <a id="e62"></a>**E62** | 191–194 | Secs. 6.1.4.1–6.1.4.4, Code 6.1, Figs. 6.1–6.4 | Mean pressure described as "almost constant" with outliers and "almost no correlation" with the other variables; figures drawn with the invalid values. | With the nine suspect values treated as missing (Code 6.1 adds the screening step), the mean pressure follows a seasonal cycle in reverse phase with temperature (higher in winter), is bimodal, shows no box-plot outliers, and is strongly negatively correlated with the mean temperature (r = −0.88; weaker with humidity, 0.33, and wind speed, −0.29). With the invalid values included, these correlations appear close to zero (−0.04, 0.00, −0.02). Figures 6.1–6.4 are redrawn. |
| <a id="e65"></a>**E65** | 232 | Sec. 6.3.5.1, connected components | "a subset of nodes … in which each node is connected to every other node". | For an undirected graph: "a maximal set of nodes in which every pair is joined by a path" (direct links between all pairs would form a clique). |
| <a id="e67"></a>**E67** | 263 | Sec. 7.3, item 3 | "green is generally accessible to individuals with color vision deficiencies". | Red–green deficiency is the most common type, so green and red should not be used as the only contrast. Pair color with labels or icons, or use a blue–orange palette. |

(clarifications)=
## Clarifications

Text that is correct but imprecise, incomplete, or easy to misread.

| ID | Page | Location | Printed | Correction |
|---|---|---|---|---|
| <a id="e03"></a>**E03** | 2 | Sec. 1 intro, para. 2 | EDA "involves any data analysis method that does not include modeling or inference". | "EDA involves data analysis methods aimed at exploration and hypothesis generation, rather than confirmatory testing of prespecified hypotheses (simple exploratory fits, such as a line or a smoother, and their residuals are often used); that is, data are manipulated, summarized, and visualized (presented), …" |
| <a id="e09"></a>**E09** | 26 | Sec. 2.3.3 | "Examples of continuous ratio data are grades in an exam, which usually span a [0, 10] or [0, 5] scale, and market share, …" | "Examples of continuous ratio data are height, elapsed duration, and market share, … Note that being discrete or continuous and the measurement scale are separate properties: a count, for instance, is discrete and ratio scale." |
| <a id="e15"></a>**E15** | 64 | Sec. 3.2.1.7, last para. | "It gives more weight to small observations and is less affected by extreme values compared to the arithmetic mean. This makes it a more reliable measure of central tendency for datasets with widely varying values." | "It gives more weight to small observations and is less affected by large values than the arithmetic mean, which makes it useful for positive data with widely varying values. It requires strictly positive values and is meaningful for ratio-scale data." |
| <a id="e16"></a>**E16** | 65 | Sec. 3.2.1.8 | "… the harmonic mean tends to mitigate the impact of large outliers and aggravate the impact of small ones." | Add: "… its reciprocal formula requires non-zero values, and it is meaningful for positive, ratio-scale data." |
| <a id="e34"></a>**E34** | 78–82 | Sec. 3.2.7.2 | Kurtosis described as measuring the peak. | Kurtosis mainly reflects the tails (the propensity for extreme values); statements about a "sharper" or "flatter" peak are not reliable. |
| <a id="e38"></a>**E38** | 81 | Sec. 3.2.7.2, text before output | "The script uses the skew() and kurtosis() methods of the Scipy library." | Code 3.13 uses the pandas methods DataFrame.skew() and DataFrame.kurtosis() (bias-corrected sample estimators of skewness and excess kurtosis). |
| <a id="e45"></a>**E45** | 89, 90 | Sec. 3.4.2.5; Table 3.7, Cramér’s V row | "variables that have more than two categories". | Cramér’s V measures the strength of association between two categorical variables, including binary ones; for a 2 × 2 table, using the uncorrected chi-square statistic, it equals \|φ\|. In Table 3.7, the Cramér’s V row reads "Two categorical variables, including binary variables". |
| <a id="e55"></a>**E55** | 110, 127, 168, 171 | Figs. 4.4, 4.22, 5.15, 5.16 | Red and green used together. | Figs. 4.4, 5.15 and 5.16 also separate the series by panels, labels or line styles. In the streamgraph of Fig. 4.22, color is the only cue, so readers with red–green color vision deficiency may not tell the series apart; the online code adds a legend and a color-blind-safe palette. |
| <a id="e60"></a>**E60** | 149 | Sec. 5.2.1 | "explanatory" and "response" variables, after "independent"/"dependent" (pp. 23, 96). | Add: "The explanatory and response variables correspond to the independent and dependent variables used earlier." |

(notation)=
## Notation

Symbols changed for consistency.

| ID | Page | Location | Printed | Correction |
|---|---|---|---|---|
| <a id="e11"></a>**E11** | 46 | Eq. (2.2) | z-score normalization written as x′ᵢ. | zᵢ = (xᵢ − mean)/σ, with zᵢ the normalized value (z-score), the same symbol as in Eq. (3.17). |
| <a id="e14"></a>**E14** | 64 | Sec. 3.2.1.5, Eq. (3.4) | Inline sum Σᵢ (fᵢ · Xᵢ); n used for the number of classes. | Σᵢ (fᵢ · xᵢ), with xᵢ the class midpoint as defined in the same sentence. Use k for the number of classes (sums from i = 1 to k); n is reserved for the sample size. |
| <a id="e28"></a>**E28** | 76 | Eq. (3.22) and the line after it | mᵢ = (1/n) Σ (xᵢ − x̄)ⁱ (i used as both index and power); "where x̄ is the mean of xᵢ = i, …, n". | mᵣ = (1/n) Σᵢ (xᵢ − x̄)ʳ, r = 2, 3; γ = m₃ / m₂^(3/2); "where x̄ is the mean of xᵢ, i = 1, …, n". |
| <a id="e33"></a>**E33** | 78–82, 143–147 | Sec. 3.2.7.2, Figs. 3.6, 5.2–5.4 | "Kurtosis" and the same symbol β used both for kurtosis and for excess kurtosis. | The excess-kurtosis formula uses its own symbol, γ₂ = β₂ − 3, where β₂ is the kurtosis of Eq. (3.24). The values reported by SciPy and pandas, and those in Figs. 3.6 and 5.2–5.4, are excess kurtosis (normal = 0). |
| <a id="e64"></a>**E64** | 232 | Eq. (6.8) | Cᵢ = (1/N) Σ Cᵢ. | C̄ = (1/N) Σᵢ Cᵢ (average clustering coefficient). |

(code-updates)=
## Code updates

Changes to code listings and their printed outputs.

| ID | Page | Location | Printed | Correction |
|---|---|---|---|---|
| <a id="e17"></a>**E17** | 66 | Code 3.7(b) | weights = np.random.randn(len(dforest[var])). | Use non-negative weights with a positive total, chosen to represent the intended weighting. Here, weights = dforest["area"] (as in Code 3.8) gives an area-weighted summary. Do not apply gmean() and hmean() to temp, which is in °C (interval scale). |
| <a id="e24"></a>**E24** | 72–73 | Code 3.9 | np.var() and np.std() use the population formulas (ddof = 0), whereas Eqs. (3.12) and (3.14) are the sample formulas; print(f"sIQR …: sIQR{sIQR:.2f}"). | Use np.var(x, ddof=1) and np.std(x, ddof=1) to match the equations (variance 30.47, std 5.52, CV 6.09%; cf. 5.52 on p. 75). Remove the stray "sIQR" in the print statement. |
| <a id="e37"></a>**E37** | 79–80 | Text vs. Figure 3.6 | Text: normal β = 0.01, Laplace β = 3.19; caption: 0.02 and 2.73. | The values come from unseeded random samples and vary between runs. Quote the caption values (excess kurtosis 0.02, −1.19 and 2.73; theoretical values: normal 0, uniform −1.2, Laplace 3). The online notebook fixes the random seed. |
| <a id="e39"></a>**E39** | 81–82 | Code 3.13 output | "wind Kurtosis: 0.05 (Mesokurtic)". | "wind Kurtosis: 0.05 (Leptokurtic)", which is what Code 3.13 prints for any positive excess kurtosis. As the interpretation states, a value this close to zero indicates tails similar to those of a normal distribution. |
| <a id="e63"></a>**E63** | 228 | Code 6.11 | import orca and pio.kaleido.scope.default_format = "svg". | Delete import orca and the Kaleido configuration line; neither is required for this example, which displays the figure with fig.show(). |
| <a id="e68"></a>**E68** | 295 | Appendix B, Code B.1 | Codes B.1–B.7 use np, pd and plt without importing them. | Add these three lines at the start of Code B.1: import numpy as np / import pandas as pd / import matplotlib.pyplot as plt (one statement per line). |

(editorial)=
## Editorial

Typos, misspelled names, and labels.

| ID | Page | Location | Printed | Correction |
|---|---|---|---|---|
| <a id="e01"></a>**E01** | xxiii | Notation | "uniformity and notation". | "uniformity of notation". |
| <a id="e02"></a>**E02** | xxviii | How This Book Was Written and the Use of AI-Assisted Tools | Bing Copilot | Microsoft Copilot |
| <a id="e04"></a>**E04** | 13 | Sec. 1.4.1 | Allan Turing | Alan Turing |
| <a id="e05"></a>**E05** | 14 | Sec. 1.4.1 | Nathanael Rochester | Nathaniel Rochester |
| <a id="e06"></a>**E06** | 14 | Sec. 1.4.1 | Simon Papert | Seymour Papert |
| <a id="e13"></a>**E13** | 63 | Figure 3.3 | x-axis label "wind". | The x-axis label should read "temp" (temperature, °C). The plotted data are correct. |
| <a id="e20"></a>**E20** | 69 | Sec. 3.2.3.1 | "subtracting the largest (x_L) from the smallest value (x_l)". | "subtracting the smallest value (x_l) from the largest (x_L)"; Eq. (3.9) is correct. |
| <a id="e26"></a>**E26** | 75 | Code 3.10 output | area: count 17.00; max 090.84. | count 517.00; max 1090.84. |
| <a id="e29"></a>**E29** | 76–78 and elsewhere | Text, code comments, figure titles, index | Fischer (pp. 76–78, 99, 123, 125, 153–155, 161, 298; index). | Fisher (R. A. Fisher): "Fisher–Pearson skewness coefficient", "Iris dataset of Fisher". |
| <a id="e30"></a>**E30** | 77 | Sec. 3.2.7.1 | Person mode skewness | Pearson mode skewness |
| <a id="e36"></a>**E36** | 79 | Figure 3.6 caption | Wiegner Semicircle | Wigner semicircle |
| <a id="e44"></a>**E44** | 89–93 and index | Sec. 3.4.2.5, Table 3.7, Code 3.16(b), outputs | Cramer, Kramers, Krammers. | Cramér (Harald Cramér): "Cramér’s V". |
| <a id="e50"></a>**E50** | 91–92 | Code 3.16(a) and output | "Kramers Rank Correlation Coefficient (KRCC)". | "Kendall’s Rank Correlation Coefficient (KRCC)". The values are Kendall’s τ and are correct. |
| <a id="e53"></a>**E53** | 95–96, 134 | Fig. 3.9 caption; Sec. 3.5; Sec. 4.2.2.2 | "regressor(s)" used for the fitted line. | Use "regression line" or "fitted line". A regressor is a predictor (explanatory) variable. |
| <a id="e66"></a>**E66** | 232 | Eq. (6.9) | "where E is the number of nodes". | "where E is the number of edges". |

To report a further issue, please [open an issue](https://github.com/lndecastro/EDA-Book/issues).
