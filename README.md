# ABC Diagnostics — AI PTO Policy Assistant

A novice learning and portfolio project for Sydney Rosser: upload a fictional PTO policy PDF, answer employee questions using its stored text, and record PTO requests for human review.

## Implemented version 1

| Workflow | Behavior |
| --- | --- |
| Policy ingestion | Extracts PDF text and upserts the `abc-pto` row in ABC Policies. Re-uploading updates the same policy. |
| Policy questions | Retrieves the complete PTO policy from a Data Table and passes it to an OpenAI model with the employee question. Responses are instructed to cite the policy, acknowledge missing information, and refuse approvals. |
| Request routing | Accepts a separate form submission, records a request, assigns Planned PTO to Manager and Policy exception to HR, and displays a pending-review confirmation. |

This version uses a fixed policy lookup and full-text context. It does not use embeddings, vector search, Pinecone, Google Drive, or OpenRouter. The chat and request form are separate entry points; the AI does not submit requests. Assignment is a table field, with no email notification or approval interface.

## Start here

1. Follow [setup](workflow/README.md) to import three workflows and create two Data Tables.
2. Upload [the fictional policy](policies/ABC_Diagnostics_Paid_Time_Off_Policy.pdf).
3. Follow [the demo](DEMO.md).
4. Review [observed results](04-testing-and-results/results.md) and [controls](03-solution-design/controls-and-exceptions.md).

Exports are sanitized templates of the workflows tested on October 6, 2026. Select your own tables and model credential after import. Workflows remain inactive. The exports do not include table contents, real employee information, or API credentials.

## Evidence and scope

Manual tests demonstrated policy ingestion, repeat-upload update behavior, three live AI response cases, and complete form submissions for both request types. No measured production time savings, error reduction, or ROI is claimed. This is a fictional demonstration, not a deployed HR service.

The project was built with AI assistance and manually tested. Sydney should reproduce the setup and explain the design and limitations before presenting it as her portfolio work.
