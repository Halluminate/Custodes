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
Caldervane Emerging Markets Fund is a new client's first fund with us and we are delivering our first reports for it today for COB June 30th. The client wants the initial reports as soon as they are available, so they can review these BAU deliverables in detail. Go through the attached pack and let me know if there are any issues stopping me sending the reports to the client as they are. Write it up as a short .md memo.
</original_prompt>

<context_files>
- Atlas_Markets_EM_Credit_Quote_Recap_30Jun2026.pdf
- BVAL_Evaluated_Prices_30Jun2026.csv
- Caldervane_Consolidated_Geneva_Price_Source_Report_30Jun2026.xlsx
- Caldervane_Geneva_Position_Valuation_Report_30Jun2026.xlsx
- Caldervane_Market_and_Currency_Exposure_30Jun2026.xlsx
- ICE_Evaluated_Prices_30Jun2026.csv
- Kesterholt_Approved_Broker_Source_Register_Q2_2026.pdf
- Kesterholt_Approved_Pricing_Source_Hierarchy_Effective_01Jan2026.pdf
- Kesterholt_Geneva_Pricing_Readiness_Email_30Jun2026.pdf
- Kesterholt_Launch_Pricing_Support_Email_30Jun2026_Outlook.pdf
- Official_Exchange_Settlement_Prices_30Jun2026.csv
- WM_Refinitiv_FX_Forward_Valuation_Extract_30Jun2026.csv
- WM_Refinitiv_Spot_FX_Closing_Rates_30Jun2026.csv
</context_files>

Criteria:

