# ChatGPT Ads Launch Kit

Build a launch-ready ChatGPT Ads campaign for any brand, without guessing at the new platform. Built by [Sulka Labs](https://sulkalabs.com).

This plugin turns a brand's details into everything you need to launch: ad group structure, ad copy, context hints for targeting, UTM tracking, an ad creative prompt, and a bulk-upload workbook that matches ChatGPT Ads' own template so it drops straight into the platform.

## What it does

Once installed, just say something like "build a ChatGPT Ads campaign for my brand" and it walks you through the whole thing:

- Learns your brand from a website or a few quick details, including what style of ad creative you're after
- Sets a clean campaign structure (one landing page, one ad group, a Daily budget you control)
- Writes 4 to 5 ad copy options for you to pick from, inside the platform's real character limits, title up to 24 characters, copy up to 48
- Writes 20 to 30 context hints, the natural phrases ChatGPT Ads uses to target, instead of keywords
- Wires UTM tracking so you can see ChatGPT traffic in your analytics
- Writes an image prompt for your ad creative and explains how to host it publicly, wherever you already keep your images
- Assembles a bulk-upload workbook (`campaigns`, `adgroups`, `ads`) matching ChatGPT Ads' own template exactly, ready to load straight into the platform's bulk upload tool

## Why it is built this way

- **Copy gets approved before the sheet is built.** You review and pick, then it assembles the file. No wasted output.
- **One ad length, no guessing.** ChatGPT Ads' bulk upload template only has one length, title up to 24 characters, copy up to 48, so every option already fits instead of getting drafted long and cut down later.
- **Context hints, not keywords.** ChatGPT Ads targets on the shape of the conversation, so the kit writes natural phrases a real person would type.
- **Tracking from day one.** In-platform reporting is thin, so your UTMs are your real scoreboard.
- **No required connectors.** Creative hosting works with whatever you already use, Google Drive, Imgur, Dropbox, your own site. Nothing needs to be wired into Claude for this to work.

## How to use it

1. Install the plugin.
2. Say "build a ChatGPT Ads campaign for [your brand]" or paste your website and brand details.
3. Answer a couple of quick questions, including what kind of ad creative you want, then pick your favorite ad copy.
4. Generate and host your ad creative using the prompt the kit writes for you.
5. Get a bulk-upload workbook that matches ChatGPT Ads' own template, ready to drag into the platform.

## What's inside

- **chatgpt-ads-campaign-builder** skill: the full build workflow, a copywriting guide with the exact character specs and voice, a worked example, and a script that generates the bulk-upload workbook with validation built in (catches bad IDs, over-length copy, unsupported countries, and placeholder image links before you try to upload).

## Requirements

- The bulk-upload step uses `openpyxl`. If it is not already available, run `pip install openpyxl`.
- No API keys, no account connections, no external setup.

## A note on the platform

The prompts and workflow are model-agnostic. What you are building for is ChatGPT Ads, OpenAI's product that places ads inside live ChatGPT conversations. The platform is new and evolving. The bulk-upload workbook is built directly from ChatGPT Ads' own template, which currently defaults to Views (CPM) campaigns, Clicks (CPC) is listed but the template notes it was rolling out in beta at time of writing. Confirm in your ChatGPT Ads dashboard which objectives are live for your account. Expect updates as the platform adds features.

---

Built by Sulka Labs, a human-led, AI-driven DTC growth partner. If you would rather have us build, launch, and manage it for you, reach out at [sulkalabs.com](https://sulkalabs.com).
