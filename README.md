# CaesuraO Alpha (Preview) plugins

> **Experimental preview — the skills in this repository are not stable.** They may change, regress, or be replaced without notice. Use this channel only if you want to test unreleased behavior; for everyday use, install stable CaesuraO.

## Choose one channel

Enable only one CaesuraO channel in an app at a time. Stable and alpha provide the same skills and connect to the same CaesuraO service; enabling both can request guidance twice and consume extra credits. To switch, turn off or uninstall the other plugin, install this one, and start a new conversation.

Preview analyses use your account’s credits and follow the same privacy and storage terms as stable.

## Install in the ChatGPT app

1. In the ChatGPT desktop app, open the **Plugins Directory** and add a marketplace with this repository: `caesura-io/caesurao-plugins-alpha`.
2. Choose that marketplace, install **CaesuraO Alpha (Preview)**, and connect your CaesuraO account when asked.
3. Start a new chat.

## Install in Codex

```sh
codex plugin marketplace add caesura-io/caesurao-plugins-alpha
codex plugin add caesurao-alpha@caesurao-alpha
```

Start a new session and connect your CaesuraO account when asked. To check the connection, ask whether CaesuraO is connected: the setup skill uses `get_account`, which sends no analysis text and uses no credits.

## Install in the Claude app and Cowork

1. Open **Customize → Plugins → Add marketplace** and enter `caesura-io/caesurao-plugins-alpha`.
2. Install **CaesuraO Alpha (Preview)**, open its **Connectors** settings, and choose **Connect**.
3. Start a new conversation.

## Install in Claude Code

```text
/plugin marketplace add caesura-io/caesurao-plugins-alpha
/plugin install caesurao-alpha@caesurao-alpha
```

Choose the installation scope when prompted. Start a new session, run `/mcp`, select `plugin:caesurao-alpha:caesurao`, and choose **Authenticate**.

## Update to the latest version

New preview versions are published here; your app picks them up when it refreshes the marketplace. Start a new conversation afterwards, since running conversations keep the skills they already loaded.

- **ChatGPT app:** quit and reopen ChatGPT, then update **CaesuraO Alpha (Preview)** in the Plugins Directory if an update is offered.
- **Claude app and Cowork:** sync the marketplace in plugin settings (turn on automatic sync where available) and check the installed version.
- **Codex:**

  ```sh
  codex plugin marketplace upgrade caesurao-alpha
  codex plugin add caesurao-alpha@caesurao-alpha
  ```

- **Claude Code:** `/plugin` → Installed → **CaesuraO Alpha (Preview)** → Update now, or from your shell:

  ```sh
  claude plugin marketplace update caesurao-alpha
  claude plugin update caesurao-alpha@caesurao-alpha
  ```

  To update automatically, open `/plugin` → Marketplaces → `caesurao-alpha` → Enable auto-update.

If the app asks you to reconnect CaesuraO, use its connector settings; never paste passwords, API keys, or login codes into a chat.

## Pause, disconnect, and data

Say “Stop CaesuraO analysis in this chat” to pause analysis in the current conversation, and “Resume CaesuraO analysis” to resume. To disconnect the account, use the host’s connector controls. Selected text and results are handled under the [Privacy Policy](https://caesurao.com/privacy) and [Terms of Service](https://caesurao.com/tos). Masking is performed by the assistant and is not guaranteed anonymization.

Support: support@caesura.io
