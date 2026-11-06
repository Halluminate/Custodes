Apply the official judge instructions below. The agent's output files are the run outputs, and the reference files are in the Grader Reference Files list. Judge only the delivered files (and the final message where the task asks for a text answer), not the agent's process.

The agent's working directory (/home/model/Desktop; its files are the run outputs) is the final snapshot of a workspace where an LLM agent was asked to complete a complex professional-domain task. The snapshot contains the input/context files the agent was given, and may also contain output/deliverable files the agent created. Determine which files are agent-created outputs versus provided context by comparing your working directory against the CONTEXT FILES listed below - a file that is absent from the context list, or that differs from its context version, is an agent output. The agent's final message may be found in the run record at the task transcript.

Your job is to grade the agent's deliverables against the criteria below. The agent's deliverables are (a) any files it created or modified, and (b) its final message, when the task called for a written answer. The ORIGINAL PROMPT is provided for context only - do not attempt to solve it yourself; grade only what the agent produced.

GRADING SOURCE OF TRUTH - read before assigning any verdict:

- Grade the deliverable the task actually asked for.
  - File deliverable: open and inspect the actual contents of the file.
  - Text deliverable: when the task asks for the answer itself as text with no file expected, the agent's final message IS the deliverable - grade it directly.
  - Some tasks ask for both: grade each file-based criterion against the file and each text-based criterion against the final message.

- The final message counts as evidence ONLY when it is the requested text deliverable. Never use the final message or "I have completed..." / "I updated X" process claims as evidence for what a file contains, or that a file was produced or edited. Such claims are not evidence and must never justify a pass.

- Cite concrete evidence for every verdict: a file name plus the specific content, or the specific passage of the final message. If you cannot locate the required content in the actual deliverable, the criterion FAILS - an unverifiable claim is a fail, not a pass.

- Verify produced OUTPUT, not mechanism. A formula, function, script, or source asset that *should* yield the required result is not enough: compute the value yourself and confirm it matches. For rendered artifacts (images, video, audio, PDFs), inspect the actual rendered output - never infer correctness from generation code, filenames, or logs.

- Distinguish provided inputs from authored deliverables. A delivered file that is byte-identical to a supplied input has NOT been modified; do not credit any required change to it. Confirm required edits are actually present in the delivered version.

- If a required file is missing, empty, a placeholder/stub, or unchanged from its input, fail every criterion that depends on its intended edited contents. An unchanged file still passes criteria whose required content is genuinely present in it; only fail criteria that require content the agent needed to add or change.

- Apply each criterion to exactly what it asks - no more, no less. Do not fail a criterion for a problem it does not mention, and do not pass it by accepting a weaker, broader, or partial result than it specifies.

<original_prompt>
Evaluate the 2026 expansion proposal using the attached materials and recommend whether Dreamy should proceed, and if so where/how to finance it. Summarize your work and export in text-based file.
</original_prompt>

<context_files>
- Board_Dividend_Policy.pdf
- Bramworth_Inc_Form8-K_Q1_FY2026.pdf
- Consolidated_Balance_Sheet_2024-2026.pdf
- Consolidated_Cash_Flow_2024-2026.pdf
- Consolidated_Income_Statement_2022-2026.pdf
- Dreamy_Furniture_Org_Chart.pdf
- Financing_Memo_Credit_Facility.pdf
- Import_Duty_Schedule_2021.pdf
- Modeling_Assumptions_New_Store.xlsx
- New_Store_Performance_History.pdf
- New_Store_Pro_Formas_2026-2029.xlsx
- Screenshot 2025-08-01 at 18.10.25.png
- Screenshot 2025-08-13 at 11.07.42.png
- Screenshot 2025-08-23 at 17.08.28.png
- Site_Evaluation_Chattanooga_TN.pdf
- Site_Evaluation_Columbus_OH.pdf
- Site_Evaluation_Nashville_TN.pdf
- Store_Sales_Forecasts_2022-2027.xlsx
</context_files>

Criteria:

