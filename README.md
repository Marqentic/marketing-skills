# MARqentic: marketing skills and live research for AI assistants

**Research your market, understand your audience and plan your next move with live data.** MARqentic connects your assistant to SEO, AI-answer visibility, public social research, Google Maps, Google ad-library research, app stores, Amazon and Google Shopping.

This repository contains **26 marketing skills** and their supporting references. The skills provide research methods, dated evidence and workflows; the hosted MCP server supplies live data when you authorize a connection.

```text
https://devshine-seo-mcp-e36n.vercel.app/mcp
```

The server uses remote Streamable HTTP with browser OAuth or a scoped workspace API key. You do not need to run the MARqentic backend locally.

[Quick start](#quick-start) · [Connect your assistant](#connect-your-assistant) · [Example prompts](#ask-it-like-this) · [All skills](#the-skills) · [Credits](#credits-and-budgets) · [Troubleshooting](#troubleshooting)

## Quick start

### Step 1: Install the marketing skills

In a terminal, run:

```sh
npx skills add Marqentic/marketing-skills
```

Select your assistant and the skills you want when prompted. Run the command in your project for a project installation. To install only SEO, or install for your user account:

```sh
npx skills add Marqentic/marketing-skills --skill seo
npx skills add Marqentic/marketing-skills -g
```

You need Node.js and npm compatible with the [skills installer](https://github.com/vercel-labs/skills). This command installs skill files; the MCP connection is configured separately in the next step.

### Step 2: Add the MARqentic MCP server

For Claude Code, run this in your terminal:

```sh
claude mcp add --transport http marqentic https://devshine-seo-mcp-e36n.vercel.app/mcp
```

Then open Claude Code and run:

```text
/mcp
```

Select MARqentic and start authorization. Other assistants have their own setup steps under [Connect your assistant](#connect-your-assistant).

### Step 3: Sign in and authorize your workspace

1. Follow the sign-in link opened by your assistant.
2. Sign in to MARqentic, or create an account through the sign-in flow. Complete email verification if requested.
3. Review the requesting client and callback address.
4. Choose the workspace whose data and credits the assistant should use.
5. Approve the requested permissions and return to your assistant.

The server exposes `tools:read` and `tools:execute` scopes. Execution permission requires an owner or administrator of the workspace. Connecting the research server does not authorize posting to a social account.

### Step 4: Set up your business context

In Claude Code, run:

```text
/manifold-get-started
```

Or ask your assistant:

> Use the manifold-get-started skill to set up marketing context for my business. My website is https://example.com. Ask me for anything you cannot determine from the site, then recommend the first two skills to use.

The skill writes `.agents/product-marketing.md` with your offer, customers, positioning, competitors and goals. The other skills read this shared context. If your assistant cannot write files, it can give you the Markdown to save yourself.

The name `manifold-get-started` is retained from the upstream library for compatibility. It is the getting-started skill for this MARqentic distribution.

### Step 5: Check the connection and run your first research task

Start with discovery:

> Show the available MARqentic tool categories using catalog_list_categories. Do not run paid research yet.

Then try:

> Use the SEO skill to find keyword opportunities for my website in my target market. First show your proposed calls and any supported dry-run estimates. Ask me for a credit budget before executing paid research.

New customer workspaces start with **zero credits**. Add credits through your workspace's available billing flow before paid research. A working connection can still reject a paid call when the balance is insufficient.

## Connect your assistant

Install the skills with `npx skills add Marqentic/marketing-skills` wherever your assistant supports the installer. Hosted chat clients can connect to the MCP server without installing local skill files; follow their supported skill-upload workflow separately if you also want the skills.

| Client | Add the server | Authorize |
|--------|----------------|-----------|
| Claude Code | Use the command in [Step 2](#step-2-add-the-marqentic-mcp-server). | Run `/mcp`, select MARqentic and follow browser sign-in. |
| Claude web or desktop | Where custom connectors are available, open Settings → Connectors, add a custom connector named MARqentic and paste the MCP URL. | Choose Connect and complete browser sign-in. Availability can depend on your plan and organization settings. |
| ChatGPT | Where your account permits custom MCP servers, use the setup below. | Choose OAuth and complete MARqentic sign-in. |
| Codex | Use the commands below. | Run `codex mcp login marqentic` and complete browser sign-in. |
| Cursor | Add the JSON configuration below to your MCP settings. | Enable the server and follow its authorization prompt. |
| Gemini CLI | Use the command below. | Inside Gemini CLI, run `/mcp auth marqentic`. |
| Other MCP clients | Add the URL as a remote Streamable HTTP server. | Use the client's OAuth flow, or its private bearer-header configuration for a workspace API key. |

### ChatGPT

1. In a ChatGPT account or workspace that permits custom MCP servers, choose **Add custom MCP server**. Your administrator may need to enable access.
2. Name the connection **MARqentic** and enter `https://devshine-seo-mcp-e36n.vercel.app/mcp`.
3. Choose **OAuth**, create the connection and complete MARqentic sign-in and workspace consent.
4. Enable the connection for your conversation and ask it to list the available research categories before running paid calls.

This is a custom connection; this repository does not claim a published MARqentic directory listing. See the [official custom MCP server guide](https://developers.openai.com/api/docs/guides/custom-mcp-server) for the setup available to your account.

### Codex

In your terminal:

```sh
codex mcp add marqentic --url https://devshine-seo-mcp-e36n.vercel.app/mcp
codex mcp login marqentic
```

Install the skills with the quick-start command and select Codex. After installation, ask it to use `manifold-get-started` for your business. See the [official Codex MCP documentation](https://learn.chatgpt.com/docs/extend/mcp?surface=cli).

### Cursor

Merge this entry into `.cursor/mcp.json` in your project, or `~/.cursor/mcp.json` for all projects. Preserve any existing servers:

```json
{
  "mcpServers": {
    "marqentic": {
      "url": "https://devshine-seo-mcp-e36n.vercel.app/mcp"
    }
  }
}
```

Open Cursor's MCP settings, enable MARqentic and complete authorization. Install the skills with the quick-start command and select Cursor. See the [official Cursor MCP documentation](https://prod.cursor.com/docs/mcp).

### Gemini CLI

In your terminal:

```sh
gemini mcp add --transport http marqentic https://devshine-seo-mcp-e36n.vercel.app/mcp
```

Inside Gemini CLI:

```text
/mcp auth marqentic
```

Install the skills with the quick-start command if your installed skills CLI supports your Gemini setup. See the [official Gemini CLI MCP documentation](https://geminicli.com/docs/tools/mcp-server/).

### API-key connection

Clients that support custom HTTP headers can use a scoped workspace API key as `Authorization: Bearer <your-workspace-key>`. Store the key in the client's private credential configuration. Do not commit it to MCP JSON files or put it in a URL, skill file or chat prompt. See [connection and availability](CONNECTING.md).

This release uses the skills installer and manual MCP connection. It does not include Claude marketplace plugin manifests or a Gemini extension manifest. Manifold's plugin-install commands do not install MARqentic. For Claude Code configuration details, see the [official MCP documentation](https://code.claude.com/docs/en/mcp).

## Ask it like this

Describe the outcome you want, or ask for a skill by name. Skill selection depends on your assistant's support for installed skills.

| You ask | Skills to use |
|---------|---------------|
| “Find search opportunities for our site and prioritize content we can realistically rank for.” | `seo`, `technical-seo` |
| “Do AI answers mention our brand for these buying questions? Which sources do they cite?” | `ai-search` |
| “Find creators in our niche and compare their public videos and engagement.” | `creators`, `tiktok`, `instagram`, `youtube` |
| “What do people on Reddit complain about in our category?” | `reddit`, `voice-of-customer` |
| “Research this advertiser's Google ads and suggest creative angles.” | `paid-ads` |
| “Who appears for this local search, and how do our competitors' profiles compare?” | `local-seo` |
| “Compare competing apps' reviews and turn the complaints into positioning ideas.” | `app-store`, `competitor-intel` |
| “Use our customer research to propose a launch plan with a clear research budget.” | `growth-strategy`, `market-research` |

## What your assistant can research

| Area | Supported research |
|------|--------------------|
| SEO | Keyword ideas and metrics, search results, rankings, domain research, backlinks and supported site analysis. |
| AI answers | Supported AI-answer visibility, named brands, citations and readiness research. |
| Public social | Supported public accounts, posts, comments and video research across Reddit, TikTok, Instagram, YouTube, Facebook and LinkedIn. Fields and transcript coverage depend on the source and provider. |
| Google Maps | Local search, businesses and profile research. |
| Google ad library | Advertiser search, advertiser ads and individual ad details. |
| Commerce and apps | Supported Amazon, Google Shopping, App Store and Google Play research. |

Use MCP tool discovery and `catalog_list_categories` to confirm what your connected deployment exposes. The live tool schemas take priority over examples and reference prices in skill prose.

Search Console, Bing Webmaster Tools, Google Analytics, verified lead enrichment and X tool families are not implemented in this distribution's documented coverage. Their skills still provide research guidance and manual alternatives. Ad-library support currently covers Google; other ad platforms, keyword-based ad search and Google creative-text enrichment are not implemented. TikTok audience information and LinkedIn commenters are samples.

## The skills

All 26 skills are independently installable. These descriptions explain the workflows; live tool coverage is listed above.

### Start here

| Skill | Use it for |
|-------|------------|
| [manifold-get-started](skills/manifold-get-started/SKILL.md) | Save shared business context and choose the first workflows for your goals. |

### Search, AI visibility and authority

| Skill | Use it for |
|-------|------------|
| [seo](skills/seo/SKILL.md) | Keyword research, content opportunities, briefs and organic search planning. |
| [technical-seo](skills/technical-seo/SKILL.md) | Crawlability, indexing, site health, traffic-drop investigation and migrations. |
| [ai-search](skills/ai-search/SKILL.md) | Brand mentions, citations and visibility in AI-generated answers. |
| [link-building](skills/link-building/SKILL.md) | Backlink opportunities, lost links and authority-building research. |
| [digital-pr](skills/digital-pr/SKILL.md) | Story ideas, coverage opportunities and evidence-based outreach planning. |

### Social, communities and creators

| Skill | Use it for |
|-------|------------|
| [tiktok](skills/tiktok/SKILL.md) | Public video, account, hook and trend research. |
| [instagram](skills/instagram/SKILL.md) | Reels, posts, profiles and audience-response research. |
| [youtube](skills/youtube/SKILL.md) | Channels, video ideas, comments and supported transcript research. |
| [linkedin](skills/linkedin/SKILL.md) | Public professional content, company positioning and discussion research. |
| [facebook](skills/facebook/SKILL.md) | Public page and community research where the provider supports it. |
| [x-twitter](skills/x-twitter/SKILL.md) | X content strategy and manual account research; live X tools are unavailable. |
| [reddit](skills/reddit/SKILL.md) | Communities, threads, customer problems and participation planning. |
| [creators](skills/creators/SKILL.md) | Creator discovery, vetting, campaign briefs and partnership planning. |

### Local, commerce and apps

| Skill | Use it for |
|-------|------------|
| [local-seo](skills/local-seo/SKILL.md) | Local search, Maps visibility and Business Profile comparison. |
| [amazon](skills/amazon/SKILL.md) | Listings, products, competitors and marketplace research. |
| [google-shopping](skills/google-shopping/SKILL.md) | Shopping results, product comparisons and feed strategy. |
| [app-store](skills/app-store/SKILL.md) | App listings, reviews, competitors and store positioning. |

### Advertising and outreach

| Skill | Use it for |
|-------|------------|
| [paid-ads](skills/paid-ads/SKILL.md) | Ad strategy and competitor creative research, with live Google ad-library coverage. |
| [outbound](skills/outbound/SKILL.md) | Account research, messaging and outreach planning using manual alternatives for unavailable lead tools. |

### Research, strategy and reporting

| Skill | Use it for |
|-------|------------|
| [voice-of-customer](skills/voice-of-customer/SKILL.md) | Turn customer language into pain points, objections and positioning. |
| [market-research](skills/market-research/SKILL.md) | Demand checks, category research and market-entry questions. |
| [competitor-intel](skills/competitor-intel/SKILL.md) | Competitor comparisons, monitoring and evidence-backed battlecards. |
| [growth-strategy](skills/growth-strategy/SKILL.md) | Channel priorities, launch plans and marketing experiments. |
| [brand-monitoring](skills/brand-monitoring/SKILL.md) | Brand mentions, awareness signals and monitoring plans. |
| [agency](skills/agency/SKILL.md) | Client onboarding, prospect research and recurring reports. |

## Credits and budgets

- Installing and reading these MIT-licensed skills does not purchase server credits.
- New customer workspaces begin with zero credits. Check your workspace balance before paid research.
- Ask for a supported `dry_run: true` quote before paid execution. The connected tool's schema and quote determine the cost.
- Agree on a total research budget and use supported `max_credits` limits for each call. A per-call cap does not enforce a total budget across multiple calls; the assistant must track spending.
- Prices and operational notes imported with the skills describe their upstream revision. Confirm live prices instead of treating those reference figures as a current MARqentic price list.

## What gets installed and sent

This repository distributes Markdown skills, supporting research references, license notices and provenance. The package contains no backend source, credentials, executable hooks or automatic connector configuration. Running `npx skills add` executes the external skills installer to place these files in your chosen assistant's skill directory.

When connected, the assistant sends MCP requests to the MARqentic URL above. Research parameters can include domains, URLs, keywords, AI prompts, public handles, post URLs and subreddit names. The server may forward parameters to the providers needed for that research. SEO research uses DataForSEO underneath the MARqentic tools.

Only send data appropriate to the task and your workspace. Review the deployed service's privacy terms before supplying confidential inputs. This README does not promise a retention period or provider policy that has not been verified for the deployment.

Installing the skills does not grant permission to post, comment, message or manage a social account. Any supported connected-account action needs its own account connection, tool permissions and your explicit instruction.

## Troubleshooting

| Problem | What to check |
|---------|---------------|
| Skills installed, but no MARqentic tools appear | Add the MCP server separately, complete OAuth, enable it in the client and start a new session if the client requires it. |
| Skills do not appear | Re-run the installer for the correct assistant and project/global scope; confirm that your client supports the Agent Skills format. |
| Opening `/mcp` in a browser shows `401 Unauthorized` | This is expected without authentication. Add the URL through an MCP client and complete its OAuth flow. |
| Sign-in succeeds, but execution is denied | Check workspace selection, email verification, requested scopes and your owner/admin role. Reauthorize if permissions changed. |
| A paid call reports insufficient credits | Check the selected workspace balance and its billing options. Successful OAuth does not add credits. |
| A workflow names an unavailable tool | Check tool discovery and [connection and availability](CONNECTING.md), then use the skill's manual fallback. Do not invent results. |
| A call returns missing fields or no transcript | Coverage depends on the source and provider. Mark unavailable fields clearly and distinguish missing data from measured zero. |
| The client cannot connect | Confirm the full HTTPS URL ends in `/mcp`, use Streamable HTTP and check client/admin restrictions. Include a redacted error when reporting the issue. |

## Updates and feedback

Re-run the installer to select the current published skills, or use its [documented update workflow](https://github.com/vercel-labs/skills). Skill updates do not replace your separate MCP authorization.

Report bugs and request workflows through [GitHub issues](https://github.com/Marqentic/marketing-skills/issues). Include the client, skill, expected behavior and a redacted error; never include access tokens or workspace keys.

The canonical library and release templates live in the MARqentic application repository. This repository is generated from that source. Changes should be made at the source and exported, validated and reviewed before publication so they survive later releases.

## Attribution and license

Adapted from [Manifold marketing-skills](https://github.com/manifoldmcp/marketing-skills) under the MIT license. Original skill identifiers, source citations and research attribution are preserved. Findings credited to Manifold remain Manifold's findings; they were not re-measured by MARqentic. MARqentic is an independent adaptation.

See [LICENSE](LICENSE), [NOTICE](NOTICE.md) and the pinned revision in [UPSTREAM.json](UPSTREAM.json).
