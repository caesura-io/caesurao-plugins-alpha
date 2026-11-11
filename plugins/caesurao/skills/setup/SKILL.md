---
name: setup
description: Explains how to connect, use, pause, resume, or disconnect the CaesuraO plugin and what data it shares. Use when the user installs CaesuraO, asks how it works or how to connect their CaesuraO account, asks whether it is connected, or reports that CaesuraO is not connected. Does not run a sample analysis.
license: UNLICENSED
---

# Set up CaesuraO Alpha

Keep setup brief. Explain that this is the experimental CaesuraO Alpha plugin: its skills are not stable, it uses the production CaesuraO service and real credits, and the user should enable either stable or alpha rather than both. Explain that CaesuraO gives Claude response guidance for interpersonal situations and difficult moments during ordinary tasks. Claude continues the original task and uses the guidance without presenting an analysis report. This is not therapy or diagnosis.

Explain before first use that selected task-related text is sent to CaesuraO, with identifying details and secrets masked by Claude. Do not promise perfect anonymization. Each analysis uses the connected account's credits, and submitted text and results are stored under the [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos). Do not invent a retention period or promise that data is never stored.

## Connect the account

The account is linked through the host's OAuth flow; never ask for passwords, API keys, or login codes in the conversation. Give the instruction that matches where the user is, rather than claiming the account is connected:

- **Claude Code:** run `/mcp`, select the `caesurao` server (shown as `plugin:caesurao-alpha:caesurao`), and choose Authenticate. A browser window opens to sign in to CaesuraO and approve access.
- **Claude apps (web, desktop, mobile) and Cowork:** open Customize → Plugins → CaesuraO Alpha (Preview) → Connectors and choose Connect, then sign in to CaesuraO and approve access.

The CaesuraO account needs access to the service, accepted Terms of Service, and available credits. If sign-in succeeds but the connector still reports an authorization error, the account may lack access or accepted terms; direct the user to https://app.caesurao.com to finish account setup.

To check the connection, call `get_account` on the CaesuraO connector. It sends no text and uses no credits. If it returns an account, say CaesuraO is connected and name the account. If the tool is unavailable or reports an authorization error, the account is not connected yet; give the steps above. Never call `analyze` to test the connection: that submits text and can consume credits. Resume a real eligible task once the connection is available.

## Use, pause, and disconnect

Guidance is selected automatically for relevant tasks; it does not run before every answer. The user can say "Stop CaesuraO analysis in this conversation" and later "Resume CaesuraO analysis." A pause takes effect without a backend call and lasts for the current conversation, including after summaries, until explicitly resumed. To disconnect the account, use the same connector settings (or `/mcp` in Claude Code); a conversation instruction does not change account settings.

Do not require an example, emotional disclosure, or questionnaire to finish setup. If the user already has a task, continue it under the response-guidance skill and any current opt-out. Explicit user instructions take precedence over this skill.
