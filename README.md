# proxy services: how to pick one without overpaying — per-IP vs per-GB billing, what's actually included, and where the fine print bites

Search for proxy services and you get ten listicles telling you ten different companies are the market leader. None of them tell you the thing that actually decides your bill, which is not the brand name at all. It's the billing model. Per-IP and per-GB are two different products wearing the same word, and picking the wrong one is how people end up paying three times what they needed to for the same amount of work.

So let's do this properly. Below I'll use 9Proxy as the working example, because it's a residential-only provider with public tier pricing and a genuinely unusual model — unlimited bandwidth per IP. That makes it a good teaching case. Everything concrete here comes from its published documentation, its pricing page, and third-party reviews; where a number is a company claim rather than an independent measurement, I'll say so.

## The question to answer before you compare anything

There are really only four questions that matter:

1. **Do you need sticky sessions or high rotation?** Logging into the same account repeatedly wants the same IP. Scraping ten thousand product pages wants a new IP every request. These are opposite requirements and they map onto different billing models.
2. **Is your workload bandwidth-heavy or request-heavy?** Downloading video-ish payloads, large files, or running a headless browser through the proxy burns data fast. Hitting an API endpoint a million times burns almost none.
3. **How predictable is your monthly volume?** Subscriptions reward predictability. Balance-based top-ups reward the opposite.
4. **What does failure cost you?** If a dead IP means a retry, fine. If it means a broken account, you need replacement speed and session stability, and you should pay for it.

Answer those, and the shortlist mostly builds itself. Skip them, and you'll be comparing per-GB prices against per-IP prices as though they're the same number, which is like comparing rent to electricity.

## What you're actually buying when you buy proxy services

The word "proxy" covers at least four products that behave nothing alike:

- **Residential** — IPs from real home connections. Slowest of the four in absolute terms, hardest to detect, most expensive per unit. This is what almost every scraping, ad-verification, and multi-account workflow actually needs.
- **Datacenter** — IPs from cloud infrastructure. Fast, cheap, and flagged by a lot of targets within minutes. Fine for bulk jobs against soft targets.
- **ISP (static residential)** — datacenter-hosted IPs registered to an ISP. Sits between the two; good when a session has to survive for weeks.
- **Mobile** — carrier IPs. Highest trust, highest price, often sold by the day.

9Proxy only sells residential. No datacenter, ISP, or mobile product line, and its documentation describes exactly two models: residential by IP and residential by GB. A datacenter product is listed as upcoming on some coupon and directory pages, but it isn't something you can buy today.

The other thing worth knowing: advertised pool size is close to meaningless as a purchase signal. Independent directories reviewing 9Proxy note that public figures for the same company range from roughly 9 million IPs to 95 million, depending on which promotional page you land on, with the most consistently corroborated number being about 20 million residential IPs across 90-plus countries. That's a normal amount of noise in this industry. Treat pool numbers as directional, and test against your own targets instead.

## Per-IP vs per-GB: the billing question that decides your budget

This is the fork in the road, and 9Proxy happens to spell out the tradeoffs in its own docs more clearly than most.

**Residential by IP** — you buy a fixed number of IPs. Each one carries unlimited traffic while it's alive. IPs you haven't used don't expire, so buying a block of 5,000 and burning through 200 a week is a legitimate strategy rather than a waste. The catch is lifespan: an individual residential IP stays usable for a few hours up to around 24 hours, and it does not naturally rotate. If you want rotation here, you configure it yourself on selected ports through the desktop app.

**Residential by GB** — you buy traffic. Endpoints are unlimited; bandwidth is not. You generate as many proxy endpoints as you want from the dashboard, choose sticky or rotating sessions per request, and only the gigabytes you consume come off your balance. Your balance is valid for 180 days, or indefinitely on the enterprise tiers.

The practical translation:

