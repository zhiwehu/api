---
title: Quadrant API Reference

language_tabs:
  - shell

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
curl "http://quadrant.io/api/v1/series/<slug or id>"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
{
  "series_id": "CUUR0000SA0L1EPCY",
  "title": "All items less food and energy (Core CPI)",
  "slug": "core-cpi-yearly-change",
  "units": "Percent (YoY)",
  "frequency": "Monthly",
  "date_range_begin": "1958-01-01",
  "date_range_end": "2014-11-01",
  "series_data_list": [
    {
      "date": "1958-01-01",
      "value": 3.16
    },
    {
      "date": "1958-02-01",
      "value": 3.16
    }
  ],
  "allow_frequency_list": [
    "Monthly",
    "Quarterly",
    "Semiannual",
    "Annual"
  ],
  "aggregate_method": "AVG",
  "last_updated": "2015-01-04T14:30:00Z"
}
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

# SGE

## Categories

```shell
curl "http://quadrant.io/api/v1/get_sge_categories/<country_slug>"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
[
  {
    "shortname": "Inflation",
    "children": [],
    "id": 24569,
    "longname": "Inflation"
  },
  {
    "shortname": "Employment",
    "children": [],
    "id": 24606,
    "longname": "Employment"
  },
  {
    "shortname": "Interest Rates",
    "children": [],
    "id": 24654,
    "longname": "Interest Rates"
  },
  {
    "shortname": "GDP",
    "children": [],
    "id": 24697,
    "longname": "GDP"
  }
]

```

This endpoint retrieves all sge categories.

### HTTP Request

`GET http://quadrant.io/api/v1/get_sge_categories/<COUNTRY_SLUG>`

### URL Parameters

Parameter | Description
--------- | -----------
COUNTRY_SLUG | ex: united-states

## Category Series

```shell
curl "http://quadrant.io/api/v1/get_sge_category_series/<category_id>"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
  [
    {
        "last_updated": "Sep 12, 2014",
        "seasonal_adjustment_full": "NSA",
        "percent_change": "5.0",
        "title": "Afghanistan - Sales Tax Rate",
        "seasonal_adjustment": "N",
        "calc_begin_date": "2013-01-01",
        "date_range_begin": "Jan 2014",
        "date_range_end": "Jan 2014",
        "series_id": "SGE_AFGSTR",
        "source": "Afghanistan Revenue Department",
        "frequency": "D",
        "frequency_adjustment": "(D, N)",
        "units": "Percent",
        "frequency_full": "Daily",
        "last_value": "5.0",
        "slug": "afghanistan-sales-tax-rate",
        "change": "5.0",
        "release": ""
    }
]
```

### HTTP Request

`GET http://quadrant.io/api/v1/get_sge_category_series/<CATEGORY_ID>`

### URL Parameters

Parameter | Description
--------- | -----------
CATEGORY_ID | ex: 12355

## Countries

```shell
curl "http://quadrant.io/api/v1/api_sge_countries"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
[
    {
        "slug": "afghanistan",
        "tags": [
            "Asia",
            "Asian Development Bank (ADB)",
            "Executive head of state",
            "Fragile and conflict affected situations",
            "Heavily indebted poor countries",
            "HIPC",
            "IDA",
            "International Development Association",
            "Least Developed Countries (LDC)",
            "Low income",
            "Presidential System",
            "Republic",
            "South Asia"
        ],
        "iso": "AF",
        "id": 1,
        "name": "Afghanistan"
    },
    {
        "slug": "albania",
        "tags": [
            "Ceremonial head of state",
            "Europe",
            "Europe and Central Asia",
            "IBRD",
            "International Bank for Reconstruction and Development",
            "NATO",
            "Parliamentary republic",
            "Republic",
            "Upper middle income"
        ],
        "iso": "AL",
        "id": 2,
        "name": "Albania"
    }
]
```

### HTTP Request

`GET http://quadrant.io/api/v1/api_sge_countries`

