# Github Repository Lookup

## Problem

Fetch Github repository information using owner name and repository name.

# Input

```json 
{
    "owner": "torvalds",
}
```

## Output

Repository name
Stars ⭐
Forks
Open issues
Primary language
Last updated

# Workflow

Webhook -> Edit Field(SET) -> -> HTTP Request(GET) -> Discord 

## Concepts Learned

- Webhooks
- HTTP Requests
- JSON Parsing
- Discord Webhooks
- REST API
- Data Transformation
  
