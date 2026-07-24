# ChatGPT Ads Copywriting Guide

This reference holds the copy specs, voice approach, and prompt structure for writing ChatGPT Ads copy and context hints, checked directly against the platform's real bulk upload template.

## Character Specs

| Field | Recommended | Hard max |
|---|---|---|
| **Title** | 16-24 characters, title case | 50 |
| **Copy** | 32-48 characters, sentence case | 100 |

The recommended range is what reads best in-line with a chat response, confirmed against ChatGPT Ads' own bulk upload schema checklist. Going past it isn't a rejected file, just a weaker ad, so write to the recommended range by default. Always print the character count in parentheses after each field, e.g. `Title: Get the Right Part Fast (24 chars)`.

Some ad platforms use a long and short version of the same line (a full headline plus a truncation-safe backup). ChatGPT Ads doesn't work that way, there's only one length. Write straight to the recommended range instead of drafting long and cutting down.

**Multiple ads in the same ad group should be different angles, not different lengths.** There's no "safe fallback" format on this platform, so a second ad in an ad group exists to test a different hook, not to be a shorter backup of the first.

## Voice

ChatGPT Ads show up inside a conversation where the user is already in a problem-solving mindset. Copy that reads like a genuinely helpful answer outperforms hard-sell ad-speak.

**Write as a senior direct-response copywriter, not a brand marketer.** Assume the reader is skeptical and has already scrolled past a hundred ads today. Every claim needs a receipt, a number, a name, a comparison, a guarantee, not a bare adjective. "Weatherproof" is a claim. "Keeps gear dry through a 4-hour downpour" is a receipt. If the only available detail really is generic, say so in your own reasoning rather than dressing it up, then lean harder on a different angle that does have a real detail behind it.

- Conversational and natural, not corporate.
- Lead with the benefit or the problem you solve, not the brand name.
- Be concrete. Specifics and trust signals do the heavy lifting, and at this length there's no room for a wasted word.
- Match the brand's own voice. If brand guidelines or approved copy exist, draw from that language. Don't invent claims that haven't been confirmed.
- Skip em dashes. Use periods or commas, they read more natural in this short a space anyway.

### Sourcing the ammunition (do this before drafting a single line)

Generic copy happens when a model starts writing before it has anything specific to say. Before drafting, pull out, in one line each:

1. **The sharpest proof point available** — a number, material, test, or guarantee. Not "durable," but what makes it durable (stitching count, fabric name, a stated test condition).
2. **The #1 objection a buyer has** — price, durability doubt, "is this actually different," shipping time, whatever it is for this category.
3. **What the best alternative gets wrong** — the gap this product fills that a named or implied competitor doesn't. If the user hasn't given competitor detail, use the category's default option (e.g. "the mall backpack," "the big-box version") as the foil.
4. **One weirdly specific, non-generic detail** — something oddly precise enough that no competitor could casually claim it. Pulled from real customer language (reviews, testimonials, site copy) if the brand is real and that's available; reasoned from the actual inputs given if it's a demo or fictional brand.

If research tools are available and the brand is real, use them to pull actual review language, testimonials, or competitor positioning before this step, real customer phrasing beats invented phrasing every time. If not, still do this step from whatever inputs were given, don't skip it because there's no live research access.

### Choosing the angle

Lead with whatever best matches the buyer's intent for this brand and audience. Common angles:
- The problem the product solves
- What makes the brand different / first-of-its-kind
- Selection or quality
- Price or value
- Speed or convenience
- Proof / specificity (a hard number or guarantee stands in for the whole pitch)
- Objection-handling (name the hesitation and answer it directly)

For pure awareness brands (especially retail brands with no e-commerce checkout, like a CPG product driving people to stores), the angle is usually the product's distinctive hook and the benefit, not a "buy now" push.

**Every option in a set must come from a different angle bucket.** If two of the five combos are both restating price/warranty in different word order, that's one angle twice, not two angles. Cut the weaker one and write a real replacement from an angle bucket nothing else is using yet.

## Copywriting Prompt Structure

Use this thinking when drafting, tightened to fit the real character caps.

Inputs to ground every draft:
- Brand / service: what they sell or do
- Target audience: who they're targeting
- Offer / angle: what makes them different or what problem they solve

Before writing, be clear on:
1. The goal of this ad group
2. The key message or hook to lead with for this audience
3. The action the reader should take

Then, after running the ammunition step above, produce, per ad:
- **Title:** 16-24 characters recommended, title case
- **Copy:** 32-48 characters recommended, sentence case

On the first pass, give 4 to 5 title/copy combos, each from a different angle bucket, so a real direction can be picked at a glance, not five versions of the same idea. If two angles need testing in the same ad group, treat each as its own full ad, not a long/short pair of the same idea.

## Context Hints Prompt Structure

Context hints describe the conversations, topics, or keywords where the ad is most relevant. They guide matching but are not exact-match rules. Write them as short, natural phrases someone might actually be discussing when the product would be a relevant solution.

Aim for 20 to 30 per ad group, blending:
- **Category / product terms** — what the thing is ("frozen fruit snack", "weather seal")
- **Problem / need statements** — the pain or desire ("I want a healthier dessert")
- **Shopping / comparison queries** — active consideration ("best healthy snack brands")
- **Conversational / long-tail** — how people actually talk to ChatGPT ("what's a good frozen treat that isn't full of sugar")

Keep them tightly relevant to the brand and offer. Generic hints that match unrelated conversations waste budget. They tend to skew a bit more long-tail and conversational than Google keywords, but a two or three word phrase is fine too.

## Worked Example

This is the established format, shown so the structure is concrete.

```
Ad Group Name: RidgelineBackpackBid12V1

Ad 1
  Title: Hike Farther, Carry Less (24 chars)
  Copy: Free shipping over $75. Ships in 2 days. (40 chars)

Ad 2
  Title: The Last Pack You'll Buy (24 chars)
  Copy: Lifetime warranty. 45L capacity. $189. (38 chars)

Context Hints (sample):
hiking backpack
weatherproof hiking backpack
best backpack for a 3 day hike
backpack with lifetime warranty
recycled nylon backpack
REI alternative backpack
```
