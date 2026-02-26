# PokéAPI — Data Extraction Workflow

## What it does
Calls the PokéAPI to retrieve Pokémon data, extracts three specific fields, and returns a clean JSON output.

## Trigger
Manual — "Execute Workflow" button

## Endpoint
```
GET https://pokeapi.co/api/v2/pokemon/{name}
```
No authentication required.

## Workflow Structure
```
Manual Trigger → HTTP Request → Code in JavaScript
```

| Node | Type | What it does |
|------|------|--------------|
| Manual Trigger | Trigger | Starts the workflow manually |
| HTTP Request | HTTP | Calls PokéAPI with GET method |
| Code in JavaScript | Code | Extracts and returns clean fields |

## Output Example
```json
{
  "name": "pikachu",
  "base_experience": 112,
  "type": "electric"
}
```

## Code — Field Extraction
```javascript
const response = $input.first().json;

const name = response.name;
const base_experience = response.base_experience;
const type = response.types[0].type.name;

return [{
  json: {
    name,
    base_experience,
    type
  }
}];
```

## Key Concepts Practiced
- REST API: GET method, public endpoint, no auth
- JSON navigation: nested objects and arrays
- n8n: HTTP Request node + Code node pattern
