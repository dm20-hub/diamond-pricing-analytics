# Diamond Pricing Analytics

Diagnostic analytics on a 53,940 record diamond sales dataset to identify what actually drives price, and where a naive, unadjusted comparison points to the wrong conclusion.

## Key Findings

- **Carat is the dominant price driver**, correlating with price at 0.92, far ahead of any other single feature.
- **A naive average-price-by-cut comparison is misleading:** Fair-cut diamonds appear to average more ($4,359) than Ideal-cut diamonds ($3,458), only because Ideal-cut stones skew toward smaller carats (median 0.31 vs 0.70).
- **Normalizing by carat reverses the picture:** on a price-per-carat basis, Fair drops to the lowest tier ($3,767) while Premium and Very Good lead ($4,223 and $4,014), the comparison that actually reflects cut quality.
- **Clarity and color behave as expected:** price per carat rises monotonically from the lowest to the highest grade on both scales.
- **146 duplicate records** were identified and removed during cleaning, out of 53,940 original rows.

**Implication:** the core lesson generalizes past diamonds. Any category-level KPI comparison in a business process (price, cost, cycle time) needs to be checked for a confounding size or volume variable before it is used to draw conclusions, since the unadjusted view can point in the exact opposite direction of the adjusted one.

## Project Structure

```
diamond-pricing-analytics/
├── diamond_pricing_analytics.ipynb   # full analysis notebook, executed with outputs
├── charts/                           # exported PNG charts from the notebook
├── requirements.txt
└── README.md
```

## Analysis Steps

1. Data cleaning: null and duplicate checks
2. Price distribution overview
3. Carat as the primary price driver (correlation, scatter plot)
4. Price by cut, unadjusted (the misleading first look)
5. Diagnosing the confound: carat distribution by cut
6. Price per carat by cut, the size-adjusted comparison
7. Price per carat by clarity and color
8. Correlation analysis across numeric features

## Running Locally

```bash
pip install -r requirements.txt
jupyter notebook diamond_pricing_analytics.ipynb
```

## Tools

Python, Pandas, NumPy, Matplotlib, Seaborn, Jupyter

## Dataset

The `diamonds` sample dataset from the official [seaborn-data](https://github.com/mwaskom/seaborn-data) repository (maintained by seaborn's author, Michael Waskom), loaded directly via `seaborn.load_dataset("diamonds")`. Source file: [diamonds.csv](https://github.com/mwaskom/seaborn-data/blob/master/diamonds.csv). 53,940 diamonds with carat, cut, color, clarity, dimensions, and price.
