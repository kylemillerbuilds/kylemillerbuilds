# Kyle Miller

I build software by directing AI agents rather than by typing it myself. That puts my work in
architecture, judgment, and verification, and the last one is where most of what I know came from.
Agents report success constantly while shipping work that is wrong, so nothing I run is trusted on
its own word.

I co-founded **Tritan**, a print-on-demand art brand selling on Shopify and Etsy, and I own the
technical side of it. I designed and operate the pipeline that generates the artwork, runs it
through automated quality gates, creates the products through the Printify API, assembles the
mockups, writes the listing SEO, and publishes to both channels.

**Themis Foundry LLC** is my own company. Its first product is Hermes, a retention platform for
independent insurance brokers that turns unstructured carrier documents into structured, queryable
client data. FastAPI and Alpine, built and pre-launch.

Before this I sold solar door to door and built an independent health insurance book from zero
clients. I handed the book off in August 2026 to build full time.

I am looking for a role on a small, early-stage team where building with AI agents is just how the
work gets done rather than something novel.

## Repos worth opening

Ordered by what they show, not by stars.

**[momus-agent-firewall](https://github.com/kylemillerbuilds/momus-agent-firewall)**
A deterministic scanner for AI-generated diffs. It came out of a payment address in one of my
own projects that carried a code comment asserting it was my verified wallet. It was not mine, and
the comment stood for five weeks past two reviews, because every check that looked at it read the
comment. When an agent later changed that address, my own audit called the change unauthorized and
published that — and I was wrong the second time too. Both halves of that episode produced a
confident, well-cited, wrong claim about who owned an address. So Momus checks values against an
allowlist a human maintains, never against the justification sitting next to them in the diff.

**[apollo-contract-scan](https://github.com/kylemillerbuilds/apollo-contract-scan)**
A pay-per-call Solidity risk scan that sells itself to other agents over x402 on Base. The
deployment holds no signing keys and no wallet, so it cannot custody or move money. It can only
receive. Read [GROWTH.md](https://github.com/kylemillerbuilds/apollo-contract-scan/blob/main/GROWTH.md)
before the code. It is the honest ledger for the project and it records the mistakes as carefully as
the milestones: the audit that concluded the service was never listed after reading page one of a
14,810 entry paginated index, and the on-chain sweep that reported zero transfers because the RPC
was quietly returning 403 and a positive control was the only thing that caught it.

**[agent-guardrails](https://github.com/kylemillerbuilds/agent-guardrails)**
The hook that sits between my agents and my working tree. Nine rules, each one added after
something broke, plus a regression matrix that has to run green before the guard is edited. Seven
fail open on purpose; two fail closed, because they face injection rather than my own clumsiness. A guard that can freeze a parallel session gets deleted within a week, and a
guard that only ever blocks explicit matched patterns gets to stay forever.

**[printify-publish-queue](https://github.com/kylemillerbuilds/printify-publish-queue)**
Printify's publish endpoint returns 200 immediately and then syncs later through a queue you cannot
see, which means a product that is merely slow and a product that has silently died look identical
for several minutes. Retrying is the natural move and it is what creates duplicate listings. This
encodes the difference, and the cost of learning it.

**[safe-url-fetch](https://github.com/kylemillerbuilds/safe-url-fetch)**
The guard I put in front of every server-side fetch of a URL that a person typed. Scheme allowlist,
every resolved IP checked against the private ranges, and redirects revalidated on each hop. The
tests run without touching the network.

**[pixel-sprite-animator](https://github.com/kylemillerbuilds/pixel-sprite-animator)**
One 32x32 idle sprite in, a complete animated character out, with zero AI at runtime. I built the
image-model version first and spent most of its code fighting identity drift. Replacing the model
with a rig read better, because at that resolution a walk cycle is small enough to describe exactly.

## The thing I keep relearning

A check that cannot say "I could not look" will say "pass."

I found that out on the pipeline above. Part of it decides which photo shows up as a product's main
image, and I had a verifier that pulled each product back down off the live site and compared the
image against what I meant to publish. It came back clean across four product lines. Then I opened a
real product page myself and saw a Christmas living room sitting behind a poster we sell year round.

The verifier was reading the same field the writer had just set, so it was really asking whether I
put a thing where I put it, and the answer was always going to be yes.

So I changed how checking works here. A check has to look at something different from whatever the
writer touched, ideally the thing the customer sees. It has to fail on purpose before I trust it,
because if I have never watched it turn red I do not know that it works. And it has to be able to
report "could not check" as its own answer, separate from "passed," because those two were being
treated the same and that is how the bad work got through.

Reach me at kyle@themisfoundry.com · [LinkedIn](https://linkedin.com/in/kylemillerfl)
