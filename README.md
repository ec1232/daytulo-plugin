# Daytulo for Cursor and Grok Bot

Daytulo plans your tasks around the time you actually have. This plugin connects Cursor, and Grok Bot, to your Daytulo account so an assistant can add a task, read what is open, update or complete it, and look at your plan and free time.

- MCP server: `https://mcp.daytulo.com/mcp` (remote, streamable HTTP)
- Requires: a Daytulo account (iOS app) with an active plan or trial

## Connect

1. Install the plugin and choose **Authenticate**. No API key or variable is needed.
2. In the Daytulo app open **Rhythm → Connected assistants**, accept the disclosure and tap **Get a connection code**.
3. Enter the eight-digit code on the Daytulo page that opens in your browser and press **Allow**.

Auth is OAuth 2.1 with PKCE (S256), dynamic client registration or client ID metadata documents. Scopes: `tasks:add`, `tasks:read`, `tasks:write`, `plan:read`, `calendar:freebusy` (and optional `calendar:details`). The grant limits what the assistant can do: a read-only grant cannot add or delete tasks. Remove a connection any time in the app.

## Tools

Read: `get_profile`, `list_tasks`, `get_task`, `list_projects`, `get_plan`, `get_availability`, `suggest_slots`
Write: `add_task`, `update_task`, `complete_task`, `reschedule_task`, `restore_task`, `create_project`, `update_project`
Destructive (preview first, then `confirm: true`): `delete_task`, `delete_project`, `apply_changes`

Tools that change or overwrite existing data (`update_task`, `complete_task`, `reschedule_task`, `restore_task`, `update_project`, and the destructive ones above) are annotated `destructiveHint: true`; `add_task` and `create_project` are additive (`destructiveHint: false`).

Deleting moves items to Recently deleted for 30 days. Busy times are shared only if you turn it on; event titles are a separate opt-in. No tool sends data to other services.

## Prompts

Two ready-made prompts appear in clients that support MCP prompts (for connections that can read tasks or the plan):

- `tidy-up` ("Tidy up my Daytulo"): reviews your plan and open tasks, flags overdue deadlines, missing estimates, duplicates and WAITING items with no follow-up date, proposes changes and waits for your OK before changing anything. Afterwards it adds anything you mention as a task with an estimate and a deadline if there is one.
- `daily-check` ("Check my day"): reads today's plan, says what is at risk and what to do first, and changes nothing.

The server also sends the assistant a short brief on first connect: read `get_plan` and `list_tasks` first, ask before changing anything, give new tasks a time estimate, add one task per call, never invent tasks.

## Links

- Privacy: https://daytulo.com/legal/privacy
- Terms: https://daytulo.com/legal/terms
- Support: https://daytulo.com/support (contact@daytulo.com)
- Setup guide: https://daytulo.com/docs/assistants

Team admins: allow the MCP host `mcp.daytulo.com`.
