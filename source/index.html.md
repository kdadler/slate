---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - accountRequest
  - contacts
  - offers
  - offerLines
  - baskets
  - basketLines
  - unitPriceNegotiations
  - salesOrders
  - salesOrderLines 
  - usageData
  - errors
  - ztodo

search: true
---

# Introduction

WIP version of the internal API docs for Yoda. Is REST.

# Making a Request

> base path

```
{base_url}/api/{entity_type}(/{id})
```

> Headers

```json
{
  "Accept": "application/vnd.api+json",
  "content-type": "application/vnd.api+json"
}
```

## Authentication

TBC, possibly something like JWT?
