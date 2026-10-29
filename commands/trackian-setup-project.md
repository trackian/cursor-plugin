---
name: trackian-setup-project
description: Review and improve a project's Trackian setup - alerts, KPIs, custom metrics, and funnels. Every change previews first and needs your OK.
---
This command's steps live in Trackian and are always up to date. Call `get_command` with `name: "setup-project"` (pass `projectRef` in `args` if the user named a project). The returned `reference` describes how Trackian approaches this workflow and which tools supply each piece of evidence; use it to carry out the request.

Before you start: if `~/.trackian/profile.md` exists, read it and follow it, and answer the way the `trackian` skill sets out. The reference is shared with Trackian's downloadable agent folder, so read its paths the plugin way: `custom/profile.md` is `~/.trackian/profile.md`, `reports/` is a `trackian-reports/` folder in the current workspace, and a command named `/<name>` is `/trackian-<name>`.

If the Trackian tools are not available, or `get_command` fails with a sign-in error, do not improvise: the plugin is not signed in yet. Follow the `trackian-get-started` skill (sign in to the Trackian MCP server: Customize > MCPs > trackian > Authenticate), then retry.
