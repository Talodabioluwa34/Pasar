# Pasar – UX Contract (MVP)

## Purpose
Defines the non-negotiable UX rules for Pasar MVP.
No screen or interaction may exist outside this contract.

## Design Philosophy
- Trust over aesthetics
- Evidence over promises
- Status clarity over delight

## MVP Screen Inventory
1. Marketplace Listing
2. Product Detail + Scan Proof
3. Checkout & Escrow Lock
4. Order Status Timeline
5. Delivery & Inspection
6. Dispute
7. Basic Profile

---

## Screen 1: Marketplace Listing (Buyer Entry)

### Purpose
This is the **default entry screen** of the app.
Its sole job is to answer one question within 3 seconds:

> “Is it safe to buy here?”

This screen optimizes for **trust clarity**, not discovery depth.

---

### Who Sees This Screen
- All users (authenticated or newly authenticated)
- No forced onboarding before access

---

### Core User Intent
- Quickly assess whether Pasar is trustworthy
- Browse available verified phones
- Select a phone to inspect deeper

---

### Data Required (Mandatory)

Each product card MUST display:

- Phone model (e.g. iPhone 12 Pro)
- Price (NGN – primary)
- Condition grade (A / B / C)
- Verification status (Scan passed)
- Escrow protection badge
- Seller reputation score
- Seller location (city only)

If any of the above data is missing, the listing MUST NOT render.

---

### Trust Signals (Non-Negotiable)

Each listing MUST show:

- “Escrow Protected” badge
- “IMEI Verified” or “Scan Verified” badge
- Seller rating (numeric, not stars only)

These signals must be visible **without scrolling**.

---

### Primary Interaction

- Tap product card → Product Detail + Scan Proof screen

No other primary action is allowed.

---

### Secondary Interactions (Allowed)

- Filter by:
  - Price range
  - Condition grade
  - Verified sellers only

- Sort by:
  - Newest
  - Price (low → high)

---

### Explicitly Forbidden Interactions

- No chat with seller
- No “Save for later”
- No social reactions
- No ads or sponsored cards
- No “Pay now” from listing screen

---

### Empty State

If no listings are available:

- Show message:
  “All listings on Pasar are verified. New phones will appear soon.”

- No call-to-action to sell from buyer entry

---

### Error States

- Network failure → retry state
- Verification failure → listing hidden entirely

---

### Performance Constraints

- First contentful paint < 2 seconds on mid-range Android
- Skeleton loaders allowed
- Infinite scroll allowed, pagination preferred

---

### Design Constraints

- Neutral background
- No bright promotional colors
- Color usage only for:
  - Escrow status
  - Verification status
  - Errors

---

### MVP Guardrails

This screen MUST NOT:
- Explain blockchain
- Explain crypto
- Show delivery mechanics
- Show dispute mechanics
- Show seller contact details

This screen only establishes **trust and selection**.

---

---

## Screen 3: Checkout & Escrow Lock

### Purpose
This screen exists to **convert intent into a protected transaction**.

It must make the buyer feel:
- In control
- Protected
- Certain about what happens next

No ambiguity is allowed here.

---

### Who Sees This Screen
- Buyers only
- Accessed after tapping “Buy with Escrow” on Product Detail

---

### Core User Intent
- Confirm purchase details
- Understand escrow protection
- Complete payment safely

---

### Data Required (Mandatory)

This screen MUST display the following sections, in this order:

---

#### Section 1: Order Summary

- Phone model
- Condition grade
- Price (NGN)
- Delivery city
- Seller reputation snapshot

This section is read-only.

---

#### Section 2: Escrow Explanation (Simple)

Must include a short, plain-language explanation:

> “Your payment is locked securely and only released after you confirm delivery.”

No mention of:
- Blockchain
- Crypto
- Smart contracts

---

#### Section 3: Delivery Address

- Select or confirm delivery address
- City-level precision is sufficient for MVP
- Address must be editable before payment

---

#### Section 4: Payment Method (V1)

- NGN only
- Bank transfer / card
- No crypto selection UI

Payment option must be explicit and singular.

---

### Primary Action (Single CTA)

- Button: “Confirm & Lock Payment”

This CTA:
- Locks funds in escrow on success
- Is disabled if any required data is missing
- Must show loading + success states

---

### Success State

After successful payment:
- Show confirmation message:
  “₦X secured in escrow”
- Transition user to Order Status Timeline screen

---

### Error States

- Payment failure → retry
- Network failure → retry
- Escrow unavailable → block transaction

If escrow cannot be locked, the transaction MUST NOT proceed.

---

### Explicitly Forbidden Actions

- No payment outside escrow
- No partial payments
- No price changes
- No promo codes or discounts

---

### Performance Constraints

- Payment confirmation feedback < 3 seconds
- Clear loading indicators required

---

### Design Constraints

- Calm, neutral UI
- Emphasis on security and confirmation
- No celebratory animations

---

### MVP Guardrails

This screen MUST NOT:
- Offer alternative payment flows
- Educate about future features
- Expose seller contact information

This screen exists solely to **lock funds safely**.

---
