# CaesuraO Alpha (Preview) plugins

> **Experimental preview — the skills in this repository are not stable.** They may change, regress, or be replaced without notice. Use this channel only if you explicitly want to test unreleased behavior. For everyday use, install [stable CaesuraO](https://github.com/caesura-io/caesurao-plugins).

## Choose one channel

Enable only one CaesuraO channel in a host at a time. Stable and alpha provide the same skills and connect to the same assistant MCP; enabling both can duplicate guidance requests and consume extra credits. To switch, disable or uninstall the previous plugin, install the other channel, and start a new session.

Preview analyses use your account’s credits and follow the same privacy and storage terms as stable.

## Before installing the private marketplace

Each tester needs a GitHub account with read access to `caesura-io/caesurao-plugins-alpha`. Ask the CaesuraO team for repository access first.

For ChatGPT desktop, Codex, and Claude Code, use SSH:

1. Configure an SSH key for the GitHub account that has repository access. Add its public key under GitHub Settings → SSH and GPG keys. See [GitHub’s SSH setup instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).
2. Verify access from Terminal before adding the marketplace:

   ```sh
   git ls-remote git@github.com:caesura-io/caesurao-plugins-alpha.git HEAD
   ```

   Successful access prints a commit hash and `HEAD`. Resolve any SSH authentication or host prompts in Terminal first. `Permission denied (publickey)` means SSH authentication needs attention; a repository-not-found error can mean the account lacks access.
3. Follow the host-specific steps below. Keep SSH authentication available for future marketplace updates.

The `owner/repo` shorthand clones over HTTPS in ChatGPT/Codex. Without configured HTTPS credentials, it can fail with `could not read Username ... terminal prompts disabled`. Use the SSH URL below. Local SSH credentials do not authorize a cloud-hosted Claude app or workspace; those hosts need their own GitHub access.

## Install in Claude Code

After completing the SSH prerequisites, run this in a Claude Code session:

```text
/plugin marketplace add git@github.com:caesura-io/caesurao-plugins-alpha.git
/plugin install caesurao-alpha@caesurao-alpha
```

Choose the installation scope when prompted. Start a new session, run `/mcp`, select `plugin:caesurao-alpha:caesurao`, and choose Authenticate. Sign in to your CaesuraO account and approve access in the browser.

## Install in Claude apps and Cowork

1. Open Customize → Plugins → Add marketplace and enter `caesura-io/caesurao-plugins-alpha`.
2. Install **CaesuraO Alpha (Preview)**.
3. Open its Connectors settings, choose Connect, and complete CaesuraO OAuth sign-in.

For a private repository, your host must have authorized GitHub access to it; local SSH access alone does not grant the Claude web app access. If the host or workspace cannot import the private marketplace, use Claude Code with authorized Git credentials or ask the workspace administrator to enable access.

## Install in Codex

```sh
codex plugin marketplace add git@github.com:caesura-io/caesurao-plugins-alpha.git
codex plugin add caesurao-alpha@caesurao-alpha
```

Start a new session, select **CaesuraO Alpha (Preview)**, and complete the host’s CaesuraO connection flow if prompted. Ask whether CaesuraO is connected: the setup skill uses `get_account`, which sends no analysis text and consumes no analysis credits.

## Install in ChatGPT desktop

After completing the SSH prerequisites, use Codex CLI to register the marketplace from Terminal:

```sh
codex plugin marketplace add git@github.com:caesura-io/caesurao-plugins-alpha.git
```

Fully quit and reopen ChatGPT. Open the Plugins Directory, choose the `caesurao-alpha` marketplace, and install **CaesuraO Alpha (Preview)**. Complete the CaesuraO OAuth connection flow, then start a new chat. Do not enter `caesura-io/caesurao-plugins-alpha` as the marketplace source when relying on SSH: that shorthand selects HTTPS.

This command requires [Codex CLI](https://developers.openai.com/codex/cli/) on your machine. For a cloud-managed ChatGPT workspace marketplace, an administrator must configure the workspace’s GitHub access separately; local SSH keys do not provide cloud access.

## Update an existing installation

**Claude Code:** with repository access and SSH authentication still available, refresh the catalog and update the installed plugin from your shell:

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

Start a new session and check the installed version in `/plugins`.

**ChatGPT desktop:** refresh the registered SSH marketplace from Terminal:

```sh
codex plugin marketplace upgrade caesurao-alpha
```

Fully quit and reopen ChatGPT, check the installed plugin version in the Plugins Directory and apply an available update, then start a new chat. For a cloud-managed marketplace, ask the workspace administrator to sync it. Running sessions can retain the skills they already loaded.

If an update reports `terminal prompts disabled`, check the configured marketplace source: it should be the SSH URL above, not the HTTPS URL. Verify SSH repository access with the `git ls-remote` command before retrying. If an old version remains, check the installed version and refresh the marketplace before reinstalling this channel. Reconnect CaesuraO through the host’s OAuth controls if prompted; never paste passwords, API keys, or login codes into a chat.

## Pause, disconnect, and data

Say “Stop CaesuraO analysis in this chat” to pause analysis in the current conversation, and “Resume CaesuraO analysis” to resume. To disconnect the account, use the host’s connector controls. Selected text and results are handled under the [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos). Masking is performed by the assistant and is not guaranteed anonymization.

Support: support@caesura.io
