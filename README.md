# Trackian for Cursor

Ask Cursor why sales moved, which ads waste money and what to fix next. The agent answers from your live Trackian data: GA4, Google Ads, Meta Ads, TikTok Ads, Search Console, Merchant Center, Tag Manager and your Shopify, WooCommerce or Magento store, plus the anomalies Trackian Sentinel detects every night.

You need a Trackian account. If you don't have one, the sign-in page lets you create one, or start at [trackian.com](https://trackian.com).

## What's in the plugin

- **MCP server** `trackian` at `https://api.trackian.app/mcp`. You sign in through your browser with your Trackian account (OAuth), so there's no API key to paste.
- **Skills**
  - `trackian`: how to answer marketing and sales questions from Trackian data (evidence, currencies, previews before changes).
  - `trackian-get-started`: sign in, see your projects, save how you want answers and get a first answer.
- **Commands.** Each command fetches its current steps from Trackian with `get_command`, so a workflow improves without a plugin update.

| Command | What it does |
| --- | --- |
| `/trackian-setup` (alias `/trackian-start`) | Sign in, see projects and platforms, choose how answers are written |
| `/trackian-investigate` | Find what changed in a project and why |
| `/trackian-deep-dive` | Explain one known incident end to end |
| `/trackian-weekly-review` | The week in one summary |
| `/trackian-briefing` | What happened across all projects |
| `/trackian-opportunities` | Where to grow |
| `/trackian-pacing` | Are this month's targets on track |
| `/trackian-ads-audit` | Paid-media health check across ad platforms: cut, fix, scale |
| `/trackian-creative-fatigue` | Facebook and Instagram ads that are wearing out |
| `/trackian-creative-review` | What each ad shows and says, and what drives results |
| `/trackian-search-terms` | Google Ads searches wasting money, and negatives to add |
| `/trackian-blended` | What all the advertising together made |
| `/trackian-product-waste` | Products wasting Shopping and Performance Max spend |
| `/trackian-keyword-health` | Dead keywords, lost impression share, duplicates |
| `/trackian-funnel-dropoff` | Where the Meta funnel leaks, per ad set |
| `/trackian-attribution-gap` | What the platforms claim vs what analytics saw |
| `/trackian-landing-pages` | Paid landing pages that convert badly or aren't tracked |
| `/trackian-geo-waste` | Countries and regions that spend without results |
| `/trackian-recommendations` | Google's and Meta's own recommendations, filtered |
| `/trackian-merchant` | Review and fix a Google Merchant Center feed |
| `/trackian-gtm` | Change a Google Tag Manager setup from a plain-words request |
| `/trackian-profit-metrics` | Gross profit, margin and profit on ad spend from product costs |
| `/trackian-set-targets` | Set the monthly KPI targets |
| `/trackian-setup-project` | Improve a project's alerts, KPIs, custom metrics and funnels |
| `/trackian-dashboard` | Build or edit a custom Trackian dashboard |
| `/trackian-report` | A branded report saved as HTML |

- **Agent** `marketing-analyst`: for multi-step analysis when the main chat only needs the conclusion. It reads and never changes anything.

## Install

1. Install **Trackian** from the Cursor marketplace.
2. In Cursor, open **Customize** > **MCPs**, find **trackian** and click **Authenticate**. Your browser opens a Trackian page; sign in or create an account, and you're sent back to Cursor.
3. In chat, run `/trackian-setup`, or just ask "why did sales dip last Tuesday?".

To try a local copy, clone this repository into `~/.cursor/plugins/local/trackian` and run **Developer: Reload Window**.

## Changes need your yes

Most changes are two-step. The first call returns a preview and changes nothing. The agent shows you the before and after, and applies the change only after you confirm. The few tools that apply in one call say so in their description, and the agent asks you first. Changes to live ad campaigns, and to WooCommerce or Magento products and orders, are off for a new connection until an account owner turns them on in Trackian under Settings > AI Agent Setup.

## Where the plugin keeps files

- `~/.trackian/profile.md` holds your answer preferences (language, detail level, projects to watch). `/trackian-setup` writes it.
- `trackian-reports/` in your workspace holds the reports you generate.

## Support

- Help: [help.trackian.com](https://help.trackian.com) or support@trackian.com
- [Privacy policy](https://trackian.com/privacy-center/privacy-policy/) and [terms](https://trackian.com/privacy-center/terms-and-conditions/)

## License

MIT
