# Worked Example: A Full Campaign, Start to Finish

A neutral example so the expected output shape is concrete. Do not reuse this copy for a real brand. It is here to show structure, not to be copied.

## The inputs the user gave

- Brand: Summit Trail Coffee, a small-batch coffee roaster
- What to advertise: the whole brand, driving to the homepage
- Ideal customer: home coffee drinkers who care about freshness and origin, tired of stale grocery-store beans
- Goal: traffic and awareness
- Destination URL (base): https://summittrailcoffee.com

## Step 1 to 2: Structure

Single ad group for a first test.

```
Ad Group Name: General - Home Page - V1
Objective: Clicks (CPC)
Budget: $500 total, Daily - about $17/day
Campaign Name: Launch Test - Clicks - 6/20/26
```

## Step 3: Version A options presented in chat (user picks one)

```
Option 1
  Headline: Coffee Roasted the Week You Order (33 chars)
  Description: Small-batch beans shipped fresh, never sitting on a shelf. Taste the difference. (79 chars)

Option 2
  Headline: Ditch the Stale Grocery Beans (29 chars)
  Description: Freshly roasted, single-origin coffee delivered days after roasting, not months. (80 chars)

Option 3
  Headline: Fresh Coffee, Roasted to Order (30 chars)
  Description: Single-origin small batches, shipped within days of roasting for peak flavor. (77 chars)

Option 4
  Headline: Better Coffee Starts With Freshness (35 chars)
  Description: Small-batch beans roasted the week you order and shipped straight to your door. (78 chars)
```

User picks Option 2.

## Step 4: Version B, the truncation-safe short version

```
Version B
  Headline: Fresh-Roasted Coffee (20 chars)
  Description: Roasted to order. Never stale. (30 chars)
```

## Step 5: Context hints (20 to 30)

```
fresh roasted coffee
single origin coffee beans
best coffee subscription
how to buy fresh coffee beans
my grocery store coffee tastes stale
where to get freshly roasted coffee
small batch coffee roaster
coffee delivered fresh
best beans for pour over
what makes coffee taste fresh
how long do coffee beans stay fresh
good coffee for home brewing
specialty coffee online
coffee that ships right after roasting
recommend a coffee roaster
best whole bean coffee
freshly roasted coffee delivery
upgrade my morning coffee
direct from roaster coffee
where do baristas buy coffee beans
```

## Step 6: Destination URLs

```
Version A: https://summittrailcoffee.com?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GeneralV-A
Version B: https://summittrailcoffee.com?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GeneralV-B
```

## Step 7: The JSON fed to the sheet builder

```json
{
  "brand": "Summit Trail Coffee",
  "phase": "Phase 1",
  "campaign": {
    "name": "Launch Test - Clicks - 6/20/26",
    "budget": "$500",
    "budget_type": "Daily - about $17/day",
    "objective": "Clicks",
    "destination_url": "https://summittrailcoffee.com"
  },
  "ad_groups": [
    {
      "name": "General - Home Page - V1",
      "destination_urls": [
        "https://summittrailcoffee.com?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GeneralV-A",
        "https://summittrailcoffee.com?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GeneralV-B"
      ],
      "versions": [
        {"label": "Version A (Long)", "headline": "Ditch the Stale Grocery Beans", "description": "Freshly roasted, single-origin coffee delivered days after roasting, not months."},
        {"label": "Version B (Short)", "headline": "Fresh-Roasted Coffee", "description": "Roasted to order. Never stale."}
      ],
      "context_hints": [
        "fresh roasted coffee",
        "single origin coffee beans",
        "best coffee subscription",
        "my grocery store coffee tastes stale",
        "where to get freshly roasted coffee",
        "small batch coffee roaster",
        "coffee delivered fresh"
      ]
    }
  ]
}
```

Run:
```bash
python scripts/build_campaign_sheet.py campaign.json "Summit Trail Coffee ChatGPT Ads Campaign Launch.xlsx"
```

Result: a three-tab workbook (Campaign, Ad Copy, Context Hints) ready to load into the platform.
