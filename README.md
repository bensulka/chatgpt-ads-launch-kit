# ChatGPT Ads Launch Kit

A free Claude plugin that turns your brand into a launch-ready ChatGPT Ads campaign, and delivers it as a bulk-upload workbook that matches ChatGPT Ads' own template exactly. No retyping into the platform by hand, no dashboard, no API keys, no code.

Built by [Sulka Labs](https://sulkalabs.com), a human-led, AI-driven growth partner for DTC brands.

---

## What it does

Say "build a ChatGPT Ads campaign for my brand" and the kit walks you through the whole thing:

- Learns your brand from a website or a few quick details, including what style of ad creative you want
- Sets a clean campaign structure and a budget you control (Daily by default, so you're never committing more than you meant to on day one)
- Writes 4 to 5 ad copy options to pick from, inside the platform's real character limits, title up to 24 characters, copy up to 48
- Writes 20 to 30 context hints, the natural phrases ChatGPT Ads targets on instead of keywords
- Wires UTM tracking so you can see ChatGPT traffic in your analytics
- Writes a ready-to-paste image prompt for your ad creative, and walks you through hosting it anywhere you like
- Assembles a bulk-upload workbook (`campaigns`, `adgroups`, `ads`) that matches ChatGPT Ads' own template field for field, ready to drag straight into the platform's bulk upload tool

Everything is generated in-chat. It does not require any account connections, Google Drive included, you paste your brand details or a website URL and walk away with a file that's actually ready to upload.

---

## Install

Pick the version of Claude you use.

### Claude desktop app (most people)

1. Download `chatgpt-ads-launch-kit.plugin` from this repo (click the file, then Download).
2. Open the Claude desktop app and click **Customize**.
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

## What you need

Three things, that's it:

1. **Your product's URL.** The landing page you want the ad to send people to.
2. **A picture of your product.** Doesn't need to be a professional shot, the kit can also generate an AI creative for you if you'd rather.
3. **Claude, with this kit installed.**

---

## Requirements

- The bulk-upload step uses `openpyxl`. If it is not already available, run `pip install openpyxl`.
- No API keys, no account connections, no external setup. Image hosting is up to you (Google Drive, Imgur, Dropbox, your own site all work).

## A note on the platform

You are building for ChatGPT Ads, OpenAI's product that places ads inside live ChatGPT conversations. The platform is new and evolving. This kit's bulk-upload workbook is built directly from ChatGPT Ads' own template, which currently defaults to Views (CPM) campaigns, Clicks (CPC) is listed but the template notes it was rolling out in beta at time of writing. Confirm in your ChatGPT Ads dashboard which objectives are live for your account. Expect updates as the platform matures.

---

## Want a human to run it for you?

This kit is free, forever. If you would rather have a senior team build, launch, and manage your ChatGPT Ads (and your Google, Meta, and Amazon) so you can scale profitably without operating it yourself, Sulka Labs does exactly that for DTC brands. Reach out at [sulkalabs.com](https://sulkalabs.com).

## License

MIT. Use it, fork it, adapt it.
