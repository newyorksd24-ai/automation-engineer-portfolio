# Formatter Lab

## What it does
Validates and normalizes lead data.
Checks for duplicates on Google Sheets.
Saves only new and valid leads.

## Flow
Input → JS Validation → Duplicate Lookup → Append or ERR

## Scenarios
| Scenario | Result |
|----------|--------|
| Valid lead, not duplicate | Append + ok output |
| Valid lead, duplicate | ERR output |
| Invalid lead | ERR output with errors[] |

## Files
- `formatter-lab.json` → n8n workflow, ready to import