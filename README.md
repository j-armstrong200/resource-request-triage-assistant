# Resource Request Triage Assistant

A small AI-assisted tool that helps nonprofit intake staff quickly prioritize
incoming requests for help — built as a project for my Claude Corps Fellow
application.

**Try it live:** https://claude.ai/public/artifacts/b86d6398-a12f-4e85-b074-1529e0dddcf2
*Note: this tool calls the Claude API live, so Anthropic requires viewers to be signed into a free Claude.ai account to use the "Triage this request" button.*

## The Problem

Small nonprofits that handle general social services intake — housing,
food, financial assistance, medical, legal, employment — often receive more
requests than staff can immediately read and prioritize. A request that
needs a response within the hour can end up sitting in the same queue as
one that can wait a few days, simply because there's no fast way to tell
them apart at a glance.

## What This Tool Does

Staff paste in a request (an email, a voicemail transcript, a walk-in note)
along with the client's name and contact info, and the tool:

- Assigns a priority: **Emergency**, **Respond Today**, or **Can Wait**
- Suggests a category (Housing, Food, Financial Assistance, Medical, Legal,
  Employment, Other)
- Summarizes the request in one line
- Flags if contact information is missing
- Suggests a concrete next step
- Drafts an editable follow-up email
- Keeps a running "Today's Summary" log with priority counts

A human caseworker always reviews and makes the final call — the tool only
provides a first read to help prioritize a busy inbox.

## A Decision I Made: The Triage Rules

The core judgment of this tool lives in an editable set of triage rules
(visible in the tool itself). I defined three tiers:

- **Emergency** — immediate safety risk, a disclosure of danger, a medical
  emergency, or a housing/utility issue happening the same day
- **Respond Today** — a hard deadline this week (like a court date), or a
  first-time caller in visible distress
- **Can Wait** — general information requests, referrals, and routine
  follow-ups

I chose these tiers based on what seemed like the clearest, most defensible
way to separate "this could cause harm if delayed" from "this is important
but not time-critical." I wrote these rules myself, without real intake
data — a real intake coordinator would likely refine them significantly.

## What I'd Do Differently

- Rules were written without input from actual nonprofit staff. Before
  using this for real, I'd sit with an intake coordinator, walk through
  real (anonymized) past requests, and adjust the tiers based on what they
  actually consider urgent.
- Right now, the daily summary only persists for the current browser
  session — it disappears if the page is closed. A real version would need
  to save requests somewhere staff could return to.
- There's no way yet to correct a wrong priority and have the tool learn
  from that correction — right now, staff would just override it manually.
- I'd want to test it with messier, more realistic input (typos, incomplete
  sentences, multiple issues in one request) rather than clean examples.

## How It Was Built

Built as a single HTML/CSS/JavaScript page, using the Claude API to read
each request against the triage rules and return a structured response.
No backend server or database — the tool runs entirely in the browser.

## Author

Jeanine Armstrong — built as part of a Claude Corps Fellow application.

