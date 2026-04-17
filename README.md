# Trackian MCP Plugin for Cursor

This plugin connects Cursor's AI to your Trackian Marketing Analytics data via the Model Context Protocol (MCP). It allows Cursor's Composer and Chat to seamlessly query your marketing performance, investigate anomalies, and generate insights directly inside your IDE.

## Requirements

To use this plugin, you must have an active Trackian account. If you don't have one yet, [register at ai.trackian.com](https://ai.trackian.com) to get started.

## Installation

1. Clone or download this plugin repository to your local machine.
2. Get your `tmcp_` API key from the Trackian Settings page.
3. In Cursor, open **Settings** > **Features** > **MCP**.
4. Click **+ Add New MCP Server**.
5. Configure the server with the following details:
   - **Name**: `trackian`
   - **Type**: `command`
   - **Command**: `node /path/to/trackian-cursor-plugin/mcp-bridge.mjs` (replace with the actual absolute path to the downloaded folder)
6. Under the new server, add an Environment Variable:
   - **Key**: `TRACKIAN_MCP_TOKEN`
   - **Value**: `YOUR_TMCP_TOKEN_HERE` (replace with your actual API key)

## Usage & Rules Included

This plugin includes custom Cursor Rules (`.cursor/rules/*.mdc`) that teach Cursor exactly how to use the Trackian tools. To use them, just ask Cursor's Composer or Chat:

*   **"Generate a Trackian channel performance report for project X from Y to Z"**: Cursor will use `runGa4Report`, `getFacebookMetrics`, `getMetricsFromGads`, and `getMetricFromGSC` to build a comprehensive executive summary.
*   **"Investigate the Trackian anomaly for project X on metric Y on date Z"**: Cursor will act as a Sentinel Investigator, following a strict 5-step diagnostic protocol to find the root cause.
*   **"Perform a deep data analysis on project X regarding Y"**: Cursor will use natural language data querying to pull raw marketing data and synthesize actionable insights.

## Tools Included

The plugin exposes the following MCP tools directly to Cursor:

*   `runGa4Report`: Pull GA4 metrics for a project and date range — traffic, sessions, conversions, revenue, and funnel events.
*   `getFacebookMetrics`: Pull Facebook Ads time-series metrics — spend, impressions, CPM, frequency, reach, and CTR.
*   `facebookCampaignStatus`: Check Facebook Ads campaign status (ACTIVE/PAUSED) along with daily budget, lifetime budget, and budget remaining.
*   `getMetricFromGSC`: Pull Google Search Console time-series metrics — clicks, impressions, average position, and CTR.
*   `inspectGscUrl`: Check the Google index status of a URL on the project's verified Search Console property.
*   `getMetricsFromGads`: Pull Google Ads time-series metrics — cost, CPC, impressions, clicks, and conversions.
*   `googleAdsQuery`: Run a custom GAQL query against Google Ads for anything the other tools don't cover — bid strategy, impression share, keyword quality, and more.
*   `googleAdsCampaignStatus`: Check Google Ads campaign status (ENABLED/PAUSED) and daily budgets.
*   `whatChanged`: Cross-platform "what changed?" dimensional analysis — identifies which campaigns, products, keywords, landing pages, ads, or cities drove a metric move.
*   `listMacroFactors`: List cross-cutting macro events (algorithm updates, platform changes) overlapping a date range, to rule them in or out as causes.
*   `getSentinelMetrics`: Get Trackian Sentinel's live-recomputed metrics and active alerts for a project on a specific date.
*   `listSentinelAlerts`: List all Sentinel alerts firing on a project across a date window.
*   `getSentinelIncidentDetails`: Drill into a specific Sentinel incident — hypotheses, evidence, and affected metrics.
*   `getGuardianHealthSummary`: Rolled-up site health for a project — uptime, page speed, and GSC URL inspection.
*   `listGuardianLogs`: Raw Guardian log entries for a project — site uptime, page speed, GSC inspections, and more.
*   `runDataQuery`: Ask a natural-language question of the project's data warehouse, or run a custom SQL query directly.
*   `whoAmI`: Show which Trackian account and company the current API key belongs to.
*   `listProjects`: List every project accessible with the current API key.
