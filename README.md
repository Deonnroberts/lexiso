🚀 **Lexiso is now public (v0.1.0).**
This is an early open-core release; interfaces may evolve.
Feedback welcome via GitHub Issues.

---

# **Lexiso**

Lexiso is the authorization and compliance layer for AI agents executing financial actions. As AI agents gain the ability to spend money, subscribe to services, and trigger real-world financial effects—Lexiso ensures that nothing executes without explicit, verifiable authorization.

This repository contains the open-core of Lexiso under the Lexiso Source-Available License.

---

## **The Problem**

Autonomous AI agents are increasingly capable of taking financial actions:

- Making purchases on behalf of users
- Managing subscriptions and renewals
- Executing procurement workflows
- Accessing paid APIs and services

Existing safeguards focus on model alignment, monitoring, and post-hoc auditing.

**These approaches fail at the critical moment: execution.**

---

## **The Lexiso Approach**

All financial actions must pass through an authorization gate before execution.

Each request is evaluated against explicit policies, resulting in a cryptographically signed decision:

- ALLOW - execute with signed proof of authorization
- DENY - reject with reason code

---

## **What Lexiso Is**

- An authorization layer, not a payment processor
- A policy engine, not a chatbot  
- A decision point, not an after-the-fact monitor
- Rail-agnostic: works with Stripe, banks, crypto, any payment system

---

## **Core Capabilities**

- Policy-Driven Authorization
- Cryptographic Signing (RSA-2048)
- Payment-Specific Controls
- AP2 Compliance

---

## **Status**

- Live API: api.lexiso.app
- Published SDK: npm install lexiso
- Documentation: lexiso.app/docs

---

## **License**

Lexiso Core is source-available under the Lexiso Source-Available License.
Commercial and production use requires a commercial license.

See LICENSE.md for details.

---

## **Links**

- Website: https://lexiso.app
- API: https://api.lexiso.app
- Docs: https://lexiso.app/docs
- npm: https://npmjs.com/package/lexiso

---

Built by Deonte Roberts.
