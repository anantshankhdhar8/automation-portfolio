# weather-api-authentication

## Problem

fetching current weather information of a city using OpenWeatherMap API with failure handling.

# Input

```json 
{
    "city": "Delhi",
    "lat": "28.6139",
    "lon": "77.2090"
}
```
## Output

city:Delhi
Temperature
Humidity
Weather
Wind Speed

# Workflow

webhook -> Edit Field(SET) -> IF(true) -> HTTP Request(GET) -> Discord -> IF(false) -> Discord->Message(Bad coordinate received)

## Concepts Learned
- Webhooks
- HTTP Requests
- JSON Parsing
- Discord Webhooks
- REST API
- Data Transformation
- Failure Handling
- Authentication
- API Key Management
- Rate Limiting
- Error Handling

## Lessons Learned
-API keys prove identity but don't automatically grant access to resources. OpenweatherMap API version 4.0 is paid and requires a paid subscription access the full API. The free version of the API is limited to version 2.5 and has a limit of 60 calls per minute. The API key is used to track usage and enforce rate limits. If you exceed the rate limit, you will receive a 429 Too Many Requests response.
-Read the endpoint documentation before assuming a URL works, we used open api 4.0 url for open api 2.5 api key.
-Validate inputs before calling external APIs, it prevents unnecessary API calls and helps in handling errors gracefully. In this case, we validated the coordinates before making the API call to avoid receiving a 400 Bad Request response from the OpenWeatherMap API.
- Query parameters can configure behavior (for example, metric vs. Kelvin), changed by &units=metric or &units=imperial. The default is Kelvin.