# clabot-config

Single **cla-bot** configuration for the **vex-protocol** organization.

## How cla-bot finds this file

The [cla-bot GitHub App](https://github.com/apps/cla-bot) automatically resolves configuration from a repository named **`clabot-config`** at the organization (or user) level:

`https://github.com/vex-protocol/clabot-config/blob/main/.clabot`

You do **not** need a `.clabot` file in every repository. Install **cla-bot** on the org (or selected repos) and grant the app access to this **`clabot-config`** repository (during install or under **Settings → GitHub Apps → cla-bot → Configure**).

If the contributor list must not be public, keep this repository **private**; cla-bot can still read it when authenticated.

## `.clabot` schema

| Property | Purpose |
|----------|---------|
| `contributors` | Array of GitHub usernames with a CLA on file, or a URL / webhook (see cla-bot docs). Here we use an **array**, updated by maintainers or by [vex.wtf](https://vex.wtf) **Admin → CLA** when `CLA_BOT_REPOS` includes this repo. |
| `message` | Optional. Comment when some committers are not in `contributors`. Supports `{{usersWithoutCLA}}`. |
| `label` | Optional. Label applied when everyone is covered (default in many setups: `cla-signed`). |
| `recheckComment` | Optional. Comment when someone runs **`@cla-bot check`**. |

Canonical sign-up flow for contributors: **https://vex.wtf/cla**

## Deploy checklist

1. Create **`vex-protocol/clabot-config`** on GitHub (this folder is the repo root). Use **`main`** as default branch so the URL above matches.
2. Grant **cla-bot** access to **`clabot-config`**.
3. Set **`CLA_BOT_REPOS=vex-protocol/clabot-config`** on vex.wtf (with **`GITHUB_CLA_BOT_TOKEN`** contents write) so approvals append usernames here.
4. Add existing maintainers to `contributors` in `.clabot` so their PRs pass before external contributors open PRs.
