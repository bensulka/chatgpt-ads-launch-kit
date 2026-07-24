# Worked Example: A Full Campaign, Start to Finish

A neutral example so the expected output shape is concrete. Do not reuse this copy for a real brand. It is here to show structure, not to be copied.

## The inputs given

- Brand: Northbound Supply Co, a DTC brand selling camping and hiking gear
- What to advertise: the Ridgeline 45L hiking backpack, $189
- Ideal customer: weekend hikers and backpackers, ages 25 to 45, active outdoor lifestyle, has bought gear from REI or Patagonia before
- Goal: drive purchases on the Ridgeline 45L product page
- Destination URL (base): https://northboundsupply.com/ridgeline-45l
- Creative direction: outdoor lifestyle and product photography, earthy tones, no cartoon or illustration style

## Step 1 to 2: Structure

Single ad group for a first test.

```
Campaign: RidgelineBackpackViews071626 | Budget: $30/day, Daily | Launch 7/16, no end date
Objective: Views | Countries: US
Ad Group Name: RidgelineBackpackBid12V1 | Max bid: $12 CPM
```

Naming convention shown here: Product/Category + Objective + Date (`MMDDYY`) for the campaign, Product/Category + Bid + Creative Version for the ad group, each segment capitalized and run together since punctuation isn't allowed. Adjust the segments to whatever naming convention is actually wanted, this is just one way to do it.

Budget is $30/day, not a round test number like $10 or $17. ChatGPT Ads enforces a confirmed $25/day minimum on Daily budgets (`CampaignDailyBudgetMinimumValidationError` if under that), so anything below $25 will fail at upload.

## Step 3: Title/copy options presented in chat (user picks)

```
Option 1
  Title: Ridgeline 45L Pack (18 chars)
  Copy: Weatherproof pack built for 3 day trips. (40 chars)

Option 2
  Title: Built for the Trail (19 chars)
  Copy: Recycled nylon. Lifetime warranty. $189. (40 chars)

Option 3
  Title: Hike Farther, Carry Less (24 chars)
  Copy: Free shipping over $75. Ships in 2 days. (40 chars)

Option 4
  Title: Northbound Ridgeline (20 chars)
  Copy: Weatherproof. Lifetime warranty. $189. (38 chars)
```

User picks Options 1 and 3, running them as two separate ads in the same ad group.

## Step 4: Destination URLs

```
Ad 1: https://northboundsupply.com/ridgeline-45l?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GenA
Ad 2: https://northboundsupply.com/ridgeline-45l?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GenB
```

## Step 5: Context hints (20 to 30)

```
hiking backpack
weatherproof hiking backpack
best backpack for a 3 day hike
backpack with lifetime warranty
recycled nylon backpack
hiking gear for weekend trips
best daypack for backpacking
durable hiking backpack
REI alternative backpack
Patagonia alternative backpack
eco friendly hiking gear
hiking backpack under $200
best backpack for weekend hikers
hiking pack with rain cover
hiking backpack for beginners
what to look for in a hiking backpack
```

## Step 6: Generate and host the creative

Reference image prompt (generate this one first, so both ad creatives stay visually consistent):

```
Create a photorealistic product photo of a hiking backpack called the Ridgeline 45L.

Product details: a 45 liter internal-frame hiking backpack, moss green body with rust
orange accent straps and zipper pulls, recycled ripstop nylon fabric with a visible
subtle woven texture, adjustable shoulder straps and a padded hip belt, a top lid
pocket, side compression straps, and a front bungee mesh pocket.

Framing: full backpack in frame, front three-quarter angle, standing upright as if on
an invisible mannequin or stand, no person wearing it.

Background: plain seamless studio backdrop, light gray, no props, no text, no logos,
no badges.

Lighting: soft, even studio lighting, minimal shadow, true-to-life color.

Style: high-detail commercial product photography, sharp focus on fabric texture and
hardware, no illustration or 3D-render look.

Square (1:1) composition.
```

Ad 1 creative prompt:

```
Create a square (1:1) product ad image for Northbound Supply Co, a DTC brand selling
the Ridgeline 45L hiking backpack, priced at $189. Match the backpack's color, texture,
and hardware to the attached reference image.

Scene: the backpack sitting on a rocky mountain trail at golden hour, weatherproof
recycled ripstop nylon texture visible, no people in frame.

Include a small badge or corner callout with the text "Free shipping over $75."

Style: clean outdoor product photography, natural light, no stock photo feel, no
cartoon or illustration style, earthy outdoorsy colors (moss green, rust orange,
warm gray).

Keep the composition simple enough to work as a paid ad creative, plenty of negative
space in one corner for a headline overlay.
```

Both images get hosted somewhere with a public link (Google Drive with sharing turned on, Imgur, Dropbox, a site's own media library), giving two `image_link` URLs.

## Step 7: The JSON fed to the sheet builder

```json
{
  "campaign": {
    "campaign_name": "RidgelineBackpackViews071626",
    "budget_max": 30,
    "budget_type": "Daily",
    "launch_date": "2026-07-16",
    "end_date": "",
    "objective": "Views",
    "target_countries": ["US"]
  },
  "adgroups": [
    {
      "adgroup_name": "RidgelineBackpackBid12V1",
      "max_bid": 12,
      "context_hints": [
        "hiking backpack",
        "weatherproof hiking backpack",
        "best backpack for a 3 day hike",
        "backpack with lifetime warranty",
        "recycled nylon backpack",
        "REI alternative backpack"
      ],
      "ads": [
        {
          "title": "Ridgeline 45L Pack",
          "copy": "Weatherproof pack built for 3 day trips.",
          "link": "https://northboundsupply.com/ridgeline-45l?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GenA",
          "image_link": "https://drive.google.com/uc?export=view&id=EXAMPLE_FILE_ID_1"
        },
        {
          "title": "Hike Farther, Carry Less",
          "copy": "Free shipping over $75. Ships in 2 days.",
          "link": "https://northboundsupply.com/ridgeline-45l?utm_source=openai&utm_medium=cpc&utm_campaign=ChatGPTAdsTest&utm_content=GenB",
          "image_link": "https://drive.google.com/uc?export=view&id=EXAMPLE_FILE_ID_2"
        }
      ]
    }
  ]
}
```

Run:
```bash
python scripts/build_bulk_upload_sheet.py campaign.json "Northbound Supply Co ChatGPT Ads Bulk Upload.xlsx"
```

Result: a three-tab workbook (`campaigns`, `adgroups`, `ads`) matching ChatGPT Ads' own bulk upload template exactly, ready to drag into the platform's bulk upload tool.
