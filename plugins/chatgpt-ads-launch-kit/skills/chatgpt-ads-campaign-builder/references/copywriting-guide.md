# ChatGPT Ads Copywriting Guide

This reference holds the copy specs, voice approach, and prompt structure for writing ChatGPT Ads copy and context hints, matching how the Sulka Labs ChatGPT Ads system runs the platform.

## Character Specs

| | Version A (Full) | Version B (Short, truncation-safe) |
|---|---|---|
| **Headline** | up to 50 chars, title case | up to 25 chars, title case |
| **Description** | up to 100 chars, sentence case | up to 50 chars, sentence case |

These are the platform's hard caps. Aim a little under (Version A headlines around 30 to 45 chars, descriptions around 80 to 100) so ads rarely truncate across placements. Always print the character count in parentheses after each field, for example `Headline: Get the Right Part Fast (24 chars)`.

Why two versions: ChatGPT serves ads in small placements where long copy can get cut off. Version A carries the full message. Version B is the safe fallback that still lands when space is tight. Version B should be the same idea as the approved Version A, not a different angle.

## Voice

ChatGPT Ads show up inside a conversation where the user is already in a problem-solving mindset. Copy that reads like a genuinely helpful answer outperforms hard-sell ad-speak.

- Conversational and natural, not corporate.
- Lead with the benefit or the problem you solve, not the brand name.
- Be concrete. Specifics and trust signals do the heavy lifting.
- Match the brand's own voice. If the user shared brand guidelines or approved copy, draw from that language. Do not invent brand claims that have not been approved.
- No em dashes. Use periods or commas.

### Choosing the angle
Lead with whatever best matches the buyer's intent for this brand and audience. Common angles:
- The problem the product solves
- What makes the brand different or first-of-its-kind
- Selection or quality
- Price or value
- Speed or convenience

For pure awareness brands (especially retail brands with no e-commerce checkout, like a CPG product driving people to stores), the angle is usually the product's distinctive hook and the benefit, not a "buy now" push.

## Copywriting Prompt Structure

Use this thinking when drafting.

Inputs to ground every draft:
- Brand or service: what they sell or do
- Target audience: who they are targeting
- Offer or angle: what makes them different or what problem they solve

Before writing, be clear on:
1. The goal of this ad group
2. The key message or hook to lead with for this audience
3. The action you want the user to take

Then produce:
- **Version A (Full):** Headline up to 50 chars (title case), Description up to 100 chars (sentence case)
- **Version B (Short):** Headline up to 25 chars (title case), Description up to 50 chars (sentence case)

On the first pass, give 4 to 5 Version A options so the user can pick a direction at a glance. Write Version B only after Version A is chosen.

## Context Hints Prompt Structure

Context hints describe the conversations, topics, or keywords where the ad is most relevant. They guide matching but are not exact-match rules. Write them as short, natural phrases someone might actually be discussing when the product would be a relevant solution.

Aim for 20 to 30 per ad group, blending:
- **Category or product terms** (what the thing is: "frozen fruit snack", "weather seal")
- **Problem or need statements** (the pain or desire: "I want a healthier dessert")
- **Shopping or comparison queries** (active consideration: "best healthy snack brands")
- **Conversational or long-tail** (how people actually talk to ChatGPT: "what's a good frozen treat that isn't full of sugar")

Keep them tightly relevant to the brand and offer. Generic hints that match unrelated conversations waste budget. They tend to skew a bit more long-tail and conversational than Google keywords, but a two or three word phrase is fine too.

## Worked Example (reference only)

This shows the established format so the structure is concrete. Do not reuse this copy for other brands.

```
Ad Group Name: General - Home Page - V1

Version A
  Headline: Snacks That Actually Taste Good (30 chars)
  Description: Real fruit, frozen crisp, no junk. A sweet snack you can feel good about. (72 chars)

Version B
  Headline: Better Frozen Snacks (20 chars)
  Description: Real fruit. No junk. Actually good. (35 chars)

Context Hints (sample):
frozen fruit snack
healthy dessert ideas
I want a sweet snack that isn't junk
best healthy snacks for kids
what's a good frozen treat that's actually good for you
```
