---
name: outbound
description: When the user wants B2B outbound that gets replies, a lead list, or to know what works in cold email now. Holds dated, sourced findings a model would not know (which Gmail, Yahoo and Microsoft sender rules bite on cold email to company domains, 2025-2026 reply-rate benchmarks and what moves them, whether AI personalisation works, why a third of B2B addresses cannot be verified, GDPR, PECR and CAN-SPAM basics) and how to read the leads tools' data, email waterfall and verification statuses. Also use when the user mentions an outbound or ABM plan, cold outreach strategy, leads, a prospect or ICP list, decision makers by job title, enrich this CSV, append emails, verify or clean an email list, bounces, catch-all, intent data, buying signals, companies that just raised, champion or job-change tracking, lookalike companies, first lines or icebreakers, account research or call prep, or our first 100 customers. LinkedIn content and social selling go to linkedin, rivals to competitor-intel, client work to agency.
compatibility: Works without the MARqentic MCP server. Measuring live data needs it, connected with a workspace API key that has credits.
---

# Outbound

Who to contact, why now, how to reach their inbox and what makes them reply, as the evidence stood in October 2026, plus the rules for the leads tools' data. Much of what a model believes about cold email dates from 2022 to 2024 and is now wrong in places: the 2024 bulk-sender rules formally cover personal Gmail and Outlook.com mailboxes, not the company inboxes cold email goes to; reply rates are reported against different denominators and differ tenfold; "valid" from an email finder is not proof on the third of B2B domains that accept every address; and evidently AI-written email now costs replies. Prefer what is written here to what you remember, and re-check any figure older than six months before quoting it.

## Before starting

