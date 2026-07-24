---
name: chatgpt-ads-campaign-builder
description: Build a complete ChatGPT Ads campaign (ad groups, ad copy, context hints, UTM URLs) for any brand, delivered as a bulk-upload-ready workbook matching ChatGPT Ads' own template so it drops straight into the platform. Use whenever the user wants to build a ChatGPT Ads campaign for their own brand or a client's brand. Trigger on "build a ChatGPT Ads campaign for [brand]", "build the ChatGPT ad for [client]", "write ChatGPT Ads copy and context hints for [brand]", "turn this into a ChatGPT Ads bulk upload sheet", or any time someone shares brand, offer, audience, or goal details and wants a ChatGPT Ads build. Load before writing ChatGPT Ads copy, context hints, or building the bulk upload sheet.
---

# ChatGPT Ads Campaign Builder

This skill turns a brand's details into a launch-ready ChatGPT Ads campaign: copy, context hints, ad creative, and a bulk-upload workbook that matches the exact format ChatGPT Ads' own bulk upload feature expects. The output isn't a summary for a human to retype, it's the file that gets uploaded directly.

It works for any brand, your own or a client's.

## What This Skill Produces

For each ad group:
- **Ad group name** (alphanumeric-only naming convention below)
- **Destination URL(s) with UTMs**
- **Ad copy** — title (up to 24 chars) + copy (up to 48 chars) per ad, one or more ads per ad group
- **Context hints** — 20 to 30 intent signals that tell ChatGPT when to serve the ad
- **A hosted creative image** for each ad, generated (or supplied) by the user and hosted anywhere with a public direct-view link

The final deliverable is a **bulk-upload .xlsx** with three tabs (`campaigns`, `adgroups`, `ads`) matching ChatGPT Ads' own template field for field. This is built directly from the platform's real bulk upload template, not a general-purpose summary that someone has to retype into the platform by hand.

## The Flow (important: copy gets approved in chat BEFORE the sheet is built)

The sheet is the last step, not the first. Review and approve copy, hints, and creative in chat first, then build the sheet. Building the sheet before approval wastes a round trip and produces a file nobody can use yet.

1. Collect inputs
2. Decide ad group structure
3. Draft ad copy options in chat → user picks
4. Write context hints → user approves
5. Generate and host the ad creative → get a live image link
6. Build the bulk-upload workbook

## Step 1: Collect Inputs

You need the following before writing. Pull from whatever the user shares, a brand brief, a website, pasted product details. If something essential is missing, ask before writing rather than guessing.

Essentials:
1. **Brand name** and a one-line description of what they sell
2. **What to advertise** — the whole brand for awareness, a specific product, or a category
3. **Ideal customer** and what makes them different
4. **Goal** — awareness, traffic, etc. (drives the objective and copy angle)
5. **Destination URL (base)** — the landing page the ad clicks to, without UTMs

Also ask, as its own question, not buried inside the others:

6. **Creative direction (optional).** Is there a type of ad image in mind? Give a few examples so the question isn't abstract: a straight product shot on a clean background, a lifestyle shot of someone using the product, a bold text-forward graphic with no photography, a flat lay, a UGC-style photo that looks like a phone snapshot instead of a polished shoot. If there's no preference, say you'll default to a straightforward photography style that fits the product category (a kitchen scene for a food brand, an outdoor scene for a gear brand, a clean studio shot for a tech accessory), and that it can be redirected once they see it. This answer is what drives the image prompt in Step 7, so don't skip asking it just because it's optional, an unanswered question here means guessing at the scene later.

Campaign settings map directly to fields the bulk template requires. These are real platform constraints, not style choices:

- **campaign_name**: alphanumeric characters only, no spaces, dashes, or punctuation. This is used as a literal ID across every tab in the sheet, so a stray dash breaks the whole workbook. Default pattern: **Product/Category + Objective + Date**, each segment capitalized and run together with no separators since punctuation isn't allowed (date as `MMDDYY`, always 6 digits so segment lengths stay consistent). Example: a Ridgeline Backpack campaign, Clicks objective, launched 7/22/26 becomes `RidgelineBackpackClicks072226`. If the user gives a name with punctuation or spaces in it, strip it into this same capitalized run-together format and say what it was changed to.
- **budget_max**: a number, the spend amount in the account's currency, no unit conversion needed (plain dollars, not micros). ChatGPT Ads enforces a confirmed $25/day minimum on Daily budgets, if `budget_type` is Daily, keep `budget_max` at $25 or above or the upload fails with `CampaignDailyBudgetMinimumValidationError`. Default to $30 if the user hasn't specified an amount, to clear that floor with a small margin.
- **budget_type**: `Lifetime` or `Daily`. Default to `Daily` unless told otherwise, it's the safer starting point for a first test since it caps what can go out in a single day rather than committing the full budget up front.
- **launch_date** / **end_date**: dates. Ask, or default launch_date to today and leave end_date blank for an ongoing test.
- **objective**: `Views` or `Clicks`. This decides whether the ad group bids on CPM or CPC. Ask which the user wants. One thing worth knowing: the bulk template this skill is built from is literally named a CPM template, and its own field description notes clicks campaigns are "rolling out in beta." That's not a reason to avoid offering Clicks, ChatGPT Ads does list it as a real, selectable objective, but confirm in the ChatGPT Ads dashboard that Clicks is live for the account before building a CPC campaign around it. Default to `Views` if that hasn't been confirmed either way.
- **target_countries**: a JSON array of 2-letter country codes. As of this template, only `AU`, `CA`, `GB`, `JP`, `KR`, `NZ`, `US` are supported. If the target market is somewhere outside that list, flag it, this template can't target there yet.
- **UTM campaign value**: `ChatGPTAdsTest` unless told otherwise.

