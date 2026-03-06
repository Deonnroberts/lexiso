🚀 **Lexiso is now public (v0.1.0).**
This is an early open-core release; interfaces may evolve.
Feedback welcome via GitHub Issues.

---

# **Lexiso**

Lexiso is the authorization and compliance layer for AI agents executing financial actions. As AI agents gain the ability to spend money, subscribe to services, and trigger real-world financial effects—Lexiso ensures that nothing executes without explicit, verifiable authorization. Lexiso sits in the execution path, not on the sidelines.

This repository contains the open-core of Lexiso under the Lexiso Source-Available License.

---

## Quick Start

Install the SDK:
```bash
npm install lexiso
```

Initialize the client:
```javascript
const { Lexiso } = require('lexiso');

const client = new Lexiso('sk_live_your_api_key');
```

Create an agent and authorize a transaction:
```javascript
// Register an AI agent
const agent = await client.createAgent('My AI Assistant', 'openai');

// Create a spending policy
await client.createPolicy(agent.id, 'Default Policy', {
  amount_limits: {
    per_transaction: 100,
    daily: 500,
    monthly: 2000
  },
  allowed_categories: ['shopping', 'software', 'travel']
});

// Authorize a payment
const decision = await client.authorize(agent.id, 49.99, {
  merchant: 'Amazon',
  category: 'shopping'
});

if (decision.decision === 'allow') {
  console.log('Authorized:', decision.signature);
} else {
  console.log('Denied:', decision.reason);
}
```

Get your API key at [lexiso.app/setup](https://lexiso.app/setup)

---

## **The Problem**

Autonomous AI agents are increasingly capable of taking financial actions:

- Making purchases on behalf of users
- Managing subscriptions and renewals
- Executing procurement workflows
- Accessing paid APIs and services
- Triggering payments and transfers

Existing safeguards focus on:

- Model alignment
- Monitoring and alerts
- Post-hoc auditing

These approaches fail at the critical moment: execution. Once a payment is triggered, it is often too late.

---

## **The Lexiso Approach**

Lexiso introduces a simple but powerful architectural principle:

**All financial actions must pass through an authorization gate before execution.**

At the gate, each request is evaluated against explicit policies, resulting in a **cryptographically signed** decision:
```
ALLOW  – execute with signed proof of authorization
DENY   – reject with reason code and audit trail
```

This creates verifiable proof of exactly what was authorized, when, and why.

---

## **What Lexiso Is (Conceptually)**

A decision point for payments, not a watcher
An authorization layer, not a payment processor
A policy engine, not a chatbot
Rail-agnostic: works with any payment system

It is designed to be:

- **Fast**: Sub-300ms authorization decisions
- **Deterministic**: Same inputs, same outputs
- **Auditable**: Every decision is cryptographically signed
- **Compliant**: Built for AP2 and emerging standards

---

## **Core Capabilities**

### Policy-Driven Authorization

- Human-readable policies (YAML/JSON)
- Deterministic evaluation
- Hot-reloadable rules
- Clear ALLOW / DENY semantics

### Cryptographic Signing

- RSA-2048 signatures on all decisions
- Verifiable proof of authorization
- Tamper-evident audit trail
- Third-party verification support

### Payment-Specific Controls

- Spending limits (per-transaction, daily, monthly)
- Merchant whitelists and blacklists
- Category restrictions
- Time-window controls
- Velocity limits

### AP2 Compliance

- Intent mandate support
- Cart mandate support
- Designed for Google's Agent Payments Protocol
- Ready for emerging agentic commerce standards

---

## **Example Use Cases**

- AI shopping assistants making purchases
- Procurement bots managing vendor payments
- Subscription management agents
- Expense automation systems
- Multi-agent financial workflows
- Regulated or compliance-sensitive environments

In all cases, Lexiso ensures that AI financial autonomy operates only within explicitly defined bounds.

---

## **Status**

Lexiso is currently in:

- **Live production API** at api.lexiso.app
- **Published SDK** on npm (`lexiso`)
- **Full documentation** at lexiso.app/docs
- **Seeking design partners** for integration feedback

The current focus is on:

- Validating with real integrations
- Expanding connector ecosystem
- Enterprise deployment models

---

## **What Comes Next**

Planned evolution includes:

- Python SDK
- Dashboard UI for policy management
- Self-service API key generation
- Enhanced audit exports
- Additional compliance certifications

---

## **Philosophy**

Lexiso is built on a single, non-negotiable principle:

**AI agents should not spend money without explicit, provable authorization.**

Lexiso provides that authorization—clearly, cryptographically, and at the moment it matters most.

---

## **License**

Lexiso Core is source-available under the Lexiso Source-Available License.
You may inspect, modify, and evaluate the software freely for non-commercial purposes only.

**Commercial and production use requires a commercial license.**

See [LICENSE.md](LICENSE.md) for details.

---

## **Links**

- **Website**: [lexiso.app](https://lexiso.app)
- **API**: [api.lexiso.app](https://api.lexiso.app)
- **Documentation**: [lexiso.app/docs](https://lexiso.app/docs)
- **npm**: [npmjs.com/package/lexiso](https://www.npmjs.com/package/lexiso)

---

**Built by Deonte Roberts.**
