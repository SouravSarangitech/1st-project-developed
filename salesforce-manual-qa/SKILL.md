---
name: salesforce-manual-qa
description: Manual QA workflow for Salesforce platform changes across Sales Cloud, Service Cloud, Experience Cloud, and custom Lightning apps. Use when planning or executing human test cycles for user stories, UAT, regression, smoke testing, pre-release validation, defect triage, and go/no-go recommendations in Salesforce orgs.
---

# Salesforce Manual QA

## Overview

Use this skill to run a repeatable manual testing process for Salesforce releases. Produce practical artifacts: risk-based test plans, detailed test cases, execution logs, defect reports, and release sign-off summaries.

## Workflow

1. **Intake release scope**
   - Capture story IDs, affected objects, automations (Flow, Apex, validation rules), profiles/permission sets, integrations, and reports/dashboards.
   - Confirm environment and data readiness (sandbox type, refresh date, test users, seeded records).
2. **Assess risk and test depth**
   - Classify each scope item as High/Medium/Low risk by customer impact, data integrity risk, security implications, and integration touchpoints.
   - Choose test depth:
     - **Smoke**: critical happy paths only.
     - **Targeted regression**: changed components + direct dependencies.
     - **Full regression/UAT**: cross-cloud flows and edge conditions.
3. **Author test cases**
   - Write each test case with: Preconditions, Steps, Expected Result, Test Data, and Post-conditions.
   - Include both positive and negative tests, role-based access checks, and audit/log visibility checks where relevant.
4. **Execute and record**
   - Run test cases manually and record actual results precisely.
   - Mark status: Pass / Fail / Blocked / Not Run.
   - Link evidence (record IDs, screenshot names, debug log snippets, email IDs, integration request IDs).
5. **Triage defects**
   - For each failed case, create a defect with severity and reproducibility.
   - Separate true defects from data/setup issues and expected behavior changes.
6. **Report release readiness**
   - Summarize coverage, pass rate, open critical defects, known risks, and go/no-go recommendation.

## Salesforce-specific coverage checklist

Always evaluate these areas when relevant to scope:

- **Data model and validation**: objects, fields, requiredness, formula behavior, duplicate/matching rules.
- **Security model**: profiles, permission sets, FLS, record-level access, sharing rules, role hierarchy.
- **Automation**: Flow, Process Builder (legacy), Apex triggers/classes, assignment/escalation rules, approval processes.
- **UI/UX**: Lightning pages, dynamic forms/actions, list views, quick actions, mobile behavior.
- **Integrations**: inbound/outbound APIs, platform events, middleware mappings, retries/error handling.
- **Reporting**: report types, dashboard components, filter logic, data visibility.
- **Notifications**: email alerts, chatter posts, in-app notifications, task creation.
- **Performance/reliability**: save latency, bulk behavior, governor-limit-sensitive paths.

If unsure what to test next, load `references/manual-test-scenarios.md` and pick scenarios matching the impacted feature set.


## Use and deploy

To run this skill in a live Codex environment, follow `references/live-setup.md`.

Quick summary:
- Install/copy (or symlink) this folder to `~/.codex/skills/salesforce-manual-qa`.
- Restart Codex so the new skill is discovered.
- Trigger it with an explicit prompt naming `salesforce-manual-qa`.

## Output formats

When asked for deliverables, use these structures:

### 1) Test plan (summary)
- Scope in / out of scope
- Risk matrix
- Test environments and users
- Test cycles and entry/exit criteria

### 2) Test case table
Columns: `ID | Feature | Priority | Preconditions | Steps | Expected Result | Data | Owner | Status | Evidence`

### 3) Defect report
Columns: `Defect ID | Linked Test Case | Severity | Environment | Steps to Reproduce | Expected | Actual | Evidence | Assignee | State`

### 4) Sign-off note
- Total test cases (pass/fail/blocked/not run)
- Open defects by severity
- Business impact statement
- Go / No-Go recommendation with rationale

## Quality bar

Before marking testing complete, verify:

- All high-risk scenarios were executed or explicitly deferred with approval.
- All Sev-1/Sev-2 defects are closed or formally accepted.
- Permission and data-visibility checks were completed for each affected role.
- Evidence is attached for every failed or blocked test.
- Final recommendation is explicit and traceable to test evidence.
