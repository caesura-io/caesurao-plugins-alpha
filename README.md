# CaesuraO Alpha (Preview) plugins

> **Experimental preview — the skills in this repository are not stable.** They may change, regress, or be replaced without notice. Use this channel only if you explicitly want to test unreleased behavior. For everyday use, install [stable CaesuraO](https://github.com/caesura-io/caesurao-plugins).

## Choose one channel

Enable only one CaesuraO channel in a host at a time. Stable and alpha provide the same skills and connect to the same assistant MCP; enabling both can duplicate guidance requests and consume extra credits. To switch, disable or uninstall the previous plugin, install the other channel, and start a new session.

Alpha uses the **production** service, not a sandbox. Analyses consume real credits and follow the same storage/privacy terms as stable. The connected account’s environment selects its analysis preset; installing alpha does not select a testing preset automatically.

## Install in Claude Code

In a Claude Code session, run:

```text
/plugin install caesurao-alpha --marketplace caesura-io/caesurao-plugins-alpha
```

Or add the marketplace explicitly, then install:

```text
/plugin marketplace add caesura-io/caesurao-plugins-alpha
/plugin install caesurao-alpha@caesurao-alpha
```

Choose the installation scope when prompted. Start a new session, run `/mcp`, select `plugin:caesurao-alpha:caesurao`, and choose Authenticate. Sign in to your CaesuraO account and approve access in the browser.

## Install in Claude apps and Cowork

1. Open Customize → Plugins → Add marketplace and enter `caesura-io/caesurao-plugins-alpha`.
2. Install **CaesuraO Alpha (Preview)**.
3. Open its Connectors settings, choose Connect, and complete CaesuraO OAuth sign-in.

For a private repository, your host must have authorized GitHub access to it; local SSH access alone does not grant the Claude web app access. If the host or workspace cannot import the private marketplace, use Claude Code with authorized Git credentials or ask the workspace administrator to enable access. Private installation support must be verified in each target host.

## Install in Codex

```sh
codex plugin marketplace add caesura-io/caesurao-plugins-alpha
codex plugin add caesurao-alpha@caesurao-alpha
```

Start a new session, select **CaesuraO Alpha (Preview)**, and complete the host’s CaesuraO connection flow if prompted. Ask whether CaesuraO is connected: the setup skill uses `get_account`, which sends no analysis text and consumes no analysis credits.

For a private GitHub repository, first authenticate with an account that can read it:

```sh
gh auth login
gh auth setup-git
```

Alternatively, add the marketplace using SSH with an already configured GitHub SSH key:

```sh
codex plugin marketplace add git@github.com:caesura-io/caesurao-plugins-alpha.git
```

The marketplace is named `caesurao-alpha` regardless of whether it was added through HTTPS or SSH.

## Install in ChatGPT

Where Git-backed plugin marketplaces are available, import `caesura-io/caesurao-plugins-alpha` through the plugin marketplace controls and install **CaesuraO Alpha (Preview)**. In a managed workspace, an administrator may need to import the repository and authorize private GitHub access. Complete the CaesuraO connection flow, then start a new chat. Availability and menu names vary by host and workspace; these Git marketplace steps do not imply a public directory listing.

## Update an existing installation

**Claude Code:** refresh the catalog and update the installed plugin from your shell:

```sh
claude plugin marketplace update caesurao-alpha
claude plugin update caesurao-alpha@caesurao-alpha
```

Start a new session afterward. Inside Claude Code, `/plugin` → Installed → **CaesuraO Alpha (Preview)** → Update now is another option. To enable automatic updates, open `/plugin` → Marketplaces → `caesurao-alpha` → Enable auto-update. Third-party marketplaces do not necessarily have automatic updates enabled by default.

**Claude apps and Cowork:** refresh or sync the marketplace in plugin settings; enable “Sync automatically” where available. Check the installed version, then start a new conversation. Private updates still require repository access.

**Codex:** refresh the marketplace and select the current plugin package:

```sh
codex plugin marketplace upgrade caesurao-alpha
codex plugin add caesurao-alpha@caesurao-alpha
```

Start a new session and check the installed version in `/plugins`. **ChatGPT:** refresh/sync the imported marketplace and installed plugin through the host’s plugin controls, or ask the workspace administrator to sync it, then start a new chat. Running sessions can retain the skills they already loaded.

If an old version remains, verify repository access and the installed version before reinstalling this channel. Reconnect CaesuraO through the host’s OAuth controls if prompted; never paste passwords, API keys, or login codes into a chat.

## Pause, disconnect, and data

Say “Stop CaesuraO analysis in this chat” to pause analysis in the current conversation, and “Resume CaesuraO analysis” to resume. To disconnect the account, use the host’s connector controls. Selected text and results are handled under the [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos). Masking is performed by the assistant and is not guaranteed anonymization.

## Development

The package folders remain `plugins/caesurao/` (Claude) and `openai/caesurao/` (ChatGPT/Codex) in both repositories; the stable plugin and marketplace are named `caesurao`, and alpha uses `caesurao-alpha`. The response-guidance description and body should match across hosts; host-specific frontmatter and setup instructions can differ.

This first alpha starts from stable 0.3.1 and is versioned 0.4.0-alpha.1. Bump both plugin manifests together for each new preview. Alpha changes do not automatically release to stable; promote a reviewed, tested snapshot explicitly.

Scenario evals live in the CaesuraO monorepo (`integrations/`). Point eval runners at this checkout with `CAESURAO_PLUGINS_DIR=../caesurao-plugins-alpha`. The existing monorepo package checker expects the stable identity; alpha currently needs its own identity checks plus `claude plugin validate --strict` on the repository and Claude package. Keep private eval results and backend preset prompts out of distribution repositories.

Support: support@caesura.io
