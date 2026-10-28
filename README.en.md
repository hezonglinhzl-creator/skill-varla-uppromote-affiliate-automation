# UpPromote KOL Affiliate Workflow / UpPromote KOL 联盟流程

[简体中文](README.md) | **English**

Start from a Feishu creator record and verify affiliate details, coupons, links and email stages using the current browser state.

[Download complete project ZIP](https://github.com/hezonglinhzl-creator/varla-electric-mobility-skills-and-tools/raw/main/packages/skill-varla-uppromote-affiliate-automation.zip) · [All projects](https://github.com/hezonglinhzl-creator/varla-electric-mobility-skills-and-tools)

## Features

- Exact record/email matching
- Coupon and existing-link deduplication
- Dry runs, email drafts and stage recovery

## What is included

| Part | Location |
| --- | --- |
| Shopify KOL Browser Order Tool | [shopify-order-bot](apps/shopify-order-bot/README.en.md) |
| Skill instructions | [SKILL.md](skill/varla-uppromote-affiliate-automation/SKILL.md) |

## Download and extract

1. Open this repository, choose **Code → Download ZIP**, or use the complete-project download above.
2. Right-click the downloaded ZIP and choose **Extract All**. Open the extracted folder containing this README.
3. Keep the whole folder together. Start the program first using the next section, then install/use its skill.

Installation also writes PACKAGE-LOCATION.json beside the installed SKILL.md, mapping the bundled programs to their actual extracted directories. Keep the full extracted folder; rerun the installer after moving it. Existing Skill content is preserved by default while paths are refreshed.

## 1. Set up the program first

### Shopify KOL Browser Order Tool (`shopify-order-bot`)

Python 3.11+, AdsPower Local API and your Shopify admin access.

Open `apps/shopify-order-bot` first. Single-order Excel validation, address checks, fill and a separate submit step.

1. Run `python -m pip install -r requirements.txt`, then `python -m playwright install chromium`.
2. Copy `.env.example` to `.env` and enter your AdsPower API settings, profile ID and SHOPIFY_ADMIN_URL.
3. Prepare `KOL_order.xlsx` using this folder's documented headers; start with one synthetic test row.
4. Run `python main.py --step adspower`, then `python main.py --step browser` and log in to your own profile.
5. Run `python main.py --step fill` and review before submission. Execute real submission only when explicitly authorized.

[Full program / browser-extension guide](apps/shopify-order-bot/README.en.md)

Private configuration, login sessions and order workbooks must be supplied by the operator.

## 2. Install the Skill

1. At the extracted project's root, double-click `安装Skill.cmd` on Windows.
2. The installer copies `skill/varla-uppromote-affiliate-automation` to `%USERPROFILE%\.codex\skills\varla-uppromote-affiliate-automation`. Existing same-name skills are skipped; check the displayed result.
3. Reopen Codex and start a new chat. Use the exact skill name shown below.
4. If scripts cannot run under your organization policy, open install.ps1 for review or copy the skill directory manually to the same destination.

## 3. First task

| Prepare | Details |
| --- | --- |
| Input | Your Base/record URL, exact code, AdsPower session and service configuration. |
| Output | Verified codes/links, Feishu readbacks and email drafts or receipts. |

```text
Use varla-uppromote-affiliate-automation to dry-run my record, check existing codes/links and report missing setup without creating records or sending mail.
```

## Start with read-only validation

Run inside `skill/varla-uppromote-affiliate-automation` after configuring your Feishu/browser environment. Replace the placeholder with a URL you may access.

```powershell
python scripts/run_varla_affiliate.py --feishu-url "YOUR_FEISHU_BASE_URL" --code-name "YOUR_APPROVED_CODE" --dry-run
```

## Limits and troubleshooting

Requires your Feishu, AdsPower, Shopify/UpPromote and Gmail setup. Coupon rules must follow currently confirmed policy.

| Problem | Next step |
| --- | --- |
| Skill not visible | Check the installer output and destination SKILL.md, reopen Codex and start a new chat. |
| Program fails to start | Open its directory in PowerShell and run the documented command so the error remains visible; check that program's README. |
| Browser panel missing | Select the exact folder containing manifest.json, check supported websites and refresh the website tab. |
| External service unavailable | Supply your own authorization/settings and verify access. Keep local output rather than claiming a sync/send succeeded. |

## Privacy and status

This is a source/skill distribution. No real accounts, OAuth tokens, customer/KOL lists, contracts, orders, mailbox exports or business media are included. You configure your own services. Documentation and package paths were checked; live orders, sends and publications were not executed as part of documentation validation.
