---
name: x-twitter
description: When the user wants to know what works on X (Twitter) now, audit an X account (their own, a founder's or a competitor's), or decide whether and how to post there. Holds what a model would not know from training (what X's published ranking code weighs since January 2026, what X has said and others have measured about link posts and Premium, why engagement benchmarks disagree by a factor of a hundred, who is on X in 2025-2026) and how to read the X tools, which see one account's feed and nothing else. Also use when the user mentions an X or Twitter audit, audit our Twitter, how does our Twitter compare to a competitor's, what a founder or brand posts on X, which tweets get the views, the X algorithm, the link penalty, links in replies, whether to pay for X Premium or a blue check, threads, why our reach dropped on X, shadowbanned, or an X strategy. LinkedIn goes to linkedin, finding and paying creators to creators, mentions of the brand by others to brand-monitoring.
compatibility: Works without the MARqentic MCP server. Measuring live data needs it, connected with a workspace API key that has credits.
---

# X (Twitter)

What earns reach on X, as the evidence stood in October 2026, and how to read an account's numbers without fooling yourself. Most of what a model believes about X comes from the 2023 code release and from creator folklore: "a reply is worth 27 likes", "links are deboosted 50 to 90%", "post links in the first reply". Since January 2026 X publishes the For You ranking code it runs, with its production weights since August 2026, and it no longer matches that folklore in places. Prefer what is written here to what you remember, and re-check any figure older than six months before quoting it to a client: X changes the ranking with an A/B test and a post, not an announcement.

## Before starting

- **Product context.** Read `.agents/product-marketing.md` (in older setups `.claude/product-marketing.md` or `product-marketing-context.md`) and take the brand, the X handles of the company and its founders, the competitors and their handles from it; ask only for what it lacks. If it does not exist and the work needs more than two answers about the business, offer [manifold-get-started](https://github.com/Marqentic/marketing-skills/blob/main/skills/manifold-get-started/SKILL.md) first.
- **Connector.** The knowledge here needs no tools. Reading an account's profile and posts needs the MARqentic server: look for `twitter_get_profile`, `twitter_get_tweets` and `twitter_get_tweet` (hosts often add a prefix such as `mcp__marqentic__`). If other tools are there but these three are not, the X family is not built yet; say so. If none of these tools is there, still answer from this skill and use the by-hand method in [audit](references/audit.md#without-the-connector), and tell the user once how to connect the MARqentic server ([connecting](references/connecting.md)). Never invent a measurement.
- **Whose measurements.** "We", "our runs", "our sample" and the field notes are Manifold's own 2026 measurements, made with its tools before this skill was adapted ([attribution](references/connecting.md#attribution)). Cite them as Manifold's; never present them as measured by this server or by the user's team.

## What the evidence says

The findings that change decisions. Sources and detail are in the references.

1. **For You is ranked by a Grok-based transformer, and X publishes the code.** Released January 2026 at github.com/xai-org/x-algorithm, with production weights added 13 August 2026 and updates since. It predicts, per viewer, the chance of about twenty actions and sums them with fixed weights. Reason about the published code, not the 2023 release ([algorithm](references/algorithm.md)).
2. **Conversation and private sharing carry the weight; likes barely do.** The published weights put a reply, a quote and a DM share at 5, copying the post's link at 20, a follow at 4, a repost at 1 and a like at 0.66; a report is −234 and a mute −58.8. X warns these scale predicted probabilities, not counts, so "one reply equals N likes" is a misreading.
3. **Mutual follows got a reply boost in July 2026.** Posts from accounts the viewer follows back get their predicted reply chance weighted up (15 since 24 July, after a launch at 20). Being in a real two-way network now pays more than broadcasting to strangers.
4. **A post has 48 hours.** The ranking drops candidates older than 48 hours, and replies and reposts from accounts the viewer does not follow are filtered out of For You entirely. Judge a post's views after two days; a reply earns reach only in its thread and among the replier's followers.
5. **X says links are not penalised; the evidence is mixed.** Musk wrote on 29 July 2026 that X had not penalised links "for over a year", and the published weights hold no link penalty. Buffer measured 0% median engagement on non-Premium link posts from March 2025 (18.8M posts). OpenTweet's 2026 data (60 accounts) found link posts level with each account's other posts. A bare link with no stand-alone text still does badly: Musk said so in October 2025. Test it on the account; do not assert either way.
6. **Premium buys reach, measured, but not through any multiplier in the published score.** Buffer (18.8M posts, 71K accounts, August 2024 to August 2025) found median impressions under 100 for free accounts, about 600 for Premium and over 1,550 for Premium+, and free accounts' median engagement at 0%. The published For You score has no Premium term; X sells Premium on reply prioritisation, larger on higher tiers (help.x.com, About X Premium), and the gap may come from there and from who pays.
7. **Engagement benchmarks disagree by a factor of a hundred.** X's 2025 median reads 0.03% (Rival IQ/Quid, per follower), 0.12% (Socialinsider, likes and reposts per follower), 0.5% (Buffer, Premium, per impression) and 2.5% (Buffer, all accounts). Never compare an account to a benchmark without matching the formula; compare it to its own median and to a competitor read the same way ([benchmarks](references/benchmarks.md)).
8. **Followers are not an audience.** In our October 2026 reads, median views per follower ran from 0.22 (Vercel) to 0.0014 (TechCrunch, 11M followers, 20 posts in 13 hours). Views per follower, not follower count, says whether the account is alive ([field notes](references/field-notes.md)).
9. **X skews male and young; US use moved right.** Pew (5,022 US adults, 2025): 25% of men and 16% of women use X, 33% of 18 to 29 year olds; 24% of Republicans against 19% of Democrats, reversed from 2023. 12% of US adults regularly get news there. It is the venue for tech, AI, crypto, finance and live news; a weak bet for a mainstream consumer audience.

**Does not hold up:** "a reply is worth 27 likes" or "an author reply is worth 150 likes" (2023 figures; the 2026 code weighs predicted probabilities, and X says reading weights as counts is wrong); "links are deboosted 50 to 90%" (no primary source; X denies it); "always put the link in the first reply" (X says to put it in the post with enough context, and a reply is discounted in For You and dropped for non-followers); "mass reporting can kill a post" (X's code comments say reports from bad actors mostly affect viewers like them); "the blue check is a mark of standing" (anyone can buy it).

**Unknown:** what the Grok-based model has learned about link posts, since the ranking is learned rather than rule-based; whether Premium's reach gap holds now that free accounts' reach has fallen; how much X posts shape answers outside Grok (no study found, and the AI answer tools do not include Grok).

## References

Open the one the question needs.

| The user asks | Read |
|---|---|
| How does X rank posts now? Are links penalised? Does Premium help? What about replies, threads, video? | [Algorithm](references/algorithm.md) |
| Audit our X account, a founder's or a competitor's. Which posts work? How do we compare? | [Audit](references/audit.md) |
| Is our engagement good? What do benchmarks say? Who is on X? | [Benchmarks](references/benchmarks.md) |
| Should we be on X? Company or founder account? What should we post? Should we pay for Premium? Does X feed AI answers? | [Strategy](references/strategy.md) |
| What has Manifold seen in its own reads of X? | [Field notes](references/field-notes.md) |

## Using the tools

Credits below follow the published tariff; `dry_run: true` returns the live quote, which wins when they differ. Only the families [connecting](references/connecting.md#what-is-built) lists as built exist on this server: for any other tool named here, say it is not built yet and use the by-hand method.

- **One account's size:** `twitter_get_profile`, 1 credit, cached 24 hours. `verified` is true for a bought checkmark and read false for Stripe and Vercel, which carry X's gold business check; `kind` read "person" for Stripe. Neither says anything about standing.
- **What it posts:** `twitter_get_tweets`, 1 credit, cached 6 hours, one page with no cursor. **Check what the page is before measuring.** On 6 of 11 accounts in October 2026 it returned about 100 of the account's most-liked posts across years (newest from November 2025), sorted by likes, not the recent feed; on the other 5 it returned 5 to 20 recent posts. The result's `feed` says which: `most_liked` is a greatest-hits page, good for what has ever worked, useless for cadence or current medians ([audit](references/audit.md#first-check-what-the-page-is)).
- **One post by URL:** `twitter_get_tweet`, 1 credit, for a pinned, launch or remembered post the page does not reach.
- **Read the rows right:** drop rows starting "RT @" (their numbers are not the account's) and replies; leave out posts under 48 hours old. `media` reads text, image or video; a link-card post reads text. `shares` is reposts plus quotes, `saves` is bookmarks, `comments` counts replies. A null `views` is a post from before X showed views (late 2022). An X Article shows as a lone x.com/i/article link, not an external link. `top_comments` and `is_ad` came back empty on every row.
- **Cannot see:** search, replies, mentions of the brand by others, followers, impressions by source, link clicks, Premium status. Never post, reply, like, follow or message for the user.
- **Budget:** about 2 credits an account. Pass `max_credits`; `dry_run: true` prices any call for free. The server keeps no history: the host keeps each run's table to compare against.

## Related skills

- The same work on other networks: [linkedin](https://github.com/Marqentic/marketing-skills/blob/main/skills/linkedin/SKILL.md), [youtube](https://github.com/Marqentic/marketing-skills/blob/main/skills/youtube/SKILL.md), [tiktok](https://github.com/Marqentic/marketing-skills/blob/main/skills/tiktok/SKILL.md), [instagram](https://github.com/Marqentic/marketing-skills/blob/main/skills/instagram/SKILL.md), [facebook](https://github.com/Marqentic/marketing-skills/blob/main/skills/facebook/SKILL.md), [reddit](https://github.com/Marqentic/marketing-skills/blob/main/skills/reddit/SKILL.md).
- Paying or vetting accounts to post for the brand: [creators](https://github.com/Marqentic/marketing-skills/blob/main/skills/creators/SKILL.md). What others say about the brand: [brand-monitoring](https://github.com/Marqentic/marketing-skills/blob/main/skills/brand-monitoring/SKILL.md).
- A rival beyond its X feed: [competitor-intel](https://github.com/Marqentic/marketing-skills/blob/main/skills/competitor-intel/SKILL.md). Ads on X: [paid-ads](https://github.com/Marqentic/marketing-skills/blob/main/skills/paid-ads/SKILL.md). Which channels to bet on, and turning one piece into many: [growth-strategy](https://github.com/Marqentic/marketing-skills/blob/main/skills/growth-strategy/SKILL.md). How AI engines name brands: [ai-search](https://github.com/Marqentic/marketing-skills/blob/main/skills/ai-search/SKILL.md).
