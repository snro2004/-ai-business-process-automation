# Setup and import

## Prerequisites

Use an n8n environment supporting Data Tables, Form Trigger, Form Ending, AI Agent, and OpenAI Chat Model. The original environment reported n8n 2.43.0. Other versions and clean imports have not been tested. AI calls require an available model credential or Gateway credits; this package includes neither.

## Create tables

Create **ABC Policies** with string columns `policy_id`, `policy_name`, `policy_text`.
Create **ABC PTO Requests** with string columns `employee_name`, `request_type`, `request_details`, `policy_id`, `assigned_to`, `status`.
Let n8n manage row IDs and creation/update timestamps.

## Import and configure

1. Import `01-policy-ingestion.json`, `02-policy-questions.json`, and `03-request-routing.json` through the workflow import menu.
2. In **Upsert Policy Row** and **Get PTO Policy**, replace `SELECT_ABC_POLICIES` by selecting your ABC Policies table. Both nodes must use the same table.
3. In **Save PTO Request**, replace `SELECT_ABC_PTO_REQUESTS` by selecting your ABC PTO Requests table. Confirm the six field mappings are present. Operation is Insert.
4. Configure **OpenAI Chat Model** with a credential available to your environment. Original live tests used GPT-5-mini, low reasoning effort, via n8n Gateway credits. Credential references were removed from the public export. Model availability and billing depend on your account.
5. Save the workflows. Verify no nodes have pinned data.
6. Execute the complete ingestion workflow from its canvas and upload the supplied PDF. Check that `abc-pto` has nonempty `policy_text`.
7. Open chat on the Questions workflow and ask a question from DEMO.md.
8. Execute the complete Routing workflow from the canvas and submit the new form it opens. Check the confirmation and saved table row.

Use the full workflow **Execute** button for a complete form test. **Execute step** on a trigger tests only that trigger. Use a freshly opened test form while the workflow is listening. Running Form Ending separately is not a reliable test of the complete browser experience.

## Optional publishing

The supplied workflows are inactive. Publishing is not required for editor tests. For a persistent production form, configure appropriate access controls and publish deliberately, then use the Production URL shown in the trigger. The exported forms currently have no authentication. Do not collect real HR data in this demonstration.

## Troubleshooting

- **No prompt specified:** the agent must use Define below with `{{ $('Employee Question').first().json.chatInput }}`. Data Table output contains policy fields, not the chat question.
- **Empty policy:** inspect extraction output, then the stored table row. This version does not reject empty extraction automatically and does not include OCR.
- **Form submission error:** inspect the current execution and failing node. Avoid resubmitting until you check whether a row was already inserted.
- **Mock results:** unpin all nodes and retest. A mocked successful run does not verify a live model call or table insert.
- **Wrong table or credential after import:** select local resources again. Sanitized placeholder IDs are intentional.

Sanitization removed workflow/instance identifiers, webhook IDs, and credentials, and substituted table placeholders. Node logic, expressions, connections, and versions were preserved. Clean-environment runtime validation is still required after resource configuration.
