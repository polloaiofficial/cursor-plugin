# Pollo AI plugin

[Pollo](https://pollo.ai) is a multi-model studio: one account and one credit balance for image and video models such as Seedance, Kling, Veo, Sora, GPT Image, and Nano Banana.

This plugin connects that studio to Cursor and Grok Bot. After you sign in with your Pollo account, the agent can list what a model accepts, estimate credits, generate or edit, then reuse the result as the next still or clip — without leaving the chat.

The plugin itself is free to install. Each generation deducts the same credits you already use on [pollo.ai](https://pollo.ai).

## Install

When the listing is live, search **Pollo AI** in Cursor (`/add-plugin`) or in Grok Bot Plugins and add it. Sign in when prompted. No API key.

Setup notes and the MCP URL: [pollo.ai/mcp](https://pollo.ai/mcp).

## Local development

Copy the plugin files into Cursor's local plugin folder:

```bash
git clone https://github.com/polloaiofficial/cursor-plugin.git
mkdir -p ~/.cursor/plugins/local/pollo
cp -R cursor-plugin/.cursor-plugin cursor-plugin/commands cursor-plugin/assets cursor-plugin/mcp.json cursor-plugin/README.md cursor-plugin/LICENSE ~/.cursor/plugins/local/pollo/
```

Reload the window (`Developer: Reload Window`). You should see **Pollo AI** under Plugins and an MCP server named `pollo`. First use opens browser login.

After pulling updates, copy the files again and reload. To remove the local copy:

```bash
rm -rf ~/.cursor/plugins/local/pollo
```

## What is in this repo

A thin Marketplace package only:

- `mcp.json` — remote server `https://mcp.pollo.ai/mcp` (OAuth)
- `/pollo` — a slash command that tells the agent how to pick models, estimate, generate, and chain image → video
- `assets/logo.png` — listing artwork

The generation backend is not in this repository. Outbound calls go to `mcp.pollo.ai` and `pollo.ai`.

## Support

- Product: [pollo.ai](https://pollo.ai)
- MCP guide: [pollo.ai/mcp](https://pollo.ai/mcp)
- Privacy: [pollo.ai/privacy-policy](https://pollo.ai/privacy-policy)
- Terms: [pollo.ai/terms-and-conditions](https://pollo.ai/terms-and-conditions)
- Issues: [github.com/polloaiofficial/cursor-plugin/issues](https://github.com/polloaiofficial/cursor-plugin/issues)
- Email: [support@pollo.ai](mailto:support@pollo.ai)

## License

[MIT](./LICENSE).
