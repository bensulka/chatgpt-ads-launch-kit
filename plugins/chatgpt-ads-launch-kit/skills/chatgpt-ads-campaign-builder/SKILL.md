---
name: chatgpt-ads-campaign-builder
description: Build a complete, launch-ready ChatGPT Ads campaign for any brand (ad groups, Version A/B ad copy, context hints, UTM tracking URLs) and deliver it as a spreadsheet. Use whenever someone wants to create, build, or launch a ChatGPT Ads campaign, write ChatGPT Ads copy or context hints, set up ChatGPT Ads tracking, or turn brand details into a launch-ready ChatGPT Ads sheet. Trigger on phrases like "build a ChatGPT Ads campaign", "write ChatGPT Ads copy", "set up ChatGPT Ads for my brand", "context hints for ChatGPT Ads", "launch sheet for ChatGPT Ads", or any request to plan or produce a ChatGPT Ads campaign. Always load this skill before writing any ChatGPT Ads copy, context hints, or launch sheet.
---

# ChatGPT Ads Campaign Builder

Turn a brand's details into a launch-ready ChatGPT Ads campaign: ad group structure, Version A and Version B ad copy, context hints, UTM tracking, and a spreadsheet the user can load straight into the platform.

This is the reusable engine behind the Sulka Labs ChatGPT Ads system. It is brand-agnostic. It works for any brand, product, or offer.

## What this skill produces

For each ad group:
- **Ad group name** (naming convention below)
- **Destination URL(s) with UTMs** (A/B variants for tracking)
- **Version A** headline + description (full, benefit-driven)
- **Version B** headline + description (short, truncation-safe version of the same idea)
- **Context hints** (20 to 30 intent signals that tell ChatGPT when to serve the ad)

The final deliverable is a **spreadsheet (.xlsx)** with three tabs: Campaign, Ad Copy, and Context Hints.

## Core principle: approve copy before building the sheet

The sheet is the last step, not the first. Present copy and context hints in chat, let the user review and approve, then build the sheet. Building the sheet before approval wastes a round trip and produces a file nobody can use yet.

The flow:
1. Collect inputs
2. Decide ad group structure
3. Draft Version A copy options in chat, user picks
4. Write Version B (condensed) plus context hints, user approves
5. Only then, build the spreadsheet

## Step 1: Collect inputs

Gather the following before writing. If the user shared a website, a brand brief, or existing copy, pull from that. If something essential is missing, ask before writing rather than guessing.

Essentials:
1. **Brand name** and a one-line description of what they sell
2. **What to advertise** (the whole brand for awareness, a specific product, or a category)
3. **Ideal customer** and what makes the brand different
4. **Goal** (awareness, traffic, etc. This drives the objective and the copy angle)
5. **Destination URL (base)** (the landing page the ad clicks to, without UTMs)

If the user only has a website, offer to read it and pull the brand details out yourself, then confirm them before writing.

Campaign settings (use these defaults unless the user specifies otherwise):
- **Campaign name** pattern: `[Theme] - [Objective] - M/DD/YY` (example: `June Launch Test - Clicks - 6/20/26`)
- **Objective:** `Clicks` (CPC) is the default for awareness and traffic. ChatGPT Ads also offers CPM. Use CPM only if the goal is pure impressions. Conversion campaigns are not available yet, so do not offer one.
- **Budget:** ask, or default to a small test (for example `$500` total, `Daily - about $17/day`). Recommend daily budgets so the campaign can be paused and resumed.
- **UTM campaign value:** `ChatGPTAdsTest` unless the user specifies otherwise

## Step 2: Decide ad group structure

Most first tests start with a single ad group. Add more only when there is a clear reason (distinct products, audiences, or landing pages). Each ad group maps to one landing page and one set of context hints.

Naming convention:
```
[Segment] - [Page Type] - V[number]
```
- **Segment** = product, category, or audience (example: "General", "Frozen Snacks", "Retail Awareness")
- **Page Type** = the landing page (example: "Home Page", "Category Page", "Product Page")
- **V[number]** = version, starting at V1

Examples: `General - Home Page - V1`, `Frozen Snacks - Category Page - V1`

