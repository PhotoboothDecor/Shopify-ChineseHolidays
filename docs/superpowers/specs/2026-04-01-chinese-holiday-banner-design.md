# Chinese Holiday Banner — Design Spec

## Problem

Drop-shippers with Chinese suppliers face fulfillment delays during Chinese holidays. Customers are unaware and expect normal shipping times. This leads to complaints and chargebacks.

## Solution

A Shopify theme **section** that displays a top-of-page announcement banner. Under normal conditions it shows a configurable sales message. During Chinese holidays (and a 14-day pre-warning window), it automatically switches to a delay warning.

## Approach

Hardcoded dates in a single Liquid + JavaScript section file. No external dependencies, no yearly config files.

## Holidays Covered

| Holiday | Dates | Type |
|---------|-------|------|
| Chinese New Year | Varies (Jan/Feb) — lookup table 2024–2050 | 16-day duration, lunar calendar |
| Qingming Festival | Apr 4–5 | Fixed |
| Labour Day Golden Week | May 1–5 | Fixed |
| National Day Golden Week | Oct 1–7 | Fixed |

## Banner States

The banner has three display states:

1. **Sales mode** — normal promotional message (default outside holiday windows)
2. **Pre-holiday mode** — urgency message shown 14 days before a holiday starts ("Order now before delays begin!")
3. **Holiday mode** — delay warning shown during the actual holiday ("Orders placed now may experience 1–3 week delays")

## Override Modes (Theme Editor)

- **Auto** (default) — follows the holiday calendar automatically
- **Force holiday warning** — always shows the holiday/delay banner
- **Force sales message** — always shows the sales banner

## Theme Editor Settings

| Setting | Type | Default |
|---------|------|---------|
| Override mode | Select (auto / force-holiday / force-sales) | auto |
| Sales message | Text | "Free shipping on orders over $50!" |
| Pre-holiday message | Text | "Our suppliers are going on holiday soon — order now to avoid shipping delays!" |
| Holiday message | Text | "Orders placed during this period may experience delays of 1–3 weeks due to a supplier holiday." |
| Sales banner background | Color | #2E7D32 (green) |
| Sales banner text | Color | #FFFFFF |
| Holiday banner background | Color | #E65100 (orange) |
| Holiday banner text | Color | #FFFFFF |

## Architecture

Single file: `sections/chinese-holiday-banner.liquid`

- **Liquid layer** — reads Theme Editor settings, passes them as `data-` attributes to the banner `<div>`
- **CSS** — inline styles for the banner, responsive, sits above the header
- **JavaScript** — runs on page load, checks today's date against holiday windows, applies the correct message and colors

## Holiday Date Logic (JavaScript)

- Chinese New Year: lookup table keyed by year (2024–2050), 16-day holiday duration
- Fixed holidays: month/day ranges, same every year
- Pre-warning: 14 days before each holiday start date
- Post-holiday: banner turns off immediately when holiday ends (no buffer)

## Installation

User copies the section file into their theme's `sections/` directory via the Shopify code editor, then adds the section to their theme layout via the Theme Editor.
