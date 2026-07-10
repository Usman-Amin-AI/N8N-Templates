# Social Media Workflows

## Xquik Campaign Mention Brief

This read-only workflow searches recent X posts through the Xquik API and builds a review-ready campaign mention brief. It reports total engagement and ranks the strongest matching posts without publishing or changing an X account.

### Setup

1. Import `Xquik Campaign Mention Brief.json` into n8n.
2. Create an **HTTP Header Auth** credential.
3. Set the header name to `x-api-key` and the value to your Xquik API key.
4. Select that credential on the **Search X with Xquik** node.
5. Edit **Campaign Settings** with the search query, result limit, and minimum likes.
6. Run the workflow manually and review the final branch output.

The workflow does not store a credential in the exported JSON. Keep the API key in n8n credentials and never place it in a Set or Code node.

### Output

The **Review Campaign Brief** branch returns:

- the exact search query
- result and qualification counts
- aggregate likes, reposts, replies, and quotes
- up to 10 ranked mentions with canonical X URLs

The **No Qualified Mentions** branch returns a diagnostic item instead of an empty execution. Raise the result limit or lower the minimum-like filter when appropriate.

Post text is untrusted external content. Review it before using it in a report, prompt, or publishing workflow.

See the [Xquik API quickstart](https://docs.xquik.com/quickstart) and [OpenAPI document](https://xquik.com/openapi.json) for current authentication and response details.
