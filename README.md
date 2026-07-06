# ChatGPT Ads Launch Kit

A free Claude plugin that turns your brand into a launch-ready ChatGPT Ads campaign. Ad group structure, Version A and Version B ad copy, context-hint targeting, UTM tracking, and a three-tab launch spreadsheet. No dashboard, no API keys, no code.

Built by [Sulka Labs](https://sulkalabs.com), a human-led, AI-driven growth partner for DTC brands.

---

## What it does

Say "build a ChatGPT Ads campaign for my brand" and the kit walks you through the whole thing:

- Learns your brand from a website or a few quick details
- Sets a clean campaign structure and a budget you control
- Writes 4 to 5 ad copy options to pick from, inside the platform's character limits
- Writes a short, truncation-safe version of your winning ad so it still lands when the platform clips it
- Writes 20 to 30 context hints, the natural phrases ChatGPT Ads targets on instead of keywords
- Wires UTM tracking so you can see ChatGPT traffic in your analytics
- Assembles a launch spreadsheet (Campaign, Ad Copy, Context Hints) ready to load into the platform

Everything is generated in-chat. It does not connect to any account. You paste your brand details or a website URL, and you walk away with a launch-ready campaign.

---

## Install

Pick the version of Claude you use.

### Claude desktop app (most people)

1. Download `chatgpt-ads-launch-kit.plugin` from this repo (click the file, then Download).
2. Open the Claude desktop app and click **Customize** in the top right.
3. Go to the **Plugins** section.
4. Use the upload option and select the `.plugin` file you downloaded.
5. Done. Say "build a ChatGPT Ads campaign for my brand" to start.

### Claude Code (developers, terminal)

In the Claude Code prompt, run:

```
/plugin marketplace add bensulka/chatgpt-ads-launch-kit
/plugin install chatgpt-ads-launch-kit@sulka-labs-chatgpt
```

### claude.ai in the browser (Pro, no desktop app)

Browser Claude does not install plugins, but it does support Skills.

1. Open the skill file in this repo at `plugins/chatgpt-ads-launch-kit/skills/chatgpt-ads-campaign-builder/SKILL.md`.
2. In Claude, go to **Customize > Skills**, add a new skill, and paste the file contents in.
3. Or paste the skill straight into the chat as a prompt.

---

## Requirements

- The spreadsheet step uses `openpyxl`. If it is not already available, run `pip install openpyxl`.
- No API keys, no account connections, no external setup.

## A note on the platform

You are building for ChatGPT Ads, OpenAI's product that places ads inside live ChatGPT conversations. The platform is new and evolving. Conversion campaigns are not available yet, so the kit runs Clicks by default. Expect updates as the platform adds features.

---

## Want a human to run it for you?

This kit is free, forever. If you would rather have a senior team build, launch, and manage your ChatGPT Ads (and your Google, Meta, and Amazon) so you can scale profitably without operating it yourself, Sulka Labs does exactly that for DTC brands. Reach out at [sulkalabs.com](https://sulkalabs.com).

## License

MIT. Use it, fork it, adapt it.
