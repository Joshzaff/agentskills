---
name: mca-site-compliance
description: Compliance and truthfulness rules for business-funding / merchant cash advance (MCA) broker websites. Use whenever writing or editing page copy, headings, page titles, meta descriptions, OG tags, JSON-LD, alt text, FAQs, emails, SMS, or code comments on a funding-broker site, and before shipping any marketing change. Covers banned terminology, the required broker disclosure, no invented proof, no fake urgency, and the placeholder convention for missing business facts.
---

# MCA Site Compliance

These sites are live brokerages taking real applications. The rules below are
legal exposure, not style preferences. A project's own instructions (CLAUDE.md,
project knowledge) take precedence where they are more specific.

## 1. Terminology — enforced everywhere

Applies to visible copy, page titles, meta descriptions, OG/Twitter tags, JSON-LD,
alt text, aria labels, button text, emails, SMS, and code comments.

| Never use (for an MCA)          | Use instead                                   |
| ------------------------------- | --------------------------------------------- |
| loan, loans                     | advance, merchant cash advance, funding       |
| lender, lenders                 | funding partner                               |
| borrow, borrower, borrowing     | receive funding, business owner / merchant    |
| interest rate, APR, interest    | factor rate                                   |
| payment(s) / repayment          | remittance(s)                                 |
| alternative lending             | business funding, working capital             |
| loan amount                     | funding amount, advance amount                |

Describe the product as a **purchase of future receivables**, not a loan.

Only acceptable uses of "loan"/"lender": the disclosure sentences below that say
what the company is *not* ("is not a lender", "not a loan"), and SBA / term /
equipment products that genuinely are loans, labelled as such and clearly
distinct from the MCA.

Before finishing, grep the changed files, case-insensitive:

```
\b(loan|loans|lender|lenders|lending|borrow\w*|interest rate|APR|alternative lending|repayment)\b
```

Every hit must be either replaced or be one of the allowed exceptions above.

## 2. Broker disclosure — footer of every page

Keep this in the footer on every route (including /apply and success pages),
with the company name pulled from the site's company config:

> {Company} is not a lender. We connect business owners with funding partners.
> Approval amounts, factor rates, and terms are determined by the funding partner
> and vary based on business qualifications. A merchant cash advance is a purchase
> of future receivables, not a loan.

If the project defines its own exact wording, use that wording verbatim.
Never remove, shorten, shrink below readable size, or hide it behind a toggle.

## 3. Nothing invented

Never fabricate, estimate, or "placeholder with realistic values":

- testimonials, reviews, star ratings, review counts
- statistics (funded totals, approval rates, number of clients, years in business)
- team names, photos, titles, bios
- addresses, phone numbers, emails, hours, legal entity names
- partner/funder names or logos, "As seen in" strips, press mentions
- funded-deal examples or case studies

Fabricated endorsements violate FTC 16 CFR Part 255.

If a section needs a value the owner has not supplied, leave a **visible**
placeholder using the project's convention (default `TODO(owner): <what's needed>`;
some projects use `{{TODO: confirm}}`) and list every placeholder in your summary
to the user. Contact details come from the project's company config file
(e.g. `src/config/company.ts`) — never inline them.

## 4. No fake urgency

No countdown timers, "only N slots left", "offer ends tonight", fabricated
live-activity tickers ("John in Miami just got funded"), or auto-popping
scarcity modals. Real, owner-confirmed deadlines may be stated plainly.

## 5. Say the uncomfortable thing plainly

- We are a broker, not a lender — say so above the fold on relevant pages.
- Cost is a factor rate, not an interest rate. Explain it honestly
  (e.g. a 1.3 factor rate on $10,000 means $13,000 remitted) with no fabricated
  "typical" rates.
- Don't promise approval, specific amounts, or speed guarantees the owner hasn't
  confirmed. "Guaranteed approval" is never acceptable.

## 6. Imagery

No stock-photo clichés: handshakes, headset call-center staff, rooftop skylines,
piles of cash. Alt text follows the terminology rules too.

## 7. Live application flow

The apply form takes real submissions. Do not change its schema, field names,
validation, submit handler, uploads, or backend integrations as part of a
content/compliance pass. If a compliance fix would require touching submission
logic, stop and report it instead.

## Pre-ship checklist

- [ ] Terminology grep clean (or only allowed exceptions)
- [ ] Disclosure present in footer on every route
- [ ] No invented numbers, names, reviews, logos, or contact details
- [ ] Every missing fact is a visible TODO and listed in the summary
- [ ] No urgency devices
- [ ] Meta titles/descriptions/alt text checked, not just body copy
- [ ] Apply flow untouched (or explicitly approved and tested end-to-end)
