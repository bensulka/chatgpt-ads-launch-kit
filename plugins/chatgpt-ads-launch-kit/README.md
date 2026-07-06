# ChatGPT Ads Launch Kit

Build a launch-ready ChatGPT Ads campaign for any brand, without guessing at the new platform. Built by [Sulka Labs](https://sulkalabs.com).

This plugin turns a brand's details into everything you need to launch: ad group structure, Version A and Version B ad copy, context hints for targeting, UTM tracking, and a spreadsheet you can load straight into ChatGPT Ads.

## What it does

Once installed, just say something like "build a ChatGPT Ads campaign for my brand" and it walks you through the whole thing:

- Learns your brand from a website or a few quick details
- Sets a clean campaign structure (one landing page, one ad group, a budget you control)
- Writes 4 to 5 ad copy options for you to pick from, inside the platform's character limits
- Writes a short, truncation-safe version of your winning ad so it still lands when the platform clips it
- Writes 20 to 30 context hints, the natural phrases ChatGPT Ads uses to target, instead of keywords
- Wires UTM tracking so you can see ChatGPT traffic in your analytics
- Assembles a three-tab launch spreadsheet (Campaign, Ad Copy, Context Hints) ready to load into the platform

## Why it is built this way

- **Copy gets approved before the sheet is built.** You review and pick, then it assembles the file. No wasted output.
- **Two ad versions, always.** ChatGPT Ads truncates longer ads inside the chat, so every ad gets a full version and a short fallback that survives being cut off.
- **Context hints, not keywords.** ChatGPT Ads targets on the shape of the conversation, so the kit writes natural phrases a real person would type.
- **Tracking from day one.** In-platform reporting is thin, so your UTMs are your real scoreboard.

## How to use it

1. Install the plugin.
2. Say "build a ChatGPT Ads campaign for [your brand]" or paste your website and brand details.
3. Answer a couple of quick questions, then pick your favorite ad copy.
4. Get a launch-ready spreadsheet to load into ChatGPT Ads.

## What's inside

- **chatgpt-ads-campaign-builder** skill: the full build workflow, a copywriting guide with the exact character specs and voice, a worked example, and a script that generates the launch spreadsheet with character counts calculated for you.

## Requirements

- The spreadsheet step uses `openpyxl`. If it is not already available, run `pip install openpyxl`.
- No API keys, no account connections, no external setup.

## A note on the platform

The prompts and workflow are model-agnostic. What you are building for is ChatGPT Ads, OpenAI's product that places ads inside live ChatGPT conversations. The platform is new and evolving. Conversion campaigns are not available yet, so the kit runs Clicks by default. Expect updates as the platform adds features.

---

Built by Sulka Labs, a human-led, AI-driven DTC growth partner. If you would rather have us build, launch, and manage it for you, reach out at [sulkalabs.com](https://sulkalabs.com).
