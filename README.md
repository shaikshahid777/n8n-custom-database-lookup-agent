# n8n Custom Database Lookup Agent

A reusable **n8n AI Agent** that looks up customer information through a custom Workflow Tool.

## Overview

This project demonstrates:

- AI Agent workflow in n8n
- Google Gemini Chat Model
- Window Buffer Memory
- Custom Workflow Tool
- Required `customer_id` input
- Code-based mock customer database
- Valid and invalid customer lookup handling

## Workflow

```text
Chat Trigger
    ↓
Customer Support Agent
    ├── Google Gemini Chat Model
    ├── Window Buffer Memory
    └── customer_lookup Workflow Tool
             ↓
       Customer Lookup Tool
             ↓
       Lookup Customer
             ↓
        Customer Result
```

## Key Configuration

- **Model:** Google Gemini
- **Temperature:** `0.0`
- **Max Output Tokens:** `512`
- **Max Iterations:** `5`
- **Memory Context:** `10`
- **Tool Input:** `customer_id` (required string)

## Custom Tool Behavior

The lookup workflow receives a customer ID, normalizes it, checks the mock customer database, and returns either:

- `found: true` with customer details
- `found: false` with a clear not-found response

## Sample Test Cases

| Test | Input | Expected |
|---|---|---|
| Valid lookup | `Find customer CUST001` | Customer record returned |
| Valid lookup | `What plan does CUST003 have?` | Correct plan returned |
| Invalid lookup | `Find customer CUST999` | Customer not found |
| Missing ID | `What is the customer's plan?` | Agent asks for customer ID |

## Project Files

```text
workflows/
  Customer Support AI Agent.json
  Customer Lookup Tool.json

data/
  sample-customers.json

documentation/
  Topic-6-Assessment.pdf

screenshots/
test-evidence/
```

## Model Note

Google Gemini is used as the Chat Model in this implementation instead of OpenAI because of OpenAI API rate-limit limitations during development.

## Assessment

This repository contains the implementation files and supporting evidence for the Topic 6 assessment: **Building Custom Tools via Workflow, Code, and API Nodes – Create and Validate a Custom Database Lookup Tool**.

## Demo

Loom Demo: https://www.loom.com/share/fd4c58e547ec4aeb9b907a861589acbc
