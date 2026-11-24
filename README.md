# Career Profile Advisor

An early-stage AI-powered career-profile tool built by **Daijon.AI**. It helps job seekers draft or improve a LinkedIn profile using their own experience and career goals, with an emphasis on accurate, supportable claims.

**Status:** Beta / under testing. The live AI response and rate-limiting configuration should be verified before sharing widely.

## What it does

- Start a LinkedIn profile from scratch, or improve an existing one.
- Optionally paste an employer's job description for more relevant suggestions.
- Describe work experience, skills, projects, and certifications.
- Ask AI to suggest potentially relevant skills, then confirm them manually.
- Generate a draft headline, About section, experience bullets, skill gaps, and next steps.
- Copy the resulting recommendations to edit and use elsewhere.

## Built with

- Cloudflare Workers
- Cloudflare Workers AI (`env.AI` binding)
- HTML, CSS, and vanilla JavaScript

No separate frontend build system or application database is required in this beta.

## Running it on Cloudflare

1. Create a Cloudflare Worker or import this GitHub repository into Cloudflare Workers.
2. Deploy `worker.js` as the entry point. `wrangler.toml` provides the configuration for command-line or Git-based deployment.
3. Configure a **Workers AI binding named `AI`**.
4. Test `/` with fictional career data and check the AI responses.
5. **Before inviting public testers:** configure and test rate limiting for `/api/review` and `/api/skills`. The source checks an optional binding called `REVIEW_LIMIT`; the binding must be created separately.

### Files

- `worker.js` — website, browser-side interactions, and Worker API handlers.
- `wrangler.toml` — Cloudflare Worker configuration, including the Workers AI binding.

## Privacy and limitations

- Submitted text is sent to Cloudflare Workers AI for processing.
- This prototype does not implement a user-profile database.
- Do not provide passwords, government IDs, private contact information, or confidential employer information.
- Generated guidance may be inaccurate and must be verified before it is used.
- Not affiliated with LinkedIn or any employer; it does not edit LinkedIn profiles automatically.
- Public API endpoints may consume your Cloudflare Workers AI allocation. Rate limiting is needed before a public launch.

## About

An independent learning and product-building project from Daijon.AI. Feedback from job seekers and career changers will guide future improvements.
