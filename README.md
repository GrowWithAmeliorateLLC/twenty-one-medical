# Twenty-One Medical — twentyonemedical.com

Static site for Twenty-One Medical PLLC (Pineville, NC). Contact: Shawn O'Keefe, PA-C.
Built and hosted by Grow With Ameliorate LLC. Deploys from `main` via Netlify (project `twenty-one-medical`), published from the repo root with no build step.

## Project facts

- Scope: https://scope.growwithameliorate.com/twenty-one-medical
- Found report: https://found.growwithameliorate.com/twenty-one-medical
- Kickoff 2026-09-15 · go-live 2026-10-06
- Ten pages: Home, Medical Weight Loss, Hormone Replacement Therapy, Peptide Therapy,
  IV Therapy, Laser Treatments, Clinical Care hub, About (Meet Shawn), Book Online, Contact

## DNS — read before touching anything

The domain is registered at **GoDaddy** and GoDaddy runs DNS
(`ns65.domaincontrol.com` / `ns66.domaincontrol.com`). At cutover, change **only** the
A/CNAME records that point the website. Two hard rules:

1. **Never touch the MX records.** Mail runs on Microsoft 365
   (`twentyonemedical-com.mail.protection.outlook.com`). Wholesale record replacement
   takes down the practice's email.
2. **Domain expires 2026-10-04** — two days before go-live. Confirm auto-renew is on
   before launch week.

Old site: GoDaddy Airo at `160.153.0.77`. That subscription lapses after cutover;
the domain registration itself stays with the client, in the client's name.

## Integrations

| System | Role | Notes |
|---|---|---|
| DrChrono | EMR + calendar of record | Embed the scheduling widget only. Never migrate. Confirm plan tier includes it. |
| Weave | Calls, texting, patient forms, review requests | Connect to it, not around it. |
| Zocdoc | Existing patient source | Preserved. Stops being the only way to book. |
| Cherry / CareCredit | Financing | Rebuild links onto service pages using existing accounts. |
| GA4 + GTM | Analytics | Install at build. |

Nothing in this repo handles PHI. Anything collecting patient information must run
through a system the client already holds an agreement with.

## Conventions

- One `.html` file per page at the repo root, kebab-case.
- Legacy 301s live in `_redirects`, root-relative targets.
- No secrets in this repo.
