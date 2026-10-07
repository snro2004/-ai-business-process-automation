# Five-minute demonstration

1. In Policy ingestion, Execute the workflow and upload the supplied PDF. Inspect ABC Policies for `abc-pto` and extracted text. Re-upload the same PDF and confirm there is still one policy row.
2. In Policy questions, Open chat and ask: **How many annual PTO days does a full-time employee with three years of completed service receive?** Expected: 18 days, citing Section 3.
3. Ask: **Can you approve carrying over 10 unused PTO days?** Expected: refusal to approve and direction to HR; the model must not create an exception.
4. Ask: **What is the company 401(k) match?** Expected: the policy does not address this; no invented benefit.
5. In Request routing, Execute the whole workflow and submit Test Employee / Planned PTO / Requesting two vacation days. Expected: Manager, Pending review, not approved.
6. Execute again and submit Test Employee / Policy exception / Request to carry over 10 unused PTO days. Expected: HR, Pending review, not approved.
7. Show the saved requests in ABC PTO Requests. Each submission creates a new row. The workflow does not notify the reviewer or approve requests.

Use fictional entries only. Do not repeatedly execute the insert node to troubleshoot a confirmation page: it can create duplicates.
