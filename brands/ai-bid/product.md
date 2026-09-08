# AI-Bid — Product Knowledge

## Verified identity

- Product: ai-bid.lol
- Core model: pay-to-rank public leaderboard and discovery platform
- Initial launch-base markets: AI + Games
- Primary mechanic: cumulative confirmed bid value determines product ranking within a market/category.

## Primary users

- Solo AI tool builders
- Small AI product teams
- Game makers and small game teams for the launch-base Games market
- Visitors discovering products through category boards, product pages, and social sharing

## Core capabilities implemented / documented

- Anonymous paid product submission
- All-time leaderboard
- Category boards
- Daily leaderboard with UTC reset
- Permanent product pages
- Bid history
- Live bid activity/ticker
- Product OG images
- Embeddable rank badge
- Outbound click tracking
- Public aggregate market stats
- Product reporting and moderation
- Dodo Payments checkout and signed webhook reconciliation
- Firestore-backed optimized logo storage
- SEO sitemap and robots metadata

## Payment trust model

A client-side success state is not authoritative. A product becomes live and a bid affects ranking only after verified payment webhook reconciliation. Checkout intents bind the server-derived product and USD bid amount, and webhook processing is idempotent.

## Launch-base scope

AI and Games are the initial launch base. Open Source and Music are post-launch expansion phases. Hermes must not invent or advertise dormant future-market listings.

## Marketing constraints

Never claim fabricated bid totals, users, traction, rankings, customer endorsements, payment volume, or competitive wins. Current production data and explicit product evidence must be checked before using quantitative claims.

## Evidence

Primary evidence currently comes from the AI-Bid repository PRD, README, and implementation-status documentation. Live production behavior is higher-priority evidence and must be revalidated before external publication.
