# Live Setup: Use and Deploy the Salesforce Manual QA Skill

This skill does not deploy a web app. It is deployed by installing it into Codex's skill directory and then invoking it in a Codex session.

## 1) Install into Codex skills directory

From the repository root:

```bash
mkdir -p ~/.codex/skills
cp -R salesforce-manual-qa ~/.codex/skills/
```

Alternative (symlink for active development):

```bash
mkdir -p ~/.codex/skills
ln -sfn "$(pwd)/salesforce-manual-qa" ~/.codex/skills/salesforce-manual-qa
```

## 2) Restart Codex

Restart the Codex process/session so it reloads available skills.

## 3) Trigger the skill in a live run

Use an explicit prompt:

- `Use salesforce-manual-qa: Create a regression test plan for Opportunity stage automation changes.`
- `Act as Salesforce manual QA. Build UAT test cases for Case assignment and escalation.`

## 4) Validate the skill before using

```bash
python /opt/codex/skills/.system/skill-creator/scripts/quick_validate.py salesforce-manual-qa
```

## 5) What "live" means for this skill

- Live operation = the skill actively guiding test design/execution in Codex chat.
- It outputs artifacts (test plans, test case tables, defect logs, sign-off notes).
- It does not spin up a browser UI or standalone runtime service.
