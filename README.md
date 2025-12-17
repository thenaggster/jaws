# 🦈 J.A.W.S. (Jira Automated Warning System)

> **"Just when you thought it was safe to ignore your Jira tickets..."**

**J.A.W.S.** is an AI-powered agent designed for Technical Program Managers who need to keep their backlogs clean and their stakeholders accountable. It acts as an apex predator in your project management ecosystem, hunting down "Overdue" and "Fishy" issues and surfacing them directly to owners via Slack.

-----

## 🌊 What does it do?

J.A.W.S. patrols your Jira project and performs a "Swim" (execution run) to identify two types of prey:

1.  **🔴 The Overdue:** Issues where the `Target End Date` has passed.
2.  **🐟 The Fishy:** Stale issues where the `Color Status` or `Status Summary` hasn't been updated in over 3 weeks.

Once prey is identified, J.A.W.S.:

1.  **Fetches** deep context from Jira (Managers, Developers, Dates).
2.  **Resolves** the Manager's email to their specific Slack User ID.
3.  **Generates** a polite but firm direct message (using Gen AI templating).
4.  **Delivers** the notification to prompt immediate action.

-----

## ⚙️ Configuration & Filters

J.A.W.S. relies on specific JQL filters to hunt.

### 1\. Overdue Filter

  * **Logic:** Finds items past their deadline.
  * **Default JQL:** `filter=pgmChk_Overdue`

### 2\. Fishy Filter

  * **Logic:** Finds items that smell stale (no updates in 3 weeks).
  * **Default JQL:** `filter=pgmChk_FishyStatus`

-----

## 🛠️ Setup

### Prerequisites

  * Cursor
  * Atlassian MCP Server
  * Jira API Token
  * Slack MCP Server
  * Slack Bot Token (with `users:read` and `chat:write` scopes)

-----

## 📨 The Notifications

J.A.W.S. doesn't just dump data; it sends structured, actionable requests.

### Template: Overdue 🔴

> **Subject:** Immediate Action Required
> "Hello `Manager`\! While doing the program check, I noticed `Key` is overdue. Its target end was `Target End Date`. Could you close it or set a new date?"

### Template: Fishy 🐟

> **Subject:** Stale Data Detected
> "Hello `Manager`\! This issue smells fishy. `Key` hasn't had its **Color Status** or **Status Summary** updated in 3 weeks. Please update the fields."

-----

## 🚀 Usage

To start a feeding frenzy (run the agent):

```bash
# Run the agent interactively
Copy and past the prompt into cursor
Run the agent

# Expected Output:
# > 🦈 J.A.W.S. is circling...
# > Found 5 Overdue issues.
# > Found 2 Fishy issues.
# > Sending Slack DMs... 
# > Done.
```

-----

## 🧩 Contribution

Feel free to open a PR if you want to teach J.A.W.S. new hunting techniques (new JQL filters) or improve the digestion logic (message templates).

-----

*Maintained by @ricardofgarcia (TPM). Keeping the waters clear since (a long time ago...).* 🦈
