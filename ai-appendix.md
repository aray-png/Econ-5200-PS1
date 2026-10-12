# AI Appendix

## Task 4.1: Adversarial Review

### Prompt as sent
"What is the strongest objection to using a $500 cutoff as the B2B exclusion rule,
and what evidence would settle it?"

### Raw reply
The strongest objection is that the $500 cutoff is arbitrary and chosen with hindsight.
After looking at the B2B data and knowing the ground truth, any cutoff in the right
range would look principled. On a real dashboard with no hidden is_b2b label you would
not know where to draw the line, and a different cutoff gives a different answer.

### Changes made
- Added a percentile table to show the gap is visible without the label.
- Added a cutoff sweep ($200 to $1,500) to show the answer is stable across the range.
- Added a log-scale histogram to make the two populations visible without any labels.
- Shortened the written response to four sentences as required.

---

## Task 4.2: Board Slide

### Prompt as sent
"Write a board slide in 150 words or fewer covering the headline number,
the correction, the confidence, and the one thing still needed before acting on it."

### Raw reply
First draft was 180 words and used technical language (lognormal, IQR, contamination).
Rejected because it exceeded the word limit and would not land with a non-technical board.

### Changes made
- Cut to under 150 words.
- Replaced statistical terms with plain language.
- Made the headline the first line so the board sees the conclusion immediately.
- Kept the uncertainty and the one outstanding question at the end.
