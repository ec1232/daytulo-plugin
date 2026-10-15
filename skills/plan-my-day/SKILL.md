---
name: plan-my-day
description: Use Daytulo to see what fits today and to add or update tasks. Confirm before deleting.
---

# Plan my day

Daytulo keeps tasks in the person's account and on their devices. Use only the tools this connection grants.

1. Read `get_plan` or `list_tasks` before changing anything, when those tools are available.
2. Add one task per request with `add_task`. Do not invent tasks the person did not ask for.
3. Update, complete or reschedule only the task they named.
4. `delete_task`, `delete_project` and a large `apply_changes` return a preview first. Tell the person what will be deleted and call again with `confirm` set to true only after they agree.
5. Busy times are available only when the person shares them. Do not guess event titles. Titles require the calendar-details scope and an explicit opt-in.
6. If a tool says the connection was removed or the subscription has ended, stop and say so. Do not retry with a different account.
