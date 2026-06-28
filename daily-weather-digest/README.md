# Daily Weather Digest

## Problem
Generate a daily alert digest from a list of cities using weather API.

## Input

```json 
{
    "cities": ["Delhi", "New York", "London", "Tokyo"]
}
```
## Workflow:

webhook ->Split Out -> HTTP Request(geocoding api) -> Edit Field(SET) -> HTTP Request(OpenWeather api)->Edit Field(SET)->IF -> Aggregate->Code in Python -> Discord

## Sample Output: 
⚠️ Weather Alert Digest

New Delhi
42.73°C • Clear

Chennai
36.9°C • Clouds

Kolkata
36.49°C • Clouds

Jaipur
37.36°C • Clouds

Ahmedabad
39.12°C • Clouds

Lucknow
44.43°C • Clouds

Sydney
13.07°C • Rain

## Concepts Learned:
- Webhooks
- HTTP Requests
- Multi-stage enrichment
- API response mapping
- aggregation of data
- filtering
  
## Lessons Learned:
- both geocoding and current weather api have the common parent url, also they work with the same api key, so we can use the same api key for both the api calls.
- The geocoding api is used to convert city names into latitude and longitude coordinates, which are then used to fetch the current weather information for those cities.
- The OpenWeatherMap API has a limit of 60 calls per minute for the free version, so we need to be mindful of the number of cities we are querying in a single request to avoid hitting the rate limit.
- Mapping the data early to avoid sending big payloads to the next step, which can help in reducing the processing time and improving the performance of the workflow.
  