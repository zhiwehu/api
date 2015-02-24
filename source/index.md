---
title: Quadrant API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Quadrant API! You can use our API to access Quadrant API endpoints, which can get information on various cats, kittens, and breeds in our database.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace `meowmeowmeow` with your personal API key.
</aside>

# Series

## Get a Specific Series

```shell
curl "http://quadrant.io/api/v1/series"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all series.

### HTTP Request

`GET http://quadrant.io/api/v1/series/<SLUG>`
`GET http://quadrant.io/api/v1/series/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
SLUG | The series Slug
ID  | The id of the series record

### Query Parameters

Parameter | Default | Description | Depends
--------- | ------- | ----------- | -------
units | False | valid units: 'lin', 'chg', 'ch1', 'pch', 'pc1', 'pca' |
frequency | False | valid frequencies: "Monthly", "Quarterly", "Semiannual", "Annual" |
date_range_begin | False | |
date_range_end | False | |
aggregate_method | AVG | | frequency

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>
