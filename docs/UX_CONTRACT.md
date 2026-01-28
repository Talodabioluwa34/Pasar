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

---

## Screen 4: Order Status Timeline

### Purpose
This screen provides a **single, authoritative view** of the transaction state.

It eliminates:
- Buyer anxiety
- Seller confusion
- Support questions

At any moment, the user should know:
- What has happened
- What is happening
- What can happen next

---

### Who Sees This Screen
- Buyers and Sellers
- Automatically shown after successful escrow lock
- Accessible from Order History

---

### Core User Intent

**Buyer:**
- Track order progress
- Know when inspection starts
- Know when funds release

**Seller:**
- Know when pickup occurred
- Know when funds will be released
- Know if dispute is active

---

### Order States (Authoritative)

The order MUST move through these states in sequence:

1. Escrow Locked  
2. Pickup Scheduled  
3. In Transit  
4. Delivered  
5. Inspection Window  
6. Completed  
7. Disputed (optional branch)

No other states are allowed in MVP.

---

### Timeline Display Requirements

- Linear vertical timeline
- Each state must show:
  - Status label
  - Timestamp
  - Short explanation

Example:
> ✔ Escrow Locked  
> ₦250,000 secured safely

---

### Buyer Actions (State-Gated)

| State              | Buyer Action Allowed        |
|--------------------|-----------------------------|
| Escrow Locked      | None                        |
| In Transit         | None                        |
| Delivered          | None                        |
| Inspection Window  | Accept / Report Issue       |
| Completed          | View receipt only           |
| Disputed           | Upload evidence only        |

---

### Seller Actions (State-Gated)

| State              | Seller Action Allowed       |
|--------------------|-----------------------------|
| Escrow Locked      | Prepare item                |
| Pickup Scheduled   | Hand over item              |
| In Transit         | None                        |
| Inspection Window  | Await decision              |
| Completed          | Withdraw funds              |
| Disputed           | Provide response            |

---

### Inspection Window Rules

- Duration: 24 hours
- Countdown timer must be visible to buyer
- If buyer takes no action:
  - Escrow auto-releases
  - Order transitions to Completed

---

### Dispute Trigger Rules

- Buyer may dispute ONLY during Inspection Window
- Dispute action immediately:
  - Freezes escrow
  - Changes state to Disputed
  - Locks further actions

---

### Notifications (Mandatory)

User must receive notifications on:
- Escrow locked
- Pickup completed
- Delivery confirmed
- Inspection window start
- Escrow release
- Dispute opened / resolved

---

### Explicitly Forbidden Behavior

- No manual state skipping
- No manual fund release
- No seller-initiated dispute
- No buyer cancellation after pickup

---

### Performance Constraints

- Timeline must update in near-real time
- Status changes must be idempotent
- State transitions must be auditable

---

### MVP Guardrails

This screen MUST NOT:
- Explain future phases
- Show internal system jargon
- Expose admin controls
- Allow free-form messaging

This screen is a **state machine visualizer**, nothing else.

---

---

## Screen 5: Delivery & Inspection

### Purpose
Enable the buyer to make a **binary decision**:
- Accept delivery
- Report an issue

This is the only moment the buyer has control over escrow outcome.

---

### Who Sees This Screen
- Buyer only
- Triggered immediately after delivery confirmation

---

### Mandatory Elements
- Delivered item summary
- Inspection countdown timer (24h)
- Clear explanation:
  “You have 24 hours to inspect before payment is released.”

---

### Buyer Actions (Only Two)
- Accept Delivery
- Report Issue

No other actions allowed.

---

### Rules
- Accept → escrow releases
- No action after timer → auto-release
- Report issue → transition to Dispute screen

---

---

## Screen 6: Dispute Evidence

### Purpose
Collect structured evidence to resolve disputes objectively.

---

### Who Sees This Screen
- Buyer (initiator)
- Seller (response view only)

---

### Buyer Inputs (Required)
- Photo evidence (mandatory)
- Issue category (mismatch, damage, missing item)

---

### System Actions
- Freeze escrow
- Lock order state
- Notify Trust Ops

---

### Rules
- Disputes only allowed during inspection window
- No chat or negotiation
- Evidence cannot be edited after submission

---
