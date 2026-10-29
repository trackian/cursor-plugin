---
name: trackian-get-started
description: Get Trackian working in Cursor and reach a first real answer - sign in to Trackian, check which projects and platforms are connected, save how the owner wants answers, and run a first report. Use when the user has just installed the Trackian plugin, says "set up Trackian", "get started", "connect my account", or when Trackian tools are missing or fail with a sign-in error.
---

# Get started with Trackian

Get the user from a fresh install to a first real answer in as few steps as possible. Ask one thing at a time and keep every message short.

## 1. Check the sign-in

- Call `get_connected_account`. If it answers, say in one line which company they are signed in as and go to step 2.
- If the Trackian tools are not available, or the call fails with an authentication error, the plugin is not signed in yet. Tell the user, in these words or close to them:
  1. In Cursor, open **Customize** > **MCPs**.
  2. Find **trackian** (marked Plugin, "Needs authentication") and click **Authenticate**.
  3. A Trackian page opens in the browser. Sign in, or create an account there if you do not have one yet. The page sends you back to Cursor.
  4. Come back here and say "done".
  Retry `get_connected_account` after they confirm.
- If they already signed in and the tools are still missing, ask what Customize > MCPs shows for trackian. A sign-in prompt means sign in again. An error after signing in means Trackian refused the connection - most often a lapsed subscription - and signing in again will not help: send them to renew in the Trackian app or to support@trackian.com, and do not loop on sign-in.
- If the Trackian server is not listed at all, the plugin is not loaded: ask them to check that the Trackian plugin is installed and enabled, then reload the Cursor window.
- Never ask for an API key, token or password in the chat. The sign-in page handles it.

## 2. See what is there

- Call `list_projects`. Show the projects by name (with the website when it helps), never by internal id.
- If there are no projects, or a project has no platforms connected, send them to the Trackian app at https://trackian.app to add the project and connect Google Analytics, Google Ads, Meta Ads, TikTok Ads, Search Console, their store and the rest under Setup > Platforms. Trackian needs a few hours after a first connection to pull history; say so plainly.
- For one project, `get_project_setup_status` tells you what is still unconfigured (alerts, KPIs, daily summary). Mention the gaps in one line and offer `/trackian-setup-project` for later.

## 3. Save how they want answers

Run the Trackian first-run steps: call `get_command` with `name: "start"` and follow the returned `reference` (language, account type, detail level, projects to watch). Save the profile to `~/.trackian/profile.md` - that is where this plugin keeps it, in place of the `custom/profile.md` the reference names. Every Trackian command in this plugin reads it from there. The file sits in the user's home folder, outside the workspace, so Cursor may ask the user to allow the write; say so before you write, and if they decline, use their answers for this session only. The reference's capability tour uses bare names such as `/investigate`; in this plugin they are `/trackian-investigate`, `/trackian-weekly-review`, and so on.

If they want to skip the questions, skip them - the profile is optional and `/trackian-setup` can run again any time.

## 4. First answer

Offer one concrete first look for what is connected, and run it on a yes:

- Several projects: what happened across them yesterday (`/trackian-briefing`).
- One project with ads: a paid-media health check (`/trackian-ads-audit`) or the week in one summary (`/trackian-weekly-review`).
- A specific worry ("sales dipped on Tuesday"): find what changed and why (`/trackian-investigate`).

## Troubleshooting

- **Sign-in page says the link expired:** start the sign-in again from Customize > MCPs > trackian > Authenticate; the link is single-use.
- **The browser sign-in finishes, but Cursor still shows the server as not signed in:** the company's Trackian plan may not include AI agent access. Signing in again will not change that; send them to support@trackian.com or their plan settings in Trackian. Do not loop on re-authentication.
- **Signed in before, but the tools are missing and the server shows an error:** the Trackian subscription has most likely lapsed, so the server refuses the connection. Signing in again will not help; they renew in the Trackian app, then reload the Cursor window.
- **Signed in, but a change is refused:** this connection does not have permission to make that change. Changes to live ad campaigns and to WooCommerce or Magento products and orders are off for a new connection; an account owner can turn them on in Trackian under Settings > AI Agent Setup. Search Console changes and Shopify edits are not available yet.
- **Signed in to the wrong company:** switch to the right company in the Trackian app, then sign out of trackian under Customize > MCPs and authenticate again.
- **A platform shows no data:** reconnect it in the Trackian app under Setup > Platforms.
- **Anything else:** support@trackian.com.

## Hand-offs

- Any question about performance -> follow the `trackian` skill.
- Improving a project's alerts, KPIs and funnels -> `/trackian-setup-project`.
- Monthly targets -> `/trackian-set-targets`.
