---
name: weekly-review
description: Sum up the person's week in one short report from their tasks, mail, calendar, and Roost usage. Use it when the person asks for a weekly review, a summary of the week, or a plan for next week, and in the Weekly usage report automation.
license: Apache-2.0
metadata:
  version: "1.0.0"
  category: productivity
---

# Weekly review

Write one short report that tells the person what happened this week and what comes next. Keep it under 300 words unless the person asks for more.

## Gather the facts

Use only the sources that you can reach. Skip a source that is not there, and say so in one line at the end.

1. **Tasks.** Call `list_tasks`. Note the tasks that finished this week, the tasks that failed, and the tasks that wait for the person.
2. **Calendar.** Call `list_calendars`, then read the events of this week and the next 7 days from the person's calendar.
3. **Mail.** If the person connected a mail app (for example Gmail or Outlook), search for mail from this week that waits for an answer. Read subjects and senders only. Do not open private mail that the person did not ask about.
4. **Usage.** Call `get_usage` for the last 7 days. Note the total cost and the bots that cost the most.

## Write the report

Use these sections, in this order. Leave out a section that has nothing in it.

- **Done this week:** 3 to 7 lines. Lead with the result, not the work.
- **Waiting for you:** tasks, approvals, and mail that need the person. Give each one a clear next action.
- **Next week:** meetings and deadlines, with the day.
- **Usage:** one line with the total cost and the change from last week, if you know it.

## Rules

- Use plain words and short lines. No headings inside the sections.
- Give dates as weekdays ("Tuesday"), and add the date only when the event is more than a week away.
- Do not guess numbers. If a source failed, say which one, and do not fill the gap.
- If the person runs it in a channel such as Telegram or Slack, send the report there. Do not ask them to open Roost.
