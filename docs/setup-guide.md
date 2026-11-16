# Setup Guide

This guide explains how to install, configure, and run the AI Research & Reporting Agent using n8n.

## 1. Prerequisites

Before starting, ensure you have:

- An n8n Cloud account or self-hosted n8n instance.
- A Tavily API key.
- A Google Gemini API key.
- A Gmail account.
- Basic familiarity with n8n workflows.

## 2. Clone the Repository

Clone the project to your local machine:

```bash
git clone https://github.com/zahid0511/ai-research-reporting-agent.git
```

Navigate to the project directory:

```bash
cd ai-research-reporting-agent
```

## 3. Import the Workflow

1. Log in to your n8n instance.
2. Open the n8n workspace.
3. Select **Add Workflow**.
4. Open the workflow editor.
5. Click the three-dot menu in the top-right corner.
6. Select **Import from File**.
7. Choose `workflow/ai-research-agent.json`.

The workflow nodes and connections should now appear in the editor.

## 4. Configure API Credentials

The exported workflow does not contain saved API secrets. Configure your own credentials inside n8n.

### 4.1 Tavily API

Tavily is used to retrieve relevant web research sources.

1. Create an account at https://tavily.com/.
2. Generate an API key.
3. Open the Tavily Search HTTP Request node.
4. Configure Header Auth:

| Field | Value |
|---|---|
| Credential Type | Header Auth |
| Name | Authorization |
| Value | Bearer YOUR_TAVILY_API_KEY |

5. Save the credential.

### 4.2 Google Gemini API

Google Gemini generates the research report using the retrieved source content.

1. Visit https://aistudio.google.com/apikey.
2. Generate a Gemini API key.
3. Open the Gemini HTTP Request node.
4. Configure Header Auth:

| Field | Value |
|---|---|
| Credential Type | Header Auth |
| Name | x-goog-api-key |
| Value | YOUR_GEMINI_API_KEY |

5. Save the credential.

Do not add a Bearer prefix to the Gemini API key.

### 4.3 Gmail OAuth2

Gmail is used to deliver the generated research report.

1. Open the Gmail node.
2. Select or create a Gmail OAuth2 credential.
3. Connect your Google account.
4. Complete the Google authorization process.
5. Save the credential.

The connected Gmail account will be used as the sender of the automated reports.

## 5. Configure the Research Form

1. Open the Form Trigger node.
2. Review the form fields.
3. Ensure the research topic and research focus fields are configured.
4. Save the workflow.

Users will provide their research requirements through this form.

## 6. Test the Workflow

Before publishing, test the complete automation.

Example research input:

**Research Topic:**

Impact of Generative AI on Software Development

**Research Focus:**

Industry trends, opportunities, challenges, and future developments.

Execute the workflow and verify the following:

- Tavily retrieves relevant web sources.
- Research sources are structured correctly.
- The Gemini API generates a research report.
- The report is extracted and formatted successfully.
- Gmail delivers the completed report.

## 7. Publish the Workflow

After successful testing:

1. Save the workflow.
2. Click **Publish** or activate the workflow, depending on your n8n version.
3. Open the Form Trigger node.
4. Locate the Production URL.
5. Copy the public form URL.

Share this URL with users to allow them to submit research requests.

## 8. Security Considerations

- Never hardcode API keys inside workflow nodes.
- Store API keys using n8n credential management.
- Do not upload passwords, OAuth tokens, or private configuration files to GitHub.
- Use HTTPS for public access.
- Apply suitable usage limits to public form submissions.
- Monitor workflow executions and API consumption.

## 9. Troubleshooting

| Problem | Possible Solution |
|---|---|
| Tavily authentication error | Verify the API key and Header Auth configuration. |
| Gemini authentication error | Check the API key and request header. |
| Gemini returns no response | Check the model endpoint and request body. |
| Gmail authorization error | Reconnect the Google OAuth2 credential. |
| Form URL does not work | Verify that the workflow is published and use the Production URL. |
| Workflow execution fails | Inspect the failed node and review its execution data. |

## 10. Additional Resources

- n8n Documentation: https://docs.n8n.io/
- Tavily Documentation: https://docs.tavily.com/
- Google Gemini API: https://ai.google.dev/gemini-api/docs
- Gmail API: https://developers.google.com/gmail/api

---

**Project:** AI Research & Reporting Agent

**Author:** MD Zahid

**GitHub:** https://github.com/zahid0511