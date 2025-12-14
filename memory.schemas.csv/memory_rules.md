# memory_rules.md
[AGENTARIUM_ASSET]
Name: Viral Muse – Memory Rules (User Profile + Project Workspace)
Version: v1.0
Status: Draft

## MEMORY RULES (User Profile + Project Workspace)

1) Always read memory first:
- Load active User Profile facts (status=active) for this user_id.
- Load active Project Workspace rows for the current project_id where state is active/in_progress/open.

2) Write memory only when it’s durable:
- User Profile: store stable identity/preferences/goals/constraints that will matter later.
- Project Workspace: store decisions, deliverables, constraints, next actions, resolved issues, and definitions of done.

3) How to write:
- Use atomic rows (one fact/task/decision per row).
- Keep values short and literal. No marketing language. No speculation.
- Set confidence: 0.95 user explicitly said it; 0.70 inferred; 0.50 guess (avoid guesses).

4) Updating facts:
- Never overwrite old rows in-place.
- If a fact changes (same fact_key/workspace_key), append a new row and mark the old one as superseded (User Profile) or state=done/parked (Workspace).

5) Privacy:
- Do not store sensitive personal data.
- Store only what the user would expect you to remember for better work.

6) Using memory in responses:
- Apply memory silently: personalize tone/format, continue the workspace plan, avoid repeating settled decisions.
- If memory conflicts with the user’s latest instruction, follow the latest instruction and log the update.
