# Customer support text annotation guide

## Purpose and scope
This synthetic dataset supports training and evaluating customer-support classifiers and NER systems. Assign one value per record for sentiment, intent, category, and urgency. Mark every explicit supported entity in `entities_json`. It contains 150 fictional records; identifying details are fictional examples.

---

## Label definitions

### Sentiment
- `positive`: praise, satisfaction, thanks, or a clearly favorable reaction.
- `neutral`: information seeking or a request without clear emotional polarity.
- `negative`: dissatisfaction, complaint, concern, or a clearly unfavorable experience.
- Label expressed attitude, not likely outcome. A polite complaint remains negative.

---

### Intent
Choose one primary action: Transfer Issue; Password Reset; App Error; Product Information; Complaint Follow-up; Airtime/Data Issue; Account Opening; Card Issue; Complaint; Profile Update; Balance Discrepancy; Statement Request; OTP Issue; Service Feedback; Unauthorised Transaction; Fees and Charges; POS Issue; Contact Channel Issue; Account Status; Account Security; Transfer Information; Wrong Transfer; Product Feedback; Duplicate Transaction
. Prefer the most specific intent supported by the text.

---

### Category
Use the corresponding group: Transfers; Account Access; Technical Support; Account Information; Service Feedback; Airtime; Account Services; Card Services; Service Complaint; Transaction Security; Pricing; POS; Contact Support; Security; Product Feedback. Category must agree with intent.

---

### Urgency
- `low`
- `medium`
- `high`
- `critical`

---

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
