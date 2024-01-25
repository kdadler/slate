---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - companies
  - contacts
  - salesNegotiations
  - users

search: true
---

# Introduction

WIP version of the Yoda public API documentation. 

# Making a Request

The Yoda API follows a RESTful design.

> URL

```
{base_url}/api/{entity_type}(/{id})
```

> Headers

```json
{
  "Accept": "application/vnd.api+json",
  "Content-Type": "application/api"
}
```

## Authentication

TBC, likely Oauth2