## Step 2: Decide Ad Group Structure

Most first tests start with a single ad group. Add more only when there's a clear reason (distinct products, audiences, or landing pages). Each ad group maps to one landing page and one set of context hints.

**adgroup_name** follows the same alphanumeric-only rule as campaign_name, since it's also a literal ID. Default pattern: **Product/Category + Bid + Creative Version**, same capitalized run-together format, bid written as the word `Bid` plus the number (no dollar sign, since punctuation isn't allowed) and version as `V1`, `V2`, etc. Example: a Ridgeline Backpack ad group at a $4 bid, first creative version, becomes `RidgelineBackpackBid4V1`.

If a name comes in with punctuation in it, strip it down and say what it was changed to.

## Step 3: Build Destination URLs with UTMs

UTMs let the brand see ChatGPT traffic in GA4, which matters because in-platform attribution is thin.

```
[base URL]?utm_source=openai&utm_medium=cpc&utm_campaign=[campaign]&utm_content=[identifier]
```
- `utm_source` = always `openai` (how ChatGPT traffic shows up in GA4)
- `utm_medium` = always `cpc`
- `utm_campaign` = the UTM campaign value (default `ChatGPTAdsTest`)
- `utm_content` = a short tag per ad (e.g., `GeneralA`, `GeneralB`) so it's clear which creative drove the click

Each ad in an ad group gets its own `link`, differing only in `utm_content`.

## Step 4: Write the Copy

Read `references/copywriting-guide.md` for the full voice approach and prompt structure. The short version:

- **One format, not two.** Titles run 16 to 24 characters recommended (50 hard max), copy runs 32 to 48 characters recommended (100 hard max), per OpenAI's own bulk upload schema checklist. Write to the recommended range by default, it reads best in-line with a chat response, going past it isn't a rejected file, just a weaker ad.
- Always show the character count in parentheses after each field so it's easy to verify at a glance.
- Write conversationally. These ads appear inside a chat where someone is already problem-solving, so copy that sounds like a helpful answer beats hard-sell ad-speak.
- Match the brand's own voice. If approved copy or brand guidelines exist, draw from that language instead of inventing claims.
- Skip em dashes, they read a little stiff for how conversational this copy needs to be. Use periods or commas instead.
- **Multiple ads in one ad group should be different angles, not different lengths.** There is no "safe fallback" format on this platform the way there is on Meta. Two ads under the same ad group are two different hooks, each fitting the same 24/48 caps.

On the first pass, give **4 to 5 title/copy combos** to choose from. Pick just one to launch with, or pick two to run as separate ads testing different angles.

## Step 5: Write Context Hints

Context hints are ChatGPT Ads' targeting. They are short, natural phrases describing conversations where the ad is a relevant solution. They guide matching but are not exact-match rules, so they should read like things a real person would actually type or discuss.

Write 20 to 30 per ad group, covering a mix of:
- **Category/product terms** (e.g., "frozen fruit snack", "healthy dessert")
- **Problem or need statements** (e.g., "I want a sweet snack that isn't junk")
- **Shopping/comparison queries** (e.g., "best healthy snacks for kids")
- **Conversational/long-tail** (e.g., "what's a good frozen treat that's actually good for you")

Keep them specific to the brand and offer. Avoid hints so generic they'd match any unrelated conversation. In the final sheet these get stored as one JSON array string per ad group, not a separate tab, but write and review them as a plain list in chat first.

## Step 6: Present for Approval in Chat

Before building anything, present everything in this structure so it can be approved or tweaked:

```
Campaign: [campaign_name] | Objective: [Views/Clicks] | Countries: [list]

Ad Group Name: [adgroup_name]

Ad 1
  Title: [title] ([X] chars)
  Copy: [copy] ([X] chars)
  Link: [full URL with UTMs]

Ad 2
  Title: [title] ([X] chars)
  Copy: [copy] ([X] chars)
  Link: [full URL with UTMs]

Context Hints:
[list, one per line]
```

Then ask: "Want to adjust anything before I generate the creative and build the sheet?"

## Step 7: Generate and Host the Ad Creative

Every ad row in the bulk template needs a live `image_link`: a publicly viewable, hosted image URL, square, 640 to 1200px, PNG or JPG.

Don't assume any particular storage tool is connected. Most people running this skill will not have a Drive connector or any other file-storage MCP wired into their Claude setup. The default path has to work with nothing but a chat window.

1. **Generate the creative prompt, driven by the creative direction from Step 1.** Don't reuse one fixed prompt formula for every brand, the scene and style should change based on what's actually wanted. Build each prompt from five slots:
   - **Subject/scene**: the product and what's happening around it. This is the slot that changes most based on creative direction, for example a product shot uses "the product alone on a clean surface," a lifestyle shot uses "someone using the product in a real setting," a UGC-style shot uses "a casual phone-quality photo of the product in someone's home," a text-forward graphic uses "a bold color block with the product photo inset small."
   - **Must-include elements**: an offer callout or badge if there's a promo, brand colors if any were given.
   - **Style/mood**: tie this to the creative direction too (clean commercial photography, candid and unpolished, minimalist studio, bold graphic design) rather than always defaulting to the same look.
   - **What to avoid**: things that read as generic AI output (stock-photo feel, watermarks, extra fingers or garbled text) plus anything explicitly unwanted (no people in frame, no competitor logos, etc).
   - **Composition note**: square 1:1, leave clear space somewhere for a headline overlay if that's wanted later.

   Write one full prompt per ad so the creative matches that specific ad's angle, don't generate one generic image and reuse it everywhere. Give the full prompt text, ready to paste, not just a description of what the prompt should contain.

   Tip: for consistent creative across multiple ads, generate one clean, isolated reference photo of the product first (plain background, no scene, no text), then reference that image when generating each ad's creative so the product looks the same in every shot.
2. **Say where to run it.** Paste the prompt into ChatGPT, Higgsfield, or any other AI image tool available, or skip AI entirely and use an existing product photo or brand asset. Any of these is fine, the sheet only cares about the final URL.
3. **Explain how to host it.** The image needs a URL that resolves straight to the file, not a login-gated page or a viewer page. Lay out these options plainly:
   - Google Drive: upload the file, right-click it, Share, set general access to "Anyone with the link, Viewer," then use `https://drive.google.com/uc?export=view&id=[the file id from the share link]` as the `image_link`. This format is what resolves to the raw image instead of Drive's viewer page.
   - Any other host already in use for images: Imgur, Dropbox with a public link, a site's own media library, a CDN. As long as the link opens directly to the image, it works.
4. **If a file-storage tool is actually connected in this session** (check the available tools before assuming), offer to handle steps 2 to 3 automatically as a shortcut: upload the generated image and hand back a direct-view link. Even then, flag that most storage tools have no way for Claude to change sharing settings, so a private file's link won't resolve publicly. That's a one-time manual fix in the storage tool's own sharing UI (share the destination folder once, everything uploaded into it afterward inherits the access), not something to promise as fully automatic.
5. **Collect the final `image_link` for each ad** before moving on. Don't build the sheet with a placeholder link in it.

## Step 8: Build the Bulk-Upload Workbook (only after approval)

Once copy, hints, and image links are approved, assemble the campaign into a JSON file matching the schema in the docstring of `scripts/build_bulk_upload_sheet.py`, then run:

```bash
python scripts/build_bulk_upload_sheet.py campaign.json "[Brand] ChatGPT Ads Bulk Upload.xlsx"
```

This writes the exact three-tab structure (`campaigns`, `adgroups`, `ads`) the platform's bulk upload feature expects, headers matched exactly to the platform's own template. The script validates before writing and will flag real problems instead of silently producing a broken file: non-alphanumeric IDs, titles or copy over the character caps, unsupported target countries, and any `image_link` that's still a placeholder. Fix anything it flags before delivering the file.

`openpyxl` is required. If it is not installed, run `pip install openpyxl` (add `--break-system-packages` if the environment requires it).

**Default delivery: save it locally and hand it over directly.** Write the file to the working/output directory and present it the normal way. This works for everyone regardless of what's connected, and it's the right default since the whole point of this file is that someone downloads it and drags it into ChatGPT Ads' bulk upload tool as-is, not that it lives in a shared drive.

**Only if a Drive (or similar) connector is available and it's wanted there**, also upload it with the storage tool's file-creation call, keeping the file as a real `.xlsx`:
- `title`: `[Brand] | ChatGPT Ads Bulk Upload | M/DD/YY.xlsx`
- `parentId`: a specific folder if one is given, otherwise leave it off and report the link
- the .xlsx content, uploaded without converting it to a native Google Sheet, since the bulk upload tool needs a real .xlsx, not a Sheet

Either way, make clear this file is meant to be downloaded and uploaded as-is into ChatGPT Ads' bulk upload tool, not opened and reformatted first.

## Step 9: Iteration

- More options wanted → give 4 to 5 new title/copy combos
- An ad is locked → move to the next ad or lock context hints
- Everything approved → generate creative, then build/refresh the sheet
- Adding an ad group later → append it to the same JSON and rebuild so all ad groups live in one sheet
- Swapping creative on an existing ad → re-host the new image wherever it's being hosted, update `image_link` in the JSON, rebuild
- A different type of ad image is wanted (e.g., "make it a flat lay instead," "add a person using it," "less polished, more UGC") → treat this as new creative direction, rebuild the subject/scene and style slots of the prompt from scratch rather than patching the old prompt's wording

## A worked example

See `examples/worked-example.md` for one brand run all the way through, so the expected output shape is concrete.
