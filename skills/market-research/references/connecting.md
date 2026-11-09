# Connecting the MARqentic server

These marketing skills work without an MCP connection using their documented research methods. Measuring live data requires a MARqentic deployment and an authorized workspace. Never invent measurements when tools or providers are unavailable.

## Connect

This skills release does not install or automatically connect an MCP server. Use the public MARqentic MCP endpoint:

```text
https://devshine-seo-mcp-e36n.vercel.app/mcp
```

In a remote MCP client, add that URL and begin browser OAuth. Sign in with MARqentic, review the requesting client, choose a workspace and approve the permissions. For clients that support a custom bearer header, a scoped workspace API key is an alternative. Never put a key in a URL, shared repository, skill file or ordinary chat message.

For Claude Code:

```sh
claude mcp add --transport http marqentic https://devshine-seo-mcp-e36n.vercel.app/mcp
```

Then run `/mcp` in Claude Code and authorize the connection. Hosted assistants need a publicly reachable HTTPS server. Other clients should use their remote Streamable HTTP setup. Installing skills and authorizing a connector are separate actions.

## What is built

MARqentic implements SEO, AI-answer research, Google Maps, Amazon, Google Shopping, app-store research and supported public social research. Tool discovery and the deployment's schemas take priority over any static table.

- Google ad-library research supports advertiser search, advertiser ads and individual ad details. Other ad platforms, keyword-based ad search and Google creative-text enrichment are not implemented.
- Social research supports public Instagram, TikTok, YouTube, Reddit, Facebook and LinkedIn inputs, subject to source/provider availability. Transcript coverage varies. TikTok audience information and LinkedIn commenters are samples.
- The `console_*`, `analytics_*`, `leads_*` and `twitter_*` families named in some upstream workflows are not implemented. Use the documented manual approach and identify what was not measured. Do not diagnose an unsupported family as a broken connection.
- Skills do not grant posting or messaging permissions. Connected-account actions require their own supported tool and explicit authorization.

Use the connected server's tool discovery or `catalog_list_categories` to confirm coverage. Skills name tools without host prefixes; a client may display a name such as `mcp__marqentic__seo_get_serp`.

## Credits

New customer workspaces begin with zero credits. Product-credit prices and provider availability belong to the deployment you connect to. A supported `dry_run: true` requests an estimate without paid execution. State the estimate before the first paid call and use `max_credits` for the user's budget.

Upstream skill files contain reference prices and operational notes from their imported revision. Confirm the live tool schema and quote before relying on those figures. Distinguish unavailable fields from a measured zero; retain dates, markets and source context.

## Attribution

The library is adapted from [Manifold marketing-skills](https://github.com/manifoldmcp/marketing-skills), originally distributed under the MIT license. The included LICENSE preserves the original copyright and permission notice. UPSTREAM.json records the imported revision.

“We”, “our runs”, field notes and findings credited to Manifold describe Manifold's research. They were not re-measured by MARqentic or the user's team. Preserve that attribution when using or quoting the evidence. MARqentic is an independent adaptation, not an endorsement or affiliation.
