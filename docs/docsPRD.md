# Pasar – Developer‑First Product Requirements Document (PRD)

---

## 0. Document Purpose & Audience

**Primary audience (who this is for):**

* Founders & co‑founders
* Mobile & backend engineers (React Native, API, Blockchain)
* Product designers (UI/UX)
* AI / automation engineers

**Secondary audience:**

* Early investors
* Advisors
* Strategic partners (payments, logistics)

This PRD is written in a **developer‑first, system‑level tone** so it can be used directly with:

* Cursor
* Figma Make AI
* Code‑generation workflows

This is **not marketing copy**. It defines rules, constraints, flows, and architecture.

---

## 1. What Pasar Is (Clear Definition)

**One‑line definition:**
Pasar is a **trust‑enforced commerce system** that guarantees safe peer‑to‑peer transactions using escrow, verification, and controlled delivery.

**Expanded definition:**
Pasar is **not** trying to be a full e‑commerce marketplace at launch. Pasar is a **transaction engine** that sits between buyers and sellers to:

* Lock money
* Verify goods
* Control handover
* Resolve disputes objectively

Pasar wins by **owning the transaction lifecycle**, not by hosting infinite listings.

---

## 2. The Problem (Why This Exists)

### 2.1 Market Reality

In Nigeria (and similar markets):

* Buying happens on WhatsApp, Instagram, Jiji
* Payments happen with zero protection
* Delivery is untrusted
* Disputes are emotional, not evidence‑based

Commerce fails **not because of demand**, but because **trust collapses at the moment of payment and delivery**.

### 2.2 Buyer Pain

* Fear of fake or damaged products
* Fear of paying and receiving nothing
* No enforceable refund path

### 2.3 Seller Pain

* Fear of buyers denying delivery
* Losses from failed deliveries
* Cash‑on‑delivery inefficiency

### 2.4 Why Existing Platforms Fail

| Platform             | Why It Fails                         |
| -------------------- | ------------------------------------ |
| WhatsApp / Instagram | No escrow, no enforcement            |
| Jiji                 | No payment protection, high fraud    |
| Jumia / Konga        | Built for retail, not P2P; high fees |

---

## 3. Product Thesis

**Trust must be enforced by systems, not behavior.**

Pasar embeds trust into:

* Payment (escrow)
* Asset verification
* Delivery custody
* Dispute resolution

Users do not need to "trust" each other.
They only need to trust Pasar.

---

## 4. MVP Strategy (Critical Constraint)

Pasar launches with a **narrow wedge**, not a broad marketplace.

### 4.1 MVP Wedge

| Dimension | MVP Scope                           | Reason                             |
| --------- | ----------------------------------- | ---------------------------------- |
| Category  | Used Smartphones (Android + iPhone) | High value, high fraud, verifiable |
| Geography | Lagos only                          | Dense supply, logistics control    |
| Platform  | Android App (V1)                    | Market reality                     |
| Model     | Managed P2P                         | Liquidity + trust control          |

---

## 5. Core System Architecture (High Level)

Pasar consists of **five core systems**:

1. **Pasar Escrow** – money lock & release
2. **Pasar Scan** – asset verification
3. **Pasar Move** – logistics & custody
4. **Xiara** – AI trust guardrails
5. **Trust Ops** – human arbitration layer

These systems are independent but orchestrated.

---

## 6. Pasar Escrow (Payment & Settlement Engine)

### 6.1 Principles

* Fiat‑first UX
* Crypto‑backed enforcement
* No visible blockchain complexity

### 6.2 Payment Flow (V1)

**On‑Ramp:**

* Buyer pays in NGN (bank transfer / card)
* Funds auto‑converted to stablecoin (USDC)
* Stablecoin locked in escrow smart contract

**Escrow Rules:**

* Lock on payment success
* Release on buyer confirmation OR timeout
* Refund on verified failure

**Inspection Window:**

* 24 hours after delivery confirmation

**Off‑Ramp:**

* Seller withdraws NGN to bank account
* T+0 / T+1 settlement

---

## 7. Pasar Scan (Verification System)

### 7.1 Purpose

Ensure the phone listed is:

* Real
* Legal
* Matches description

### 7.2 V1 Scan Requirements

1. **IMEI Check**

* API lookup against stolen/blacklist DB

2. **Proof Video Upload**

* Timestamped
* Shows:

  * About screen (IMEI)
  * Physical condition (front/back/sides)

3. **Condition Grading**

* Grade A: Mint
* Grade B: Good
* Grade C: Fair

Listings go live **only after Scan passes**.

---

## 8. Pasar Move (Logistics & Chain of Custody)

### 8.1 Model

* Third‑party logistics partners
* OTP‑based custody transfer

### 8.2 Pickup Flow

1. Seller requests pickup
2. Rider matches phone to listing
3. OTP generated
4. OTP confirmed → custody transfers to Pasar

### 8.3 Liability

* After OTP: Pasar is responsible
* If logistics fails:

  * Buyer refunded
  * Seller paid
  * Pasar recovers from partner or guarantee fund

---

## 9. Identity & Trust Controls (KYC Lite)

### Tier 0 (Required)

* Phone verification
* Device fingerprint

### Tier 1 (Unlocks limits)

* BVN verification (hidden)

No anonymous trading at scale.

---

## 10. Xiara (AI Guardrails – MVP Scope)

Xiara is **not a chatbot**.

### MVP Responsibilities

* Price anomaly detection
* Off‑platform payment detection
* Dispute pre‑classification

Xiara assists decisions; it does not replace humans.

---

## 11. User Journeys

### Happy Path

1. Seller lists phone → Scan passes
2. Buyer pays → escrow locked
3. Pickup → OTP custody
4. Delivery → inspection
5. Buyer confirms → escrow releases

### Dispute Path

* Buyer disputes within 24h
* Evidence auto‑attached
* AI + Trust Ops resolve

---

## 12. Cold Start & Liquidity Strategy

**Managed Supply Launch:**

* 5–10 vetted Computer Village vendors
* Zero fees + free logistics

Goal: eliminate early fraud narratives.

---

## 13. Success Metrics

**North Star:**

* % of GMV settled without dispute

**Supporting Metrics:**

* Dispute rate (<5%)
* Time to escrow release
* Seller repeat rate

---

## 14. Scaling Roadmap

### Phase 1 (MVP)

* Used phones, Lagos

### Phase 2

* Laptops, tablets
* More cities

### Phase 3

* Seller storefronts
* Category expansion

### Phase 4

* Pasar as Trust API

---

## 15. Non‑Goals (Important)

* No infinite categories in V1
* No social feed
* No crypto education UX

---

## 16. Build Order (Execution Discipline)

1. Escrow logic
2. Scan verification
3. Logistics custody
4. Dispute flow
5. Marketplace UI

---

**End of PRD**