| Your workflow | Better fit |
| --- | --- |
| Same account, many requests, unpredictable data volume | Per-IP |
| Scraping with a new IP every request, small payloads | Per-GB |
| Streaming, large file transfers, headless-browser automation | Per-IP (unlimited traffic absorbs it) |
| Short bursty jobs you run twice a month | Per-GB (nothing expires on a clock you're not using) |
| Long-lived sessions you want to hold for a day | Per-IP |
| Wide geo-coverage across many countries in one job | Per-GB |

One structural difference that catches people out: the two models authenticate differently. GB-based proxies work straight from the dashboard with username/password or an IP whitelist. IP-based proxies require 9Proxy's desktop app for local port forwarding, with optional proxy authentication on top. If you're deploying to a headless Linux box with no desktop, that matters before you buy, not after.

## What a residential proxy service costs right now

9Proxy raised prices on its IP-based and bundle packages for the first time on June 1, 2026, and left GB-based packages untouched. The table below reflects pricing after that adjustment. There are no subscriptions or monthly renewals — every option is a one-time top-up onto a balance, which is why the "billing cycle" column says one-time rather than monthly.

| Plan | Model | Price | Effective rate | Validity | Buy |
| --- | --- | --- | --- | --- | --- |
| 100 IPs | Residential by IP | $24 | $0.240/IP | No expiry until used | Buy the 100 IP package |
| 500 IPs | Residential by IP | $72 | $0.144/IP | No expiry until used | Buy 500 residential IPs |
| 1,000 IPs + 500 bonus | Residential by IP | $126 | $0.084/IP | No expiry until used | Buy the 1,000 IP package with 500 free IPs |
| 2,500 IPs | Residential by IP | $210 | $0.084/IP | No expiry until used | Buy 2,500 residential IPs |
| 5,000 IPs | Residential by IP | $360 | $0.072/IP | No expiry until used | Buy 5,000 residential IPs |
| 15,000 IPs | Residential by IP | $720 | $0.048/IP | No expiry until used | Buy 15,000 residential IPs |
| 25,000 IPs | Residential by IP | $863 | $0.035/IP | No expiry until used | Buy 25,000 residential IPs |
| 50,000 IPs | Residential by IP | $1,438 | $0.029/IP | No expiry until used | Buy 50,000 residential IPs |
| 100,000 IPs | Business IP | $2,300 | $0.023/IP | No expiry until used | Request the 100,000 IP business package |
| 200,000 IPs | Business IP | $4,140 | $0.021/IP | No expiry until used | Request the 200,000 IP business package |
| 500,000 IPs | Business IP | $8,625 | $0.018/IP | No expiry until used | Request the 500,000 IP business package |
| 5 GB | Residential by GB | $15 | $3.00/GB | 180 days | Buy a 5 GB test package |
| 50 GB + 5 GB bonus | Residential by GB | $105 | $2.10/GB | 180 days | Buy the 50 GB package with 5 GB free |
| 100 GB | Residential by GB | $150 | $1.50/GB | 180 days | Buy 100 GB of residential traffic |
| 200 GB | Residential by GB | $200 | $1.00/GB | 180 days | Buy 200 GB of residential traffic |
| 1,000 GB | Residential by GB | $800 | $0.80/GB | 180 days | Buy 1,000 GB of residential traffic |
| 2,000 GB | Residential by GB | $1,500 | $0.75/GB | 180 days | Buy 2,000 GB of residential traffic |
| 3,000 GB | Enterprise GB | $2,160 | $0.72/GB | Unlimited | Request the 3,000 GB enterprise package |
| 6,000 GB | Enterprise GB | $4,200 | $0.70/GB | Unlimited | Request the 6,000 GB enterprise package |
| 10,000 GB | Enterprise GB | $6,800 | $0.68/GB | Unlimited | Request the 10,000 GB enterprise package |
| Starter Bundle | 100 IPs + 5 GB | $30 | Bundle | 180 days on traffic | Buy the Starter bundle |
| Popular Bundle | 1,500 IPs + 50 GB | $180 | Bundle | 180 days on traffic | Buy the Popular bundle |
| Pro Bundle | 5,000 IPs + 500 GB | $720 | Bundle | 180 days on traffic | Buy the Pro bundle |

Where the entry point lands in context: the cheapest per-IP rate is $0.018 and the cheapest per-GB rate is $0.68, both at the top of the volume curve. Enterprise providers in this space typically quote $8 to $12 per GB at low volumes, so a sub-$1 per GB rate isn't a rounding error — it's a different business model, and the tradeoff is that you get residential IPs and nothing else. No unblocker API, no managed scraping product, no browser automation platform.

## Where the fine print actually bites

This is the part listicles skip, and it's the part that determines whether the low rate is real value or a trap.

**There is no advertised refund.** 9Proxy's position is that the service is intangible, so purchases are non-refundable. What you get instead is a replacement mechanism: if a proxy isn't working, you check it in the "Today" list within 60 seconds and a replacement is credited. That's a genuine fix for dead IPs. It is not a fix for "this provider doesn't work for my use case," and independent directories flag the gap between those two things as the most common source of negative reviews on its Trustpilot profile. If your use case is unusual, validate it on the smallest package that makes sense.

**The free trial exists but isn't advertised.** Multiple sources describe a limited trial for new users, subject to availability, requested by contacting support or through the provider's forum threads — with different figures quoted depending on when and where the offer ran. Treat it as "ask and see," not as a published entitlement.

**IP lifespan is short by design.** A few hours to about 24 hours per IP is normal for residential, but it means you're buying a rotating inventory, not a permanent address. Budget for replacement, not just for quantity.

**Streaming is reportedly off the table on IP-based plans.** Third-party reviews note an acceptable-use update restricting media streaming on IP plans. If streaming is the reason you're shopping, confirm terms before paying.

**Performance numbers come in two flavours.** The vendor publishes roughly 99.5% success rate, ~0.6 second average response time, and 99.95% uptime. An independent directory that aggregates test data and published specs lists 9Proxy at 97% success rate with 1.3 second P95 latency. Both are plausible and neither is catastrophic — but read vendor figures as marketing and the independent number as the one to plan against.

**There's a coverage caveat worth knowing.** At least one third-party tracker reported a service-wide outage at the end of June 2026, and coverage of the provider's current status varies between directories. Whether that was an infrastructure failure or something else hasn't been publicly confirmed. The practical conclusion isn't "avoid it" — it's "don't top up a six-figure balance to a provider whose uptime you haven't personally observed."

## What it takes to get running

Setup cost is real, and it's where per-IP and per-GB diverge most.

For **GB-based proxies**, you sign in to the dashboard, generate endpoints, pick a location down to country, state, city, ZIP, or ISP, choose sticky or rotating sessions, and authenticate with credentials or an IP whitelist. Ten minutes, mostly waiting for the page to load.

For **IP-based proxies**, install the desktop client. It forwards traffic at the OS layer, which is the reason it works with software that has no proxy settings of its own. Ports are grouped per project, and auto-rotation can be scheduled at custom intervals on selected ports.

Beyond that, there's a browser-based tool for generating and routing proxies without a local install, a separate app for managing mobile devices, and a public API covering proxy generation, rotation, balance checks, and sub-user management, documented at the provider's docs subdomain.

Integration support is the usual crowd: HTTP/HTTPS and SOCKS5, so anti-detect browsers, `proxychains`, Scrapy, and custom scripts all work without protocol conversion.

## Who should use it, and who shouldn't

**Good fit:** teams running scraping or monitoring pipelines where bandwidth is the unpredictable variable and IP count is the predictable one. Agencies juggling several client accounts that each need a stable identity. Anyone doing ad verification or local SERP checks across cities. Solo operators who want to buy once and draw down a balance over 180 days rather than fight a renewal date.

**Poor fit:** enterprise data teams that need a managed unblocker, an enterprise SLA, or datacenter and mobile options under one contract. Anyone whose target requires mobile carrier IPs. Anyone who needs a documented refund path rather than a replacement credit. Streaming-first users.

## FAQ

**Are proxy services legal?**
Using a proxy is legal in most jurisdictions. What varies is the legality of what you do through it — scraping is governed by the target site's terms of service, data protection law, and local regulation. Providers generally publish acceptable-use policies precisely because the tool is neutral and the use case isn't.

**What's the difference between a proxy service and a VPN?**
A VPN routes all your traffic through one connection for privacy. A proxy service gives you many selectable exit points, which is what you need for geo-targeted data collection or keeping multiple accounts on separate network identities.

**How much should proxy services cost?**
Residential bandwidth runs from under $1 per GB at high volume to $10-plus per GB at enterprise providers with smaller commitments. Residential IPs run from roughly $0.02 to $0.25 each depending on quantity and lifespan.

**Do these providers offer free trials?**
Most offer something — a trial on request, a small credit, or a money-back window. 9Proxy's is limited and availability-dependent, so plan on buying the smallest package if a trial isn't available when you ask.

**Is residential always worth the premium over datacenter?**
No. If your targets don't have serious bot defenses, datacenter proxies will be faster and far cheaper. Residential earns its price when datacenter ranges are being blocked.

If you want to see how the numbers above land against your own workload, 👉 start with the 5 GB package and measure actual consumption before committing to a volume tier — it's $15, and it will tell you more than any review will.
