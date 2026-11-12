# CaesuraO Alpha for Claude

> **Experimental preview: these skills are not stable.** Use [stable CaesuraO](https://github.com/caesura-io/caesurao-plugins) for everyday work. Analyses use your account’s credits. Enable only one channel at a time.

CaesuraO helps Claude respond with care and clarity when a task carries human stakes: replying to a difficult message, setting a boundary, apologizing, delivering disappointing news, or working through a task while frustrated or under pressure. Before answering in those situations, Claude asks CaesuraO for brief response guidance and applies it quietly, while completing the task you asked for. It is not therapy or diagnosis.

## What it includes

- **CaesuraO connector**: a remote MCP server at `https://app.caesurao.com/api/mcp/assistant` with `analyze` for response guidance and `get_account` for checking the connected account without submitting text or using analysis credits.
- **response-guidance skill**: tells Claude when guidance is worth requesting, how to prepare a short masked excerpt, and how to apply the result without reciting it.
- **setup skill**: explains how to connect, pause, resume, and disconnect.

There are no hooks, scripts, or local executables.

## Requirements

A CaesuraO account with service access, accepted Terms of Service, and available credits. Each analysis consumes credits.

## Install and update

For the private marketplace, your GitHub account needs repository access and a configured SSH key. Ask the CaesuraO team for access, then follow [GitHub’s SSH setup instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).

Verify access in Terminal first and resolve any SSH prompts there:

```sh
git ls-remote git@github.com:caesura-io/caesurao-plugins-alpha.git HEAD
```

Then, in a Claude Code session:

```text
/plugin marketplace add git@github.com:caesura-io/caesurao-plugins-alpha.git
/plugin install caesurao-alpha@caesurao-alpha
```

For Claude apps and Cowork, open Customize → Plugins → Add marketplace, enter `caesura-io/caesurao-plugins-alpha`, and install **CaesuraO Alpha (Preview)**. Private repositories require authorized GitHub access in the host; configuring local SSH alone does not authorize Claude web or Cowork.

To update from your shell, keep repository access and SSH authentication available:

```sh
claude plugin marketplace update caesurao-alpha
claude plugin update caesurao-alpha@caesurao-alpha
```

Start a new session. In Claude apps, sync the marketplace in plugin settings, verify the installed version, and start a new conversation. Enable automatic sync where available. See the [repository README](../../README.md) for repository access troubleshooting, other hosts, channel switching, and full update instructions.

## Connect

- **Claude Code:** install the plugin, run `/mcp`, select `plugin:caesurao-alpha:caesurao`, and choose Authenticate.
- **Claude apps and Cowork:** Customize → Plugins → CaesuraO Alpha (Preview) → Connectors → Connect.

Both sign you in to CaesuraO through OAuth; Claude never sees your password.

## What data is shared

Claude calls CaesuraO only for tasks with interpersonal or emotional significance, not for routine technical or factual work. It sends a short text: the task, relevant quotations with names and identifying details replaced by placeholders such as `[MANAGER]`, and essential context. It does not send full conversation history, files, images, or secrets. Masking is performed by Claude and is not guaranteed anonymization. Submitted text and results are stored by CaesuraO under its [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos).

## Pause or disconnect

Say "Stop CaesuraO analysis in this conversation" to pause it for the current conversation, and "Resume CaesuraO analysis" to turn it back on. To disconnect your account, use the connector settings (or `/mcp` in Claude Code).

## Support

support@caesura.io · https://caesurao.com
