# WF_00 — AI Lead Qualifier

## 🎯 Purpose

Qualify incoming leads using AI, score intent, assign priority, store in CRM, and trigger alerts for high-value leads.

---

## 🔄 Workflow Overview

Webhook → Normalize Data → AI Analysis → Parse Response → Save to CRM → Priority Check → Alert → Respond

---

## 🧩 Node Breakdown

### 01 - Webhook Lead Intake
Receives incoming lead data via POST request.

Expected fields:
- full_name
- email
- phone
- message
- source

---

### 02 - Normalize Lead Data
Standardizes incoming data so downstream nodes always receive consistent fields.

Handles:
- Multiple field formats
- Missing values
- Default fallbacks

---

### 03 - Ollama Gemma Lead Analysis
Sends lead data to local AI model (Gemma via Ollama).

Returns:
- lead_type
- intent_score
- priority
- summary
- recommended_action
- reasoning

---

### 04 - Extract AI Response
Parses AI output safely.

Handles:
- Invalid JSON responses
- Cleans formatting issues
- Applies safety overrides (urgent keywords → force high priority)
- Adds timestamp

---

### 05 - Save Lead to CRM
Stores lead in Google Sheets.

Fields saved:
- lead_id
- created_at
- full_name
- email
- phone
- lead_type
- priority
- intent_score
- summary
- status
- source
- notes

---

### 06 - Check High Priority
Determines if lead requires immediate action.

Conditions:
- priority = high
OR
- intent_score ≥ 75

---

### 07 - High Priority Action
Assigns immediate action instruction.

Example:
- CALL OR TEXT IMMEDIATELY

---

### SMS Alert (Twilio)
Triggered for high-priority leads.

Sends:
- Name
- Contact info
- Score
- Summary
- Recommended action

---

### 08 - Respond Success
Returns structured JSON response to the caller.

---

## 🧠 Logic Summary

- Normalize → Analyze → Parse → Store → Decide → Alert
- AI does classification and scoring
- Workflow enforces safety overrides
- High-value leads trigger instant notification

---

## 📊 Output Example

```json
{
  "success": true,
  "lead": {
    "full_name": "John Doe",
    "email": "john@email.com",
    "phone": "1234567890",
    "lead_type": "buyer",
    "intent_score": 85,
    "priority": "high",
    "summary": "Looking to buy within 30 days",
    "recommended_action": "Call immediately",
    "reasoning": "Clear timeline + intent"
  }
}
