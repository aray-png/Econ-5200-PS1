# Econ 5200 PS1 — The Measurement Audit

## Overview

This problem set investigates how data-quality problems can make a dashboard report a misleading year-over-year change in average consumer basket value. Using reproducible simulated transaction data, I compare the true consumer averages with a contaminated dashboard measure, identify the sources of the discrepancy, and evaluate a practical correction.

## Research Question

How can large B2B orders and a change in transaction logging distort the reported average consumer basket, and how can an analyst diagnose the problem without relying on a hidden ground-truth label?

## Data and Method

I use Python with NumPy, pandas, Matplotlib, and SciPy. A seeded random-number generator (`np.random.default_rng(42)`) makes the simulation reproducible. The dataset contains 24,000 simulated consumer transactions across 2023 and 2024. I record the true consumer averages first, then introduce two data problems:

- **B2B contamination:** unusually large business orders are added to the transaction data.
- **Logging change:** in 2024, consumer baskets below $20 are omitted from the logged data.

I compare year-over-year mean changes at each stage, quantify the contribution of each mechanism, and examine basket-value cutoffs using a log-scale histogram and a cutoff sensitivity check.

## Key Findings

- The true consumer average rose only **0.44%** year over year, from **$54.07 in 2023** to **$54.31 in 2024**.
- With both data problems, the dashboard reports a **65.24%** increase.
- The B2B orders contribute an estimated **55.25 percentage points** to the year-over-year gap.
- The logging change contributes an estimated **9.54 percentage points**. It removes **1,047** 2024 consumer baskets, or **8.72%** of that year's consumer baskets.
- Excluding baskets above **$500** brings the apparent year-over-year change down to **7.37%**. The cutoff sensitivity check shows similar results for cutoffs from $300 to $1,500, and the log-scale histogram reveals two distinct populations.

## Interpretation and Limitations

The original dashboard headline substantially overstates consumer spending growth. A basket-value cutoff is a practical diagnostic because it can be chosen from the visible distribution, without using the hidden B2B label. However, it does not recover the missing baskets under $20, so the corrected estimate remains provisional. The next step is to ask whether point-of-sale system logs can recover those omitted transactions.

## Project Structure and Submission Checks

The starter notebook asks for a text explanation for every claim, so the work should remain understandable without rerunning the notebook. The assignment also calls for:

- `src/basket_metrics.py` to be pushed with the notebook, with at least three passing assertions.
- `ai-appendix.md` in the repository, documenting the required AI transcript for Phase 4.
- A successful **Runtime → Restart and run all**.
- The notebook and README to be included in the submission repository.

**AI-use requirement:** The notebook states that AI is not allowed in Phases 1–3 and is required in Phase 4, with the transcript saved in `ai-appendix.md`. Follow the official Canvas assignment brief for the full rules and grading requirements.
