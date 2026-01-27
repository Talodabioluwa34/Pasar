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
