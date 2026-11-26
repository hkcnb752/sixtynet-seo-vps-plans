# SEO VPS: Which SixtyNet Plan Fits GSA, Scrapebox or Screaming Frog, What Do Residential IPs Change, and What Do the Closed Ports Rule Out? (Full Price Table)

SixtyNet's cheapest plan that can run SEO tooling is LAX-STARTER: 2 cores, 2 GB RAM, 40 GB NVMe and 5 TB of traffic for **$200 a year**, discounted from a $240 list price. The reason to pick this host over a $3-a-month box is the IP address, not the hardware. The Residential and Irvine Pro lines sit on real ISP ranges rather than datacenter ranges, and that changes which jobs succeed. The reason to skip it is printed on the same page: those residential plans do not open ports 80 and 443, so you cannot serve a website from them.

Everything below comes from SixtyNet's own plan page and from third-party tests of the residential boxes. You get the full price table, a sizing rule for the three tools most people run, the terms that change your total cost, and the cases where a cheaper datacenter VPS is the better buy.

> **Quick pick:** running one Scrapebox instance or a rank tracker, LAX-STARTER at **$200/year** (list $240) is enough, with 2 cores, 2 GB RAM and 5 TB of traffic. Running GSA or a multi-tool stack, start at the 8-core tier and ask support whether the core count is a guaranteed allocation before you pay.
> 👉 [See SixtyNet's current plan list and prices](https://sixtynet.net/aff.php?aff=39)

## SixtyNet's full plan lineup

| Plan | Cores / RAM | Storage | Traffic | Price (USD, billed annually) | Order |
| --- | --- | --- | --- | --- | --- |
| LAX-STARTER | 2 / 2 GB | 40 GB NVMe | 5 TB | **$200** (list $240) | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 / 4 GB | 80 GB NVMe | 10 TB | **$400** (list $480) | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 / 8 GB | 160 GB NVMe | 20 TB | **$800** (list $960) | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 / 16 GB | 320 GB NVMe | 40 TB | **$1,600** (list $1,920) | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-Storage-500G | 4 / 4 GB | 300 GB + 200 GB bonus, RAID 10 | 10 TB | **$400** (list $480) | [Order](https://sixtynet.net/aff.php?aff=39) |
| LAX-Storage-1TB | 8 / 8 GB | 700 GB + 300 GB bonus, RAID 10 | 15 TB | **$700** (list $840) | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-STARTER | 2 / 2 GB | 40 GB NVMe | 5 TB | **$260** (list $300) | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-MICRO | 4 / 4 GB | 80 GB NVMe | 10 TB | **$460** (list $540) | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential, 8-core tier | 8 / 8 GB | 160 GB NVMe | 20 TB | — | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-LARGE | 16 / 16 GB | 320 GB NVMe | 40 TB | **$1,660** (list $1,980) | [Order](https://sixtynet.net/aff.php?aff=39) |
| IRVINE-PRO-STARTER | 2 / 2 GB | 40 GB NVMe | 5 TB | **$350** (list $420) | [Order](https://sixtynet.net/aff.php?aff=39) |
| Irvine Pro, 4-core tier | 4 / 4 GB | 80 GB NVMe | 10 TB | — | [Order](https://sixtynet.net/aff.php?aff=39) |
| Los Angeles China Unicom-Premium | not listed | not listed | 100M port, 3× burst, 95th percentile | **$2,500** (list $3,000) | [Order](https://sixtynet.net/aff.php?aff=39) |

Two caveats about the numbers. Every price on the page is annual, labelled "Annually", so the monthly figures in this article are the annual price divided by twelve, not a monthly billing option I could confirm. The 8-core residential and 4-core Irvine Pro configs appeared with full specs but no price in the pricing data available, so confirm those two on the order page. The China Unicom plan is a BGP and bandwidth product for China routes (AS9929, 95th percentile billing), not a tool box.

## What the residential label buys you, and what the closed ports take away

SixtyNet sells three families at nearly identical specs, and the difference is the IP. LAX plans list DDoS protection and no residential label. Residential plans list a residential IP and a notice that ports 80 and 443 stay closed "due to IP risk control". Irvine Pro plans add AS9929 China routing to the residential IP, close the same ports, and add a second restriction: the box rejects external probes and scans, and only whitelisted or port-forwarded devices can reach it.

Residential IPs matter when the target decides whether to answer based on where you're coming from. Datacenter ranges are easy to identify and easy to block; a residential address looks like home broadband. Two 2025 tests of SixtyNet's residential boxes found Cox Communications and Astound Broadband as the upstream carriers, native US IPv4, and strong streaming-unlock results. The same tests measured an AMD EPYC 7002-series CPU, I/O around 178–188 MB/s, no IPv6, and ping blocked.

The closed ports define the job. With 80 and 443 shut, the box will not serve a website, a PBN node or an HTTP callback endpoint. What it does well is outbound work: crawling, harvesting, submitting, checking rankings, and logging into platforms that treat datacenter IPs as suspicious. If your plan involves hosting pages, this is the wrong product line. If your plan involves asking other servers for data, the residential address is the feature you're paying for.

## How much machine GSA, Scrapebox and Screaming Frog actually need

Tool vendors rarely publish requirements, so here is a yardstick worth reusing. A large Screaming Frog crawl of 500,000 URLs takes hours and several gigabytes of RAM, and RAM scales with URL count. GSA Search Engine Ranker holds every core at 100% for as long as it runs, which is the exact usage pattern that gets throttled on shared hardware. Scrapebox opens thousands of connections at once, so bandwidth matters more than CPU. Browser automation adds 200–500 MB of RAM per open browser on top of everything else.

| What you run | What it needs | Closest SixtyNet plan |
| --- | --- | --- |
| Scrapebox, one instance, or rank tracking | 2 cores, 4–8 GB comfortable; bandwidth is the limit | LAX-STARTER (2/2) for light harvesting, LAX-MICRO (4/4) for steady use |
| Screaming Frog, site audits | 2–4 cores, 8–16 GB; RAM tracks URL count | LAX-MICRO for audits under six figures, LAX-MEDIUM (8/8) above |
| GSA SER, or a link-building stack with a captcha solver | 4–8 cores, 8–16 GB, and CPU that stays yours | 8-core tier or higher; confirm the cores are reserved |
| Full stack: GSA, Scrapebox, Screaming Frog, Money Robot, RankerX | 12+ cores, 32 GB | Doesn't fit; the largest SixtyNet box is 16 cores and 16 GB |

That last row is the honest limit. The sizing yardstick from the Windows VPS side of this market puts a full agency stack at 12 cores and 32 GB. SixtyNet tops out at 16 GB of RAM, so you'd split the stack across two servers or move the heavy jobs elsewhere.

The other gap is the core guarantee. SixtyNet lists core counts but doesn't state whether those cores are dedicated or shared with other tenants. GSA is the tool that cares, because it pins the CPU for hours and shared allocation is what triggers throttling. Ask support before you buy the 8-core tier.

👉 [Check whether SixtyNet's 8-core plans fit a GSA workload](https://sixtynet.net/aff.php?aff=39)

## The costs the plan page leaves out

**Billing is annual.** The discount you see is off the annual list price, so the $200 LAX-STARTER entry is $200 up front, not $16.67 a month. Budget the year.

**Refunds are narrow on one line.** Irvine Pro plans state that refunds are issued as website balance only, not back to your payment method. On the rest of the range, refund terms aren't spelled out on the plan page, and a third-party overview of the brand cites a 3-day money-back window. Three days is short next to the 14 days Cloudzy advertises. Test the IP reputation in the first 48 hours if you buy.

**ISP choice can cost extra.** A 2025 review of the residential range noted that requesting a Cox Communications IP adds $5 per month. Confirm the current add-on price when you configure.

**Operating systems aren't listed.** The plan page doesn't say which OS images you get. That matters if your stack is Windows-only, which GSA is. For context on what Windows costs elsewhere in this market, one competitor installs Windows Server as a 180-day evaluation build, then charges $6.31 per vCPU per month for the licence, and shuts the server down hourly once the evaluation expires. Nothing like that appears in SixtyNet's plan lines, so ask what OS is available and whether a licence is included before assuming GSA will run.

**Traffic is generous, ports are not.** 5 TB on the entry plan is more than most scrapers use in a month. The constraint is the port policy, not the allowance.

## How the price compares with the usual SEO VPS crowd

| Provider | Entry price | Specs at entry | Billing and notes |
| --- | --- | --- | --- |
| SixtyNet (LAX-STARTER) | $200/yr, about $16.67/mo | 2 cores, 2 GB, 40 GB NVMe, 5 TB | Annual, discounted from $240 |
| Cloudzy | $2.48/mo | 1 vCPU, 512 MB, 20 GB NVMe, 1 TB | Hourly to annual, 14-day money-back, dedicated IPv4 |
| LightNode | $7.71/mo | 1 vCPU, 2 GB, 50 GB NVMe, 1 TB | Hourly billing, 40+ locations claimed |
| MassiveGRID | $3.99/mo shared cores | Windows, RDP | Reserved cores from $18.84/mo, Windows licence $6.31/vCPU/mo after 180 days |

Read that table as four different products. The datacenter providers win on price per gigabyte of RAM by a wide margin, and their entry plans are meant for one crawler on a small site. SixtyNet's entry box costs roughly two to seven times more per month for similar or smaller specs, and the premium buys a residential address, larger NVMe volumes and multi-terabyte traffic. LightNode's own page lists same-spec references of about $10/mo at Vultr and $12/mo at DigitalOcean for 1 vCPU and 2 GB, which shows how much of the spread between providers comes from spec details rather than margin.

None of these comparisons settle which host is better. They settle what you're paying for. If IP reputation is irrelevant to your job, you're overpaying at SixtyNet. If it's the whole point, the $3 boxes can't do the work at any price.

## Who should not buy this

You need to host sites, landing pages or a PBN. Ports 80 and 443 are closed on every residential and Irvine Pro plan. Rent a normal VPS.

You need 32 GB of RAM on one box. The range stops at 16 GB.

You want to pay monthly while testing. The published prices are annual, and a year is a long commitment to a host you haven't tried.

You're crawling your own site for technical audits and nobody is blocking your IP. A $3–8 datacenter VPS handles Screaming Frog on a mid-size site without trouble.

## FAQ

**Is a SixtyNet VPS a replacement for a normal web host?**
No. Residential and Irvine Pro plans keep ports 80 and 443 closed, so you can't serve a standard website. LAX plans don't carry the port notice, but confirm before you assume they're open.

**How many cores does GSA Search Engine Ranker need?**
Four at minimum, and 8 cores with 8–16 GB is the realistic target for a stack that includes a captcha solver. GSA holds the CPU at 100% while it runs, so the core allocation matters more than the clock speed. Ask whether SixtyNet's cores are dedicated.

**Is 2 GB of RAM enough for SEO tools?**
For a single Scrapebox instance doing URL harvesting, yes. For Screaming Frog on a large site, no. Crawl memory grows with the number of URLs, and a 500,000-URL crawl needs several gigabytes on its own.

**Does the residential IP actually get treated differently?**
That's the premise of the product, and the 2025 tests found the boxes routing through consumer ISPs (Cox, Astound) with strong streaming-unlock results, which is a reasonable proxy for how platforms classify the address. It's not a guarantee that no site will ever block you.

**Can I get IPv6?**
The tested residential plans did not support IPv6. Assume IPv4 only unless support tells you otherwise.

## Which plan to order

Running a rank tracker, a single Scrapebox harvester or scheduled audits on modest sites: LAX-STARTER at $200/year. The 2 GB of RAM is the ceiling you'll hit first, not the 5 TB of traffic.

Running a link-building stack or anything that logs into platforms which block datacenter ranges: Residential-MICRO at $460/year for 4 cores and 4 GB, or the 8-core tier if you're also crawling. You're buying the IP, so the cheaper LAX line defeats the purpose for these jobs.

Running GSA around the clock: 8 cores or more, and a written answer from support on whether the cores are reserved.

Two things to confirm at checkout: whether your plan can be billed monthly, and what the refund window and refund method are, since Irvine Pro returns balance rather than cash. Then run the tool you actually care about in the first 48 hours and check whether your target sites answer the residential IP.

👉 [Compare SixtyNet's residential and LAX plans at current prices](https://sixtynet.net/aff.php?aff=39)