- 'c001': The response identifies that the Bloomberg screen quotes the Nerovexa price of 261.200 (CV-1059) in South African cents rather than South African rand. (score: "yes" or "no")
- 'c002': The response states that the Nerovexa position (CV-1059) is overstated by approximately $25.7 million (accept $25.5m–$25.9m). Accept any equivalent expression of the same direction and magnitude (e.g., "write the position down by $25.7m" or a signed difference of +$25.7m versus the corrected value). (score: "yes" or "no")
- 'c003': The response states that the corrected USD fair value of the Nerovexa position (CV-1059) is approximately $260,000 (accept $258,000–$262,000). (score: "yes" or "no")
- 'c004': The response recommends that the reports are not sent to the client until the Nerovexa position (CV-1059) is corrected. The hold must be tied to correcting the price: a hold that lifts once the quotation basis is confirmed, or that makes the correction itself conditional on that confirmation, does not satisfy this criterion. Asking for the quotation basis to be confirmed alongside an unconditional instruction to correct the price does not violate this criterion. (score: "yes" or "no")
- 'c005': Once the Nerovexa position (CV-1059) is corrected, the response states that the affected report(s) must be regenerated or re-run. Naming the Market and Currency Exposure report specifically, or stating that all of the reports (which include the exposure report) must be re-run, both satisfy this criterion. (score: "yes" or "no")
- 'c006': The response identifies that the Kingdom of Saudi Arabia 4.500% 2046 bond (CV-1073) was priced from BVAL when ICE supplied a current evaluation. (score: "yes" or "no")
- 'c007': The response states that the Kingdom of Saudi Arabia 4.500% 2046 bond (CV-1073) is overstated by approximately $143,000 (accept roughly $140,000–$146,000). Accept any equivalent expression of the same direction and magnitude, such as "$143,000 too high", "repricing reduces fair value by $143,000", or a signed difference of +$143,000 versus the primary source. (score: "yes" or "no")
- 'c008': The response identifies that the Petróleos Mexicanos 6.500% 2027 bond (CV-1098) was priced from ICE when BVAL supplied a current evaluation. (score: "yes" or "no")
- 'c009': The response states that the Petróleos Mexicanos 6.500% 2027 bond (CV-1098) is understated by approximately $275,000 (accept roughly $272,000–$278,000). Accept any equivalent expression of the same direction and magnitude, such as "$275,000 too low", "repricing increases fair value by $275,000", or a signed difference of −$275,000 versus the primary source. (score: "yes" or "no")
- 'c010': The response does not treat the Nerovexa (CV-1059) price of 261.200 as correct or verified against the Bloomberg screen. Observing that the numeric value 261.200 matches the figure on the Bloomberg screen does not violate this criterion where the response also identifies that the quotation unit is South African cents and that the loaded value is therefore wrong. (score: "yes" or "no")
- 'c011': The response does not recommend that the Emirates NBD 4.250% 2030 bond (CV-1107) be repriced from a different pricing source. Noting, without requiring, that ICE's prior-day evaluation could alternatively have been carried forward does not violate this criterion. (score: "yes" or "no")
- 'c012': The response does not identify any bond other than the Kingdom of Saudi Arabia 4.500% 2046 (CV-1073) and Petróleos Mexicanos 6.500% 2027 (CV-1098) as having been priced from the wrong source under the pricing hierarchy. (score: "yes" or "no")
- 'c013': The response states that the Nerovexa (CV-1059) price is wrong, without qualifying it as possible, likely, probable, apparent, or otherwise conditional. A recommendation to verify the quotation unit does not count as qualification where the response also directs that the price be corrected. (score: "yes" or "no")
- 'c014': The response either states a corrected total portfolio fair value of approximately USD 739.2m–739.7m (the reported ~$765.08m total less the Nerovexa cents overstatement, whether or not the two bond repricings are also booked into the total), or quantifies the position-level impacts of the corrections (Nerovexa −$25.7m, KSA −$143,000, Pemex +$275,000). A response that does both also satisfies this criterion. Describing the corrected figure as a position or control total rather than NAV does not affect satisfaction of this criterion. (score: "yes" or "no")
- 'c015': The response does not state that the Dravena Energy Systems (CV-1044) position quantity or the 1,242.000 CZK valuation price is incorrect, and does not treat the stock split or an unverified share count as a reason to withhold or delay release of the reports, or assert a Dravena fair-value misstatement (e.g., an understatement of roughly USD 67.8 million). Flagging the split as a non-blocking observation or an item to confirm after release does not violate this criterion. Making confirmation of the Dravena share count a condition of release does violate it. (score: "yes" or "no")
- 'c016': The response states that pricing CV-1107 (Emirates NBD 4.250% 2030) from the Atlas Markets broker quote is compliant because the higher-ranked sources were unavailable or stale. A response that cites either the missing BVAL evaluation or the stale ICE evaluation, with or without reference to the approved broker register, satisfies this criterion, and so does a response that does not raise this pricing as an issue. (score: "yes" or "no")
- 'c017': The response states that the Avyra (CV-1013) 26 June price is within the policy's five-business-day carry-forward allowance (two or three business days at 30 June) and requires no stale-price escalation, or does not raise that price as stale or as an issue. (score: "yes" or "no")
- 'c018': The response states that the Dravena Energy Systems (CV-1044) 30 June price of 1,242.000 CZK is the correct post-split close. A request to confirm the share count operationally does not by itself prevent this criterion from being satisfied, and a response that does not call that price wrong also satisfies it. (score: "yes" or "no")
- 'c019': The response states that the ICE price used for Prosus (CV-1031) and the BVAL price used for State of Qatar (CV-1042) are authorized fallbacks, because the higher-ranked source supplied no evaluation for the valuation date. A response that states there are no other hierarchy exceptions and that the remaining lower-ranked prices were used only where the higher-ranked source supplied no evaluation satisfies this criterion, and so does a response that does not raise either price as a hierarchy exception. (score: "yes" or "no")
- 'c020': The response identifies that the 30 June equity prices were keyed manually because the Geneva equity price schedule was not assigned to the new portfolio, and treats the manual keying as a control weakness. Stating either ten manually keyed equity prices or eleven manual records in total is acceptable; no count is required. (score: "yes" or "no")


Give every criterion a yes or no. Your <score> is the share of the 20 criteria marked yes. DAYJOB counts the task as complete only when every criterion is yes, so also state whether all passed.