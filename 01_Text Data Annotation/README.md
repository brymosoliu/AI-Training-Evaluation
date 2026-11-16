# Customer support text annotation guide

## Purpose and scope
This synthetic dataset supports training and evaluating customer-support classifiers and NER systems. Assign one value per record for sentiment, intent, category, and urgency. Mark every explicit supported entity in `entities_json`. It contains 120 fictional records; identifying details are fictional examples.

---

## Label definitions

### Sentiment
- `positive`: praise, satisfaction, thanks, or a clearly favorable reaction.
- `neutral`: information seeking or a request without clear emotional polarity.
- `negative`: dissatisfaction, complaint, concern, or a clearly unfavorable experience.
- Label expressed attitude, not likely outcome. A polite complaint remains negative.

### Intent
Choose one primary action: `refund_request`, `payment_failure`, `invoice_request`, `subscription_cancel`, `account_access`, `password_reset`, `shipping_status`, `late_delivery`, `address_change`, `product_defect`, `technical_howto`, or `warranty_question`. Prefer the most specific intent supported by the text.

### Category
Use the corresponding group: `Billing & payments` (refund, payment, invoice); `Account & subscription` (cancellation, account access, password reset); `Orders & delivery` (tracking, late delivery, address change); `Product & technical support` (defect, setup/how-to, warranty). Category must agree with intent.

### Urgency
- `low`: routine question or request with no time pressure.
- `medium`: inconvenience or an action with stated near-term timing.
- `high`: significant disruption, failed access/payment, damaged product, or explicitly urgent delivery.
- `critical`: immediate severe impact or explicit emergency-level language. Use sparingly; urgency is triage priority, not sentiment intensity.

### Named entities and offsets
`entities_json` is an array of objects with `text`, `type`, `start`, and `end`. Offsets count Unicode code points from zero; start is inclusive and end exclusive. The text slice must exactly equal the entity text. Types used are `ORDER_ID`, `MONEY`, `DATE`, `EMAIL`, `LOCATION`, and `PRODUCT`. Annotate explicit spans only; do not infer missing entities. Use `[]` when none are present.

## Consistency and adjudication
1. Read the full message before labeling.
2. Assign exactly one primary intent and its mapped category.
3. Separate sentiment from urgency: neutral can be high priority; a negative complaint can be low urgency.
4. Prefer explicit wording; for competing intents, choose the requested resolution or action.
5. Flag ambiguity for adjudication rather than inventing evidence.
6. Check duplicate IDs, allowed labels, category-intent agreement, valid JSON, and exact entity span reconstruction.

---

## Dataset 
All records are synthetic, template-based examples for demonstrating an annotation workflow. Production use should add naturally occurring, consented, de-identified data and independent double annotation.
