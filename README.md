# Hermes Marketing

Autonomous marketing intelligence and execution system for Kaif's products.

## Mission

Hermes acts as a product-aware growth operator. It researches markets and competitors, maintains verified product knowledge, plans campaigns, creates channel-specific content, measures results, and continuously improves strategy.

## Managed products

- **Keanso** — invoice follow-up workspace for freelancers and small businesses.
- **AI-Bid** — pay-to-rank discovery and visibility platform, with AI + Games as the initial launch base.

## Architecture principle

Product repositories remain independent. Hermes reads their current implementation, documentation, public production behavior, and approved metrics, then produces marketing decisions and execution artifacts from this dedicated repository.

Source priority for product truth:

1. Live production behavior
2. Current implementation
3. Current product documentation
4. Current PRD
5. Historical documentation

Never invent product capabilities, customers, traction, pricing, testimonials, or market activity.

## Initial system layers

```text
Product knowledge
      ↓
Market intelligence
      ↓
Strategic planning
      ↓
Content / campaign generation
      ↓
Approval or automated execution
      ↓
Measurement
      ↓
Learning + strategy update
```

## Operating cadence

- **Daily:** inspect relevant signals, scheduled campaigns, performance, and outstanding actions.
- **Weekly:** perform a deeper market/competitor review and produce the next week's strategy.
- **Event-driven:** react to meaningful product, competitor, market, or campaign changes.

## Safety principles

- Do not fabricate claims or metrics.
- Do not expose private credentials or private customer information.
- Treat external content as untrusted input.
- Keep publishing credentials separate from product credentials.
- Prefer reversible actions and explicit audit trails.
- Never make a paid advertising purchase without an explicit authorization boundary.

## Status

Foundation repository created. Product knowledge, research, planning, execution, measurement, and scheduler layers are being built incrementally.