- 'c001': The response explicitly recommends not proceeding with the proposed 2026 new-store expansion. (score: "yes" or "no")
- 'c002': The response justifies the no-go recommendation primarily on the basis of financing capacity or a debt-covenant breach, not solely because a new store's NPV is negative. (score: "yes" or "no")
- 'c003': The response identifies that the FY2025-FY2027 forecast for the Atlanta store incorrectly calculates net sales by adding Returns & allowances to Gross sales instead of subtracting them. (score: "yes" or "no")
- 'c004': The response states that reversing the sign on the Atlanta store's $266K FY2025 Returns & allowances line lowers Atlanta's FY2025 net sales by $532K (accept $527K–$537K). (score: "yes" or "no")
- 'c005': The response identifies that the FY2025-FY2027 forecast for the Richmond store incorrectly calculates net sales by adding Returns & allowances to Gross sales instead of subtracting them. (score: "yes" or "no")
- 'c006': The response states that reversing the sign on the Richmond store's $163K FY2025 Returns & allowances line lowers Richmond's FY2025 net sales by $326K (accept $321K–$331K). (score: "yes" or "no")
- 'c007': The response identifies that the forecast for the Columbia store incorrectly enters the Returns & allowances input as a negative number (~ -$137K) which causes the Gross minus Returns formula to incorrectly add it back. (score: "yes" or "no")
- 'c008': The response states that restoring the Columbia store's FY2025 Returns & allowances input — entered in the forecast as −$137K — to a positive sign lowers Columbia's FY2025 net sales by $274K (accept $269K–$279K). (score: "yes" or "no")
- 'c009': The response identifies that the FY2025-FY2027 forecast for the Greensboro store incorrectly calculates net sales by adding Returns & allowances to Gross sales instead of subtracting them. (score: "yes" or "no")
- 'c010': The response states that reversing the sign on the Greensboro store's $188K FY2025 Returns & allowances line lowers Greensboro's FY2025 net sales by $376K (accept $371K–$381K). (score: "yes" or "no")
- 'c011': The response identifies that the forecast for the Greenville store incorrectly enters the Returns & allowances input as a negative number (~ -$100K) which causes the Gross minus Returns formula to incorrectly add it back. (score: "yes" or "no")
- 'c012': The response states that restoring the Greenville store's FY2025 Returns & allowances input — entered in the forecast as −$100K — to a positive sign lowers Greenville's FY2025 net sales by $200K (accept $195K–$205K). (score: "yes" or "no")
- 'c013': The response reports a corrected FY2026 total-year YoY net-revenue growth for Charlotte within [+2%, +5%]. (score: "yes" or "no")
- 'c014': The response reports a corrected FY2026 total-year YoY net-revenue growth for Atlanta within [+4%, +6%]. (score: "yes" or "no")
- 'c015': The response reports a corrected FY2026 total-year YoY net-revenue growth for Columbia within [0%, +3%]. (score: "yes" or "no")
- 'c016': The response reports a corrected FY2026 total-year YoY net-revenue growth for Greensboro within [−1%, +2%]. (score: "yes" or "no")
- 'c017': The response reports a corrected FY2026 total-year YoY net-revenue growth for Savannah within [+1%, +4%]. (score: "yes" or "no")
- 'c018': The response reports a corrected FY2026 total-year YoY net-revenue growth for Virginia Beach within [−2%, +2%]. (score: "yes" or "no")
- 'c019': The response does not alter Raleigh's FY2026 total-year YoY net-revenue growth from the forecast's reported +5.5%: if the response states a figure for Raleigh, it is within [+5.2%, +5.8%], and the response does not apply a Returns & allowances sign correction to Raleigh, whose forecast already subtracts Returns & allowances correctly. A response that does not state a Raleigh growth figure does not fail this criterion. (score: "yes" or "no")
- 'c020': The response does not alter Charleston's FY2026 total-year YoY net-revenue growth from the forecast's reported +4.0%: if the response states a figure for Charleston, it is within [+3.7%, +4.3%], and the response does not apply a Returns & allowances sign correction to Charleston, whose forecast already subtracts Returns & allowances correctly. A response that does not state a Charleston growth figure does not fail this criterion. (score: "yes" or "no")
- 'c021': The response does not introduce a COGS/import-duty correction based on the stale 2021 duty schedule (blended ≈8.0% of FOB); it treats the import-duty amounts embedded in the 2024–2026 financial statements (≈20% of merchandise cost, e.g., $6.43M ÷ $32.16M in FY2024) as controlling. (score: "yes" or "no")
- 'c022': The response calculates a corrected FY2025 company net sales figure within [$81.5M, $83.0M]. (score: "yes" or "no")
- 'c023': The response states a corrected FY2025 company EBITDA within [$4.4M, $6.4M], built from corrected net sales of about $82.2M, a stable gross margin of approximately 44% (the FY2022–FY2024 historical margin of 43.8%–44.2%), not the ~45% margin embedded in the uncorrected FY2025 forecast, and consolidated operating expenses between the FY2025 plan of $31.21M and the plan with only the remaining (second-half) months trimmed toward FY2024 run-rate levels. An EBITDA above ~$6.4M — e.g., from re-planning already-incurred first-half operating expenses or freezing the full year at FY2024 levels — fails, as does the uncorrected reported $8.12M. (score: "yes" or "no")
- 'c024': The response states a corrected FY2025 company net income within [$1.7M, $3.2M] (= (corrected EBITDA − $1.50M D&A − $0.74M interest + $0.10M investment income) × 75%, evaluated at the response's own corrected EBITDA). (score: "yes" or "no")
- 'c025': The response states the pro-forma Total Debt/EBITDA for a fully debt-funded buildout as a value above the 3.00x limit, within [3.35x, 4.95x]— total funded debt ~$21.6M ($16.5M existing + ~$5.1M buildout) divided by either FY2024A TTM EBITDA ($5.87M–$5.9M → 3.66x–3.68x) or a corrected FY2025E EBITDA of $4.4M–$6.4M (→ 3.38x–4.91x). (score: "yes" or "no")
- 'c026': The response explicitly rejects the ~2.66x pro-forma Total Debt/EBITDA figure as invalid because it is computed on the inflated, uncorrected FY2025E forecast EBITDA of $8.12M. (score: "yes" or "no")
- 'c027': The response concludes that the fully debt-funded buildout causes a covenant breach because the pro-forma Total Debt/EBITDA exceeds the 3.0x limit. (score: "yes" or "no")
- 'c028': The response states the maximum incremental debt permitted under the covenant as 3.0 × its stated covenant-base EBITDA minus $16.5M existing funded debt — about $1.1M–$1.2M on FY2024A TTM EBITDA, and at most ~$2.7M at the top of the accepted corrected range; accept any value from $0M (or a stated negative/no room) up to $2.7M that is consistent with the formula — and notes this is far below the ~$5.1M buildout need. (score: "yes" or "no")
- 'c029': If the response states a covenant maximum incremental debt figure, that figure is consistent with 3.0 × its stated covenant-base EBITDA minus $16.5M (no greater than ~$2.7M) and is not conflated with any residual funding gap remaining after a revolver draw. (score: "yes" or "no")
- 'c030': The response states that the company must hold a minimum liquidity reserve of $4.0M in cash and short-term investments. (score: "yes" or "no")
- 'c031': The response concludes that deployable liquidity above the $4.0M cash + short-term-investments reserve is only about $0.6M–$0.9M (2024: $4.90M − $4.0M = $0.90M; 2025E: $4.84M − $4.0M = $0.84M; 2026E: $4.66M − $4.0M = $0.66M) and cannot bridge the ~$5.1M funding need. (score: "yes" or "no")
- 'c032': The response states that shareholder distributions cannot be cut to self-fund the expansion because there is a committed minimum distribution (~$2.3M/yr) requiring a two-thirds shareholder vote to reduce. (score: "yes" or "no")
- 'c033': The response states that corrected net income leaves little or no cushion above the committed minimum distribution — roughly $0–$0.9M before any discretionary payout, depending on its corrected net income (or roughly $0–$0.3M of discretionary capacity if the historical 80%-of-net-income payout formula is applied) — not enough to self-fund the expansion. (score: "yes" or "no")
- 'c034': The response explicitly rejects treating the facility's undrawn revolver capacity (~$3.5M) as available borrowing capacity exempt from the covenant. (score: "yes" or "no")
- 'c035': The response states that drawing the revolver to $20.0M of total funded debt would result in leverage above the 3.00x limit ($20.0M ÷ corrected FY2025E EBITDA of $4.4M–$6.4M ≈ 3.13x–4.55x; $20.0M ÷ FY2024A TTM EBITDA of $5.87M–$5.9M ≈ 3.39x–3.41x; accept 3.1x–4.6x), causing a covenant breach. (score: "yes" or "no")
- 'c036': If the response considers making the buildout fundable with proper timing by drawing once 2025E EBITDA materializes, it explicitly rejects that argument, noting that the inflated $8.12M EBITDA will not materialize and trailing-twelve-month tests will still breach. A response that does not raise such a timing argument does not fail this criterion. (score: "yes" or "no")
- 'c037': The response uses the 5.25% facility reset rate for the cost of debt / WACC calculation and does not use the stale 3.25% rate. (score: "yes" or "no")
- 'c038': The response identifies Nashville as the only candidate with positive source-supported site-level economics — i.e., the preferred site if financing were available — and explicitly rejects recommending Chattanooga. Identifying Nashville as the best site does not require, and must not be read as, a recommendation to proceed with the expansion. (score: "yes" or "no")
- 'c039': The response treats the Columbus site evaluation as stale or unreliable because it is dated 2019. (score: "yes" or "no")
- 'c040': The response either ignores the Bramworth earnings release or treats it as not a positive read-through for Dreamy's residential/consumer-furniture demand. (score: "yes" or "no")
- 'c041': The response explicitly identifies the macroeconomic / consumer-spending downturn and presents it as a downside risk or sensitivity to the sales forecasts — not merely mentioning that a downturn exists, and not presenting it as a positive or neutral demand signal. (score: "yes" or "no")
- 'c042': The response discounts the new-store unlevered free cash flow at a WACC within [7.1%, 7.7%]. (score: "yes" or "no")
- 'c043': The response applies a corrected new-store gross margin within [43%, 45%] rather than using the pro-forma's 46%. (score: "yes" or "no")
- 'c044': The response's corrected/main DCF shows Years 1–5 sales at Dreamy's historical company-average new-store ramp of approximately 48% / 72% / 89% / 98% / 100% of stabilized sales, with only rounding-level variation (roughly ±1–2 percentage points per year), rather than the pro-forma three-year ramp. (score: "yes" or "no")
- 'c045': The response uses the pro formas' FY2028 stabilized-year net sales as its base case for each candidate site — Nashville $8.5M, Chattanooga $4.9M, and Columbus $6.3M (accept ±$0.1M per site) — and labels any macro-driven sales haircut as a downside case or sensitivity rather than replacing the base case. (score: "yes" or "no")
- 'c046': The response includes maintenance capex equivalent to 2% of the buildout cost per year in the new-store NPV cash flows. (score: "yes" or "no")
- 'c047': The response recovers working capital at exit in the new-store NPV cash flows. (score: "yes" or "no")
- 'c048': The response applies a long-run or terminal growth rate between 2% and 3% in the NPV model. (score: "yes" or "no")
- 'c049': The response calculates the new store's terminal (exit) value as 5.0x the store's year-10 EBITDA. (score: "yes" or "no")
- 'c050': The response states a corrected/main-case Nashville NPV — shown as discounted at a WACC within [7.1%, 7.7%] and reflecting a corrected 43%–45% gross margin and the historical ~48% / 72% / 89% / 98% / 100% five-year ramp — as a positive value within [+$1.4M, +$4.1M]. (score: "yes" or "no")
- 'c051': The response states a corrected/main-case Chattanooga NPV — shown as discounted at a WACC within [7.1%, 7.7%] and reflecting a corrected 43%–45% gross margin and the historical ~48% / 72% / 89% / 98% / 100% five-year ramp — as a negative value within [−$2.1M, −$0.5M]. (score: "yes" or "no")
- 'c052': The response states a corrected/main-case Columbus NPV — shown as discounted at a WACC within [7.1%, 7.7%] and reflecting a corrected 43%–45% gross margin and the historical ~48% / 72% / 89% / 98% / 100% five-year ramp — as a negative value within [−$2.9M, −$0.9M]. (score: "yes" or "no")
- 'c053': The response explicitly notes that while the Nashville site has a positive NPV, it remains a no-go because it cannot be financed within the debt covenant. (score: "yes" or "no")
- 'c054': The response explicitly identifies that the apparent shareholder-distribution cushion based on uncorrected net income (80% × ~$4.48M FY2025E minus the $2.3M committed minimum ≈ $1.3M, or 80% × ~$5.66M FY2026E minus $2.3M ≈ $2.2M) is a propagation artifact; after FY2025 net income is corrected to about $1.7M–$3.2M, the cushion is at most roughly $0.9M above the committed minimum, possibly none (or roughly $0–$0.3M of discretionary capacity if the 80% payout formula is applied). (score: "yes" or "no")
- 'c055': The response concludes that total realistically available funds remain below the ~$5.1M Nashville buildout cost after applying the $4.0M liquidity reserve, the $2.3M committed minimum distribution, and the covenant debt room. If the response states a total, credit any figure up to ~$4.5M whose components are consistent with the response's own covenant debt room (≤ ~$2.7M), liquidity above the reserve (~$0.6M–$0.9M), and optionally a retained-earnings cushion (up to ~$0.9M above the committed minimum). Any stated total must be described as short of the ~$5.1M need. (score: "yes" or "no")
- 'c056': The response states that on the uncorrected/reported numbers the buildout fits the covenant - pro-forma Total Debt/EBITDA ~2.66x (within [2.60x, 2.70x]), or covenant debt room ~$7.9M. (score: "yes" or "no")
- 'c057': The response shows the debt-covenant test on either trailing-twelve-month actual EBITDA (FY2024A, ~$5.9M) or a corrected FY2025E EBITDA (within the accepted $4.4M–$6.4M range), with proposed borrowings added to the debt numerator only, and explicitly rejects using the uncorrected FY2025E EBITDA of $8.12M or the FY2026E forward EBITDA of ~$9.74M as the covenant base. (score: "yes" or "no")
- 'c058': The response's final recommendation (PROCEED vs. DO NOT PROCEED) is internally consistent with its own computed pro-forma Total Debt/EBITDA ratio, such that a computed ratio above 3.0x is paired with a DO NOT PROCEED recommendation. (score: "yes" or "no")
- 'c059': The response produces an explicit discounted cash flow / NPV calculation for each candidate site (Nashville, Chattanooga, Columbus) rather than relying solely on heuristics such as EBITDA yield, payback, or cash-on-cash multiples. (score: "yes" or "no")
- 'c060': The response shows the arithmetic linking its covenant conclusion to its inputs — displaying the numerator (total funded debt including proposed borrowings, ~$21.6M), the denominator (its stated covenant-base EBITDA), and the resulting ratio — rather than stating the ratio as an unsupported figure. (score: "yes" or "no")
- 'c061': The response does not affirmatively praise or endorse the existing-store 11-16% FY2026 YoY growth figures (e.g., as "strong same-store performance," "operating leverage," or a positive signal); treating these figures as a strength of the proposal is a fail. (score: "yes" or "no")
- 'c062': The response, if it identifies the Returns & allowances sign errors or other forecast errors, does not dismiss them as immaterial, "not decision-changing," or rounding-level; it must propagate the corrections into the EBITDA used downstream for the covenant test. (score: "yes" or "no")
- 'c063': If the response includes a memo date, "current" date, or analysis as-of date, that date is consistent with the August 2025 timeframe of the source materials and is not earlier than 2025 (e.g., not 2023 or 2024). An undated response does not fail this criterion. (score: "yes" or "no")
- 'c064': The response does not state a financial covenant limit other than a maximum Total Funded Debt/EBITDA of 3.00x, tested quarterly on a trailing-twelve-month basis. (score: "yes" or "no")
- 'c065': The response does not state a committed minimum shareholder distribution other than $2.3M per year, reducible only with the written consent of holders of not less than two-thirds of outstanding shares. (score: "yes" or "no")
- 'c066': The response does not state a minimum liquidity reserve other than $4.0M of cash and short-term investments. (score: "yes" or "no")
- 'c067': The response does not state a current cost of debt other than 5.25% for its WACC or cost-of-debt analysis. (score: "yes" or "no")
- 'c068': The response does not state existing total funded debt other than $16.5M. (score: "yes" or "no")
- 'c069': The response does not invent any additional covenant, policy provision, or financial threshold beyond the 3.00x Total Funded Debt/EBITDA covenant, the $2.3M per year committed minimum shareholder distribution, the $4.0M minimum liquidity reserve, the 5.25% current cost of debt, and the $16.5M existing total funded debt. (score: "yes" or "no")
- 'c070': The response shows the line-item adjustments that bridge from the reported FY2025E EBITDA of ~$8.12M to its corrected FY2025E EBITDA (within [$4.4M, $6.4M]) — identifying the specific store-level revenue/returns and growth corrections and their flow-through to gross profit and operating expenses — rather than asserting the corrected figure without a reconciliation. (score: "yes" or "no")
- 'c071': The response delivers its summary as a text-based file (for example .txt, .md, or a similar text-readable document) containing the recommendation and supporting analysis; a response that answers only in the chat without producing a file fails this criterion. (score: "yes" or "no")


Give every criterion a yes or no. Your <score> is the share of the 71 criteria marked yes. DAYJOB counts the task as complete only when every criterion is yes, so also state whether all passed.