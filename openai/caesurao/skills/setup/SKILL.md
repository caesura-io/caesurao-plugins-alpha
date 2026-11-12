---
name: setup
description: Set up CaesuraO when the user installs the plugin or asks how to connect, use, pause, or resume it, or whether it is connected. Explain account linking and text analysis without running a sample analysis or changing other chats.
---

# Set up CaesuraO

Keep setup brief. Explain that CaesuraO gives the assistant response guidance for interpersonal situations and difficult moments during ordinary tasks. The assistant continues the original task and uses recommendations without presenting an analysis report. This is not therapy or diagnosis.

Explain before first use that selected task-related text is sent to CaesuraO, with identifying details and secrets masked by the assistant. Do not promise perfect anonymization. Analyses use the connected account's credits, and submitted text and results are stored under the [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos). Do not invent a retention period or promise that data is never stored.

Use the host's native OAuth connection flow to link the user's CaesuraO account. If the host requires the user to open plugin connection settings, give that instruction rather than claiming the account is connected. Do not ask for passwords, API keys, or login codes. To check the connection, call `get_account`; it sends no text and uses no credits. If it returns an account, say CaesuraO is connected and name the account. If the tool is unavailable or reports an authorization error, the account is not connected yet; guide the user through the host's connection flow. Never call `analyze` to test the connection: that submits text and can consume credits. Resume a real eligible task once the connection is available.

Explain that guidance can be selected automatically for relevant tasks; it is not guaranteed to run before every answer. The user can say "Stop CaesuraO analysis in this chat" and later "Resume CaesuraO analysis in this chat." A pause takes effect without a backend call. Keep it in conversation context, including handoff summaries, until explicitly resumed. For account-wide disconnection, direct the user to the host's plugin connection controls; do not claim a chat instruction changes account settings.

Do not require an example, emotional disclosure, or extra questionnaire to finish setup. If the user already has a task, continue it under the response-guidance skill and any current opt-out. Explicit user instructions take precedence over this skill.
