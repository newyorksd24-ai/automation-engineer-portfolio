# Weather API Lab

## What it does
Calls the OpenWeatherMap API to retrieve real-time weather data for a given city, extracts key fields, and returns a clean JSON output with temperature converted from Kelvin to Celsius.

## Trigger
Manual — "Execute Workflow" button

## Endpoint
```
GET https://api.openweathermap.org/data/2.5/weather?lat={lat}&lon={lon}&appid={API_KEY}
```
Authentication: API Key via query parameter.

## Workflow Structure
```
Manual Trigger → HTTP Request → Code in JavaScript
```

| Node | Type | What it does |
|------|------|--------------|
| Manual Trigger | Trigger | Starts the workflow manually |
| HTTP Request | HTTP | Calls OpenWeatherMap with API Key auth |
| Code in JavaScript | Code | Extracts fields and converts temperature |

## Output Example
```json
{
  "city": "Trevi",
  "temp": 16.49,
  "description": "few clouds"
}
```

## Code — Field Extraction
```javascript
const data = $input.first().json;

const kelvin = data.main.temp;
const temp = parseFloat((kelvin - 273.15).toFixed(2));
const city = data.name;
const description = data.weather[0].description;

return [{
  json: {
    city,
    temp,
    description
  }
}];
```

## Key Concepts Practiced
- REST API: GET method, API Key authentication
- JSON navigation: nested objects and arrays
- Data transformation: Kelvin → Celsius conversion
- n8n: HTTP Request node + Code node pattern