If the user gives a name, use it as-is.

## Step 3: Build destination URLs with UTMs

UTMs let the user see ChatGPT traffic in their analytics (for example GA4), which matters because in-platform attribution is thin.

```
[base URL]?utm_source=openai&utm_medium=cpc&utm_campaign=[campaign]&utm_content=[identifier]
```
- `utm_source` = always `openai` (how ChatGPT traffic shows up in analytics)
- `utm_medium` = always `cpc`
- `utm_campaign` = the UTM campaign value (default `ChatGPTAdsTest`)
- `utm_content` = `[ShortSegment]V-A` or `[ShortSegment]V-B` (example: `GeneralV-A`, `FrozenSnacksV-B`)

Version A and Version B get the same base URL and differ only in `utm_content`, so the user can see which creative drove the click.

## Step 4: Write the copy

Read `references/copywriting-guide.md` for the full character specs, voice approach, and prompt structure. The short version:

- **Version A (full):** Headline up to 50 chars (title case), Description up to 100 chars (sentence case). Aim around 30 to 45 and 80 to 100 so it rarely truncates.
- **Version B (short, truncation-safe):** Headline up to 25 chars, Description up to 50 chars. Same core idea as Version A, stripped down.
- Always show the character count in parentheses after each field so the user can verify at a glance.
- Write conversationally. These ads appear inside a chat where someone is already problem-solving, so copy that reads like a helpful answer beats hard-sell ad-speak.
- Match the brand's own voice. If the user shared approved copy or brand guidelines, draw from that language instead of inventing claims. Never invent features, guarantees, or numbers a brand has not confirmed.
- Do not use em dashes.

On the first pass, give **4 to 5 Version A options** to choose from. Once the user picks one, write Version B as the condensed version of that chosen headline and description. Do not finalize Version B until Version A is locked.

## Step 5: Write context hints

Context hints are ChatGPT Ads' targeting. They are short, natural phrases describing the conversations where the ad is a relevant solution. They guide matching but are not exact-match rules, so they should read like things a real person would actually type or discuss.

Write 20 to 30 per ad group, covering a mix of:
- **Category or product terms** (example: "frozen fruit snack", "healthy dessert")
- **Problem or need statements** (example: "I want a sweet snack that isn't junk")
- **Shopping or comparison queries** (example: "best healthy snacks for kids")
- **Conversational or long-tail** (example: "what's a good frozen treat that's actually good for you")

Keep them specific to the brand and offer. Avoid hints so generic they would match any unrelated conversation. Do not finalize hints until the copy is approved.

## Step 6: Present for approval in chat

Before building the sheet, present everything in this structure so the user can approve or tweak:

```
Ad Group Name: [Name]

Destination URLs:
  Version A: [full URL with UTMs]
  Version B: [full URL with UTMs]

Version A
  Headline: [headline] ([X] chars)
  Description: [description] ([X] chars)

Version B
  Headline: [headline] ([X] chars)
  Description: [description] ([X] chars)

Context Hints:
[list, one per line]
```

Then ask: "Want to adjust anything before I build the launch sheet?"

## Step 7: Build the spreadsheet (only after approval)

Once copy and hints are approved, assemble the campaign into a JSON file matching the schema in the docstring of `scripts/build_campaign_sheet.py`, then run:

```bash
python scripts/build_campaign_sheet.py campaign.json "[Brand] ChatGPT Ads Campaign Launch.xlsx"
```

This writes a three-tab workbook (Campaign, Ad Copy, Context Hints) with character counts computed automatically. Save the file where the user can reach it and present it to them.

`openpyxl` is required. If it is not installed, run `pip install openpyxl` (add `--break-system-packages` if the environment requires it).

## Step 8: Iteration

- User wants more options: give 4 to 5 new Version A combos
- Version A locked: write Version B as the condensed version
- Both versions locked: finalize context hints
- Everything approved: build or refresh the sheet
- Adding an ad group later: append it to the same JSON and rebuild so all ad groups live in one sheet

## A worked example

See `examples/worked-example.md` for one brand run all the way through, so the expected output shape is concrete.
