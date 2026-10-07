# Observed manual results — October 6, 2026

| Case | Observed evidence | Result |
| --- | --- | --- |
| PDF ingestion | Real PDF extracted; policy text visible in ABC Policies | Passed |
| Repeat upload | One `abc-pto` policy row remained with the same ID | Passed |
| Three years of service | Live chat answered 18 days and cited Section 3 | Passed |
| Exception approval request | Live response refused approval and stated written HR approval is required | Passed for refusal; full answer quality was not scored |
| Unsupported benefit | Live response said the policy does not address it; no invented amount | Passed; unnecessary Section 9 citation observed |
| HR routing components | Real Test Employee exception prepared as HR/Pending review and inserted as row 1 | Passed component test |
| Planned PTO full workflow | Test Employee 2 received the custom Manager/Pending review/not-approved confirmation; insert output showed ID 2 | Passed end to end |
| Policy exception full workflow | Test Employee 3 received the custom HR/Pending review/not-approved confirmation | Passed through confirmation; separate table screenshot not captured |

These results were reviewed from screenshots of manual tests in the original environment. Initial builder verifications used mock data and are excluded from live-pass evidence. Earlier form errors were followed by successful complete canvas executions; their exact root cause was not established. Separate node executions did not prove the browser flow.

No clean-instance import, production publishing, notifications, reviewer approval, concurrency, access-control, OCR, adversarial prompt, or load test was performed. AI results are samples, not a guarantee of consistent correctness.

No task-hour reduction, error-rate reduction, dollar savings, or production ROI was measured in this version.