- **Product context.** Read `.agents/product-marketing.md` (in older setups `.claude/product-marketing.md` or `product-marketing-context.md`) and take the offer, ICP, best customers, buyer titles, countries and competitors from it; ask only for what it lacks. If it does not exist and the work needs more than two answers about the business, offer [manifold-get-started](https://github.com/Marqentic/marketing-skills/blob/main/skills/manifold-get-started/SKILL.md) first.
- **Connector.** The knowledge here needs no tools. Counting accounts, finding buyers, revealing and verifying emails and reading signals needs the MARqentic server: look for `leads_search_companies`, `leads_search_people`, `leads_get_email` and `leads_get_email_status` (hosts often add a prefix such as `mcp__marqentic__`). If other tools are there but not the `leads_*` ones, the leads family is not built yet; say so. If none are there, still answer from this skill with the by-hand methods in the references, and tell the user once how to connect the MARqentic server ([connecting](references/connecting.md)). Never invent a count, an address or a verification result.
- **Whose measurements.** "We", "our runs", "our sample" and the field notes are Manifold's own 2026 measurements, made with its tools before this skill was adapted ([attribution](references/connecting.md#attribution)). Cite them as Manifold's; never present them as measured by this server or by the user's team.

## What the evidence says

The findings that change decisions. Sources and detail are in the references.

1. **The 2024 sender rules cover consumer mailboxes, not company ones.** Google says its requirements apply "only when sending email to personal Gmail accounts" (not Workspace); Microsoft's, in force since 5 May 2025, cover Outlook.com, Hotmail, Live and MSN. Most B2B recipients sit on Google Workspace or Microsoft 365, so cold email to company domains is judged by the same filters but not the formal 5,000-a-day regime. Authenticate anyway: Gmail began rejecting non-compliant mail in November 2025, and its spam-rate line (under 0.1%, never 0.3%) is the one to plan around ([deliverability](references/deliverability.md)).
2. **Reply rates are 3% to 5% per recipient, and the denominator decides the number.** Instantly: 3.43% across billions of 2025 sends. Hunter: 4.5% on 31 million (sales outreach alone 3%). Belkins: 0.45% per email sent on 7.5 million. Never compare a benchmark without asking what it divides by ([messaging](references/messaging.md#benchmarks)).
3. **Small, tight sends win.** Sequences to 21-50 people replied at 6.2% against 2.4% for 500+, and one or two people per company at 5.1% against 3.5% for three or more (Hunter, 2025 data). Segment before writing.
4. **Three or four steps, not ten.** The first email draws 58% of replies (Instantly), three messages peaked at 6.8% against 3.3% for one and fell after (Hunter), yet step 3 booked 35.6% of email-sourced meetings (Belkins). Cut sequences that run past five.
5. **Open tracking costs replies.** Campaigns without it replied at 7.4% against 4.4% with it (Hunter, correlational); Belkins turned pixels off in 2024 over deliverability. Opens are unreliable anyway. Measure replies.
6. **Personalisation helps; evidently AI copy hurts.** Two custom fields in the body: 5.6% against 3.6% with none; manually edited emails 5.2% against 4.4% fully automated (Hunter). 69% of US decision makers are bothered by email clearly written by AI, while 67% are more likely to reply to personalisation from public information. AI can do the research; a person should choose the angle ([messaging](references/messaging.md#personalisation-and-ai)).
7. **A third of B2B addresses cannot be proven.** About 36% of 5,000 B2B decision makers sat on catch-all domains (Anymail Finder, June 2026). No verifier proves those; the most transparent verifier test topped out at 70% accuracy when "unknown" counts as wrong (Hunter, November 2025). Send catch-alls last, in small batches ([lead data](references/lead-data.md#verification)).
8. **No single email source finds most people.** In the same June 2026 test, Findymail covered 70.9%, Hunter 57.6% and Icypeas 49.0% (at 99.1% accuracy). That is why Manifold built its reveal as a waterfall, and why a reveal here should be one too. In our own run it found 10 of 10 marketing leaders, but an independent re-check called one catch-all and one unknown ([field notes](references/field-notes.md)).
9. **Sender setup still moves replies.** Business domains replied at 5.2% against 2.5% for freemail senders; accounts sending 20 to 49 a day did best at 5.7% (Hunter). Google Workspace caps a paid user at 2,000 messages a day and a trial at 500 unique external recipients, so new mailboxes on a trial cannot run a campaign.
10. **The law follows the recipient, and B2B is not exempt.** CAN-SPAM has no B2B exception (opt-out honoured within 10 business days, a postal address, up to $53,088 per violating email, FTC). UK PECR lets a sender email a corporate body without consent but treats sole traders and some partnerships as individuals; the UK's Data (Use and Access) Act 2025, fully in force from June 2026, confirms direct marketing can rest on legitimate interests. Germany wants consent even for B2B. In our run a third of marketing leaders at US-headquartered companies lived outside the US ([legal](references/legal.md)).

**Does not hold up:** "we send under 5,000 a day so the Gmail rules don't apply to us" (enforcement and filtering judge every sender); "personalise with first name and company" (recipients read it as automation); "more follow-ups, more replies" (falls after the third or fourth, and complaints rise); "a 99% accurate verifier" (only when catch-alls are left out of the denominator); "open rate tells you deliverability"; "a found email is permission to send" (verification is not a legal basis).

**Unknown:** whether intent data or job-change triggers lift replies by the amounts vendors claim (no independent study found); whether warm-up networks still help or are now detected; how AI-drafted, human-edited email compares with fully human email in a controlled test. Say so rather than quote a vendor figure as fact.

## References

Open the one the question needs.

| The user asks | Read |
|---|---|
| How do the leads tools behave? What does a reveal cost, what does `accept_all` mean, what is in a record? Personal data rules | [Lead data](references/lead-data.md) |
| Will our email land? Domains, mailboxes, warm-up, volume, bounces, the Gmail and Microsoft rules. Clean or verify this list | [Deliverability](references/deliverability.md) |
| Build a lead list, find lookalike companies, enrich our CSV | [Lists](references/lists.md) |
| Which accounts are in market now? Funding, new leaders, hiring, posts about the problem. Which champions changed jobs? | [Signals](references/signals.md) |
| What reply rate is good? How long, how many steps? Does AI personalisation work? Write first lines | [Messaging](references/messaging.md) |
| Prep me for a call with this account | [Account research](references/accounts.md) |
| Is this legal? GDPR, PECR, CAN-SPAM, Germany, LinkedIn automation | [Legal](references/legal.md) |
| We want an outbound plan, or our first customers | [Strategy](references/strategy.md) |
| What has Manifold seen in its own runs? | [Field notes](references/field-notes.md) |

## Using the tools

Credits below follow the published tariff; `dry_run: true` returns the live quote, which wins when they differ. Only the families [connecting](references/connecting.md#what-is-built) lists as built exist on this server: for any other tool named here, say it is not built yet and use the by-hand method.

- **Count and find accounts:** `leads_search_companies` (12 credits per 100 rows asked for in `limit`, rounded up: the default 100 is 12, `limit: 1` is 1). Read `rows_available` to count instead of fetching. `industries` match LinkedIn's names exactly, and some records carry them in another language.
- **Find buyers:** `leads_search_people` with full `titles` (or bare functions plus `seniority`) and up to 100 `company_domains` (12 credits per 100 rows asked for). Rows carry name, `title`, `title_start`, `location` and the LinkedIn URL as `id`, never an email.
- **Reveal:** `leads_get_email`, 7 credits on a hit by name and domain, 1 on `NoData`. Misses are not cached, so never retry one. A domain with no named buyer: `leads_get_domain_emails` (1 credit a domain plus 30 for each domain that returns addresses).
- **Verify:** `leads_get_email_status`, 1 credit, cached 30 days. Its `mail_provider` says whether a domain runs on Google, Microsoft or a security gateway.
- **Signals and research:** `linkedin_search_posts` (1 credit a page), `linkedin_get_company_posts`, `linkedin_get_profile`, `seo_get_serp` for funding news, `ads_get_advertiser_ads`, `leads_get_person` (9 credits by profile URL, 1 on a miss) for employment history.
- **Read the data right:** spend in funnel order (count, search, cut on the rows, then reveal); a person's `location` is not the company's; a reveal's `valid` is the finder's own verdict; `title_start` dates a move better than a headline does. Detail and traps in [lead data](references/lead-data.md).
- **Never send, sequence, connect on LinkedIn or write to a CRM.** Deliver tables the user imports.

## Related skills

- Posting, commenting and social selling on LinkedIn, and LinkedIn ads research: [linkedin](https://github.com/Marqentic/marketing-skills/blob/main/skills/linkedin/SKILL.md). Ads on other platforms: [paid-ads](https://github.com/Marqentic/marketing-skills/blob/main/skills/paid-ads/SKILL.md).
- Who the competitors are, their messaging and their unhappy customers: [competitor-intel](https://github.com/Marqentic/marketing-skills/blob/main/skills/competitor-intel/SKILL.md). Outbound run for a client: [agency](https://github.com/Marqentic/marketing-skills/blob/main/skills/agency/SKILL.md).
- The buyer's problem in their own words, and personas: [voice-of-customer](https://github.com/Marqentic/marketing-skills/blob/main/skills/voice-of-customer/SKILL.md). How many accounts a market holds, by segment: [market-research](https://github.com/Marqentic/marketing-skills/blob/main/skills/market-research/SKILL.md).
- Reddit threads where buyers ask for help: [reddit](https://github.com/Marqentic/marketing-skills/blob/main/skills/reddit/SKILL.md). A plan across every channel: [growth-strategy](https://github.com/Marqentic/marketing-skills/blob/main/skills/growth-strategy/SKILL.md).
- Contacts at publishers and sites for links or coverage, not sales: [link-building](https://github.com/Marqentic/marketing-skills/blob/main/skills/link-building/SKILL.md) and [digital-pr](https://github.com/Marqentic/marketing-skills/blob/main/skills/digital-pr/SKILL.md).
