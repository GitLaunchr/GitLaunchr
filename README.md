# GITLAUNCHR ⚡️🏙️
<p align="center">
  <img src="assets/gitlaunchr_banner.gif" alt="GitLaunchr banner" width="100%" />
</p>

<p align="center">
  <img src="assets/gitlaunchr_logo.png" alt="GitLaunchr logo" width="180" />
</p>

<p align="center">
  <b>Launch tokens using your GitHub account.</b><br/>
  A pixel-powered launchpad on <b>Base</b>, deployed by <b>Bankr</b>.
</p>

<p align="center">
  <a href="#how-it-works">How it works</a> •
  <a href="#launch-flow">Launch flow</a> •
  <a href="#fee-split">Fee split</a> •
  <a href="#setup">Setup</a> •
  <a href="#roadmap">Roadmap</a>
</p>

---

## What is GitLaunchr?
**GitLaunchr** is a GitHub-gated launchpad.
You sign in with GitHub, fill a token form, hit **LAUNCH**, and **Bankr** handles the deployment on **Base**.

No wallet popups. No browser signing.  
Just GitHub identity + a clean launch workflow.

---

## Why GitHub login?
GitHub is the builder passport:
- Prevents spam launches
- Adds reputation & identity (username, avatar, orgs later)
- Enables rate limits, allowlists, and “verified builder” badges

---

## How it works
GitLaunchr uses **Model B (platform-assisted launch)**:

1) User signs in with GitHub
2) User fills token details + creator payout address
3) Server deploys a **FeeSplitter** contract on Base
4) Server calls **Bankr Agent API** to deploy the token on Base
5) Fee beneficiary is set to the **FeeSplitter**
6) Launch page shows progress + final token address

---

## Launch flow
1. **Sign in with GitHub**
2. Go to **/launch/new**
3. Fill:
   - Token name
   - Token symbol (2–8 uppercase)
   - Creator payout address (Base/EVM)
   - Optional: description, website, twitter
4. Click **LAUNCH WITH BANKR**
5. Watch live status:
   - Splitter deployed
   - Bankr job created
   - Deploy in progress
   - Done → token address

---

## Fee split
Bankr routes the **creator share** to a **fee beneficiary** address.

GitLaunchr sets the fee beneficiary to a **FeeSplitter contract** that splits the creator share:

- **90% → creator payout address**
- **10% → GitLaunchr treasury**

### What this means in total fee terms
If the creator share is **57% of total fees**, then:
- Creator effectively receives **51.3%** of total fees (57% × 90%)
- Platform effectively receives **5.7%** of total fees (57% × 10%)

All splits are automatic and on-chain via the FeeSplitter.

---

## Tech stack
- **Next.js (App Router) + TypeScript**
- **Auth.js / NextAuth** (GitHub OAuth)
- **Supabase Postgres** (users + launches)
- **Viem** (server-side deploy of FeeSplitter on Base)
- **Bankr Agent API** (prompt + job polling)
- **CSS Modules** (pixel UI, scanlines, HUD panels)

