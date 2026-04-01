# Chinese Holiday Banner — Installation Guide

## Step 1: Add the section file to your theme

1. Go to your Shopify Admin → **Online Store** → **Themes**
2. Click **"..."** on your active theme → **Edit code**
3. In the left sidebar, find the **Sections** folder and click **"Add a new section"**
4. Name it `chinese-holiday-banner` and click **Create**
5. **Delete everything** in the new file
6. Copy the entire contents of `sections/chinese-holiday-banner.liquid` from this repo and paste it in
7. Click **Save**

## Step 2: Add the banner to your theme layout

1. Go back to **Online Store** → **Themes**
2. Click **Customize** on your active theme
3. In the theme editor, click **"Add section"** (in the left sidebar)
4. Search for **"Holiday Banner"** and select it
5. **Drag it to the very top** of your sections list so it appears above the header
6. Click **Save**

## Step 3: Configure your messages

With the Holiday Banner section selected in the theme editor, you'll see these settings:

### Banner mode
- **Auto** (default) — the banner switches automatically based on Chinese holiday dates
- **Force holiday warning** — always show the delay warning (useful for testing or unexpected delays)
- **Force pre-holiday urgency** — always show the pre-holiday "order now" message (useful for testing)
- **Force sales message** — always show the sales banner (ignore holidays)
- **Hidden** — turn the banner off entirely without removing it from your theme

### Sales banner
- **Sales message** — your normal promotional message
- **Background/text colors** — defaults to green with white text

### Pre-holiday banner (14 days before)
- **Pre-holiday message** — shown 14 days before each holiday starts. Great for urgency: *"Order now before delays begin!"*
- **Background/text colors** — defaults to amber/yellow with black text

### Holiday banner (during holiday)
- **Holiday message** — shown during the actual holiday period
- **Background/text colors** — defaults to orange with white text

## Holidays Covered

The banner automatically activates for these Chinese holidays:

| Holiday | Dates | Pre-warning starts |
|---------|-------|--------------------|
| Chinese New Year | Varies (Jan–Feb), 16 days | 14 days before |
| Qingming Festival | Apr 4–5 | Mar 21 |
| Labour Day | May 1–7 (extended for factory closures) | Apr 17 |
| National Day (Golden Week) | Oct 1–7 | Sep 17 |

All dates are evaluated in **China Standard Time (UTC+8)** so the banner activates based on when your suppliers are actually on holiday, regardless of where your customers are browsing from.

Chinese New Year dates are built in through 2050. No yearly updates needed.

## Testing

To verify it works:

1. Set the **Banner mode** to **"Force holiday warning"** in the theme editor
2. Check your storefront — you should see the orange delay warning
3. Switch to **"Force pre-holiday urgency"** — you should see the amber urgency banner
4. Switch to **"Force sales message"** — you should see the green sales banner
5. Try **"Hidden"** — the banner should disappear completely
6. Set it back to **"Auto"** for normal operation

## Updating Messages

You can change any banner text at any time through the theme editor — no code changes needed. Just click **Customize**, select the Holiday Banner section, edit the text, and save.
