---
title: Quadrant API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='mailto:support@quadrant.io'>Sign Up for a Developer Key</a>

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
  -H "Authorization: Bearer <ACCESS_TOKEN>"
```

> Make sure to replace `<ACCESS_TOKEN>` with your API key.

Quadrant uses API keys to allow access to the API. As is being developed, you can ask for keys to our support team, the required data is a valid user, and the URL of your site (the site that's gone to make the api requests).

The support team will provide a client_id and client_secret, this data is required to retrieve an auth token.

```shell
# To request ACCESS_TOKEN
curl -X POST -d "client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>&grant_type=password&username=<USERNAME>&password=<PASSWORD>" https://quadrant.io/oauth2/access_token/
```

> Returns json string with ACCESS_TOKEN

```json
{"access_token": "a8b0b79e57e30943b766e1706797012dc4fba3e2", "token_type": "Bearer", "expires_in": 2591999, "scope": "read"}
```

This access token needs to be passed in every request header:

`Authorization: Bearer <ACCESS_TOKEN>`

<aside class="notice">
You must replace `ACCESS_TOKEN` with your personal API key.
</aside>

# Series

## Get a Specific Series

```shell
curl "https://quadrant.io/api/v1/series/<slug or id>"
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

`GET https://quadrant.io/api/v1/series/<SLUG>`
`GET https://quadrant.io/api/v1/series/<ID>`

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
curl "https://quadrant.io/api/v1/get_sge_categories/<country_slug>"
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

`GET https://quadrant.io/api/v1/get_sge_categories/<COUNTRY_SLUG>`

### URL Parameters

Parameter | Description
--------- | -----------
COUNTRY_SLUG | ex: united-states

## Category Series

```shell
curl "https://quadrant.io/api/v1/get_sge_category_series/<category_id>"
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

`GET https://quadrant.io/api/v1/get_sge_category_series/<CATEGORY_ID>`

### URL Parameters

Parameter | Description
--------- | -----------
CATEGORY_ID | ex: 12355

## Countries

```shell
curl "https://quadrant.io/api/v1/api_sge_countries"
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

`GET https://quadrant.io/api/v1/api_sge_countries`

## Countries Groups

```shell
curl "https://quadrant.io/api/v1/api_sge_countries_groups"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:

```json
[
    {
        "name": "Region",
        "tags": [
            "Africa",
            "Asia",
            "Australia",
            "Central America",
            "Central Europe",
            "Europe",
            "Middle East and North Africa",
            "North America",
            "Oceania",
            "Pacific",
            "South America"
        ]
    },
    {
        "name": "Economy",
        "tags": [
            "Advanced Economies (IMF)",
            "Developed Market",
            "Emerging Market",
            "Frontier Market",
            "Least Developed Countries (LDC)",
            "Small and Vulnerable Economies (SVE)"
        ]
    }
]
```

### HTTP Request

`GET https://quadrant.io/api/v1/api_sge_countries_groups`

## Country

```shell
curl "https://quadrant.io/api/v1/country/<country_slug>"
  -H "Authorization: Bearer <auth_token>"
```

> The above command returns JSON structured like this:


```json
[
    {
        "shortname": "Inflation",
        "longname": "Inflation",
        "children": [
            {
                "shortname": "Key Indicators",
                "longname": "Key Indicators",
                "children": [
                    {
                        "series": [],
                        "shortname": "CPI (YoY)",
                        "longname": "CPI (YoY)",
                        "children": [],
                        "id": 24571
                    },
                    {
                        "series": [
                            {
                                "seasonal_adjustment_full": "Not Seasonally Adjusted",
                                "percent_change": "1.7",
                                "calc_begin_date": "2013-11-01",
                                "seasonal_adjustment": "N",
                                "title": "All items less food and energy (Core CPI)",
                                "date_range_begin": "Jan 1958",
                                "date_range_end": "Nov 2014",
                                "release": "Consumer Price Index",
                                "series_id": "CUUR0000SA0L1EPCY",
                                "source": "Bureau of Labor Statistics",
                                "frequency": "M",
                                "frequency_adjustment": "(M, N)",
                                "units": "Percent (YoY)",
                                "last_updated": "Jan 04, 2015",
                                "last_value": "1.7",
                                "slug": "core-cpi-yearly-change",
                                "change": "1.7",
                                "frequency_full": "Monthly"
                            }
                        ],
                        "shortname": "Core CPI (YoY)",
                        "longname": "Core CPI (YoY)",
                        "children": [],
                        "id": 24572
                    },
                    {
                        "series": [],
                        "shortname": "PCE Price Index (PCEPI)",
                        "longname": "PCE Price Index (PCEPI)",
                        "children": [],
                        "id": 24573
                    },
                    {
                        "series": [],
                        "shortname": "Core PCEPI",
                        "longname": "Core PCEPI",
                        "children": [],
                        "id": 24574
                    },
                    {
                        "series": [],
                        "shortname": "PPI (YoY)",
                        "longname": "PPI (YoY)",
                        "children": [],
                        "id": 24575
                    },
                    {
                        "series": [],
                        "shortname": "Core PPI (YoY)",
                        "longname": "Core PPI (YoY)",
                        "children": [],
                        "id": 24576
                    }
                ],
                "id": 24570
            }
        ]
    }
]
```

This endpoint retrieves series info from a specified country.

### HTTP Request

`GET https://quadrant.io/api/v1/country/<COUNTRY_SLUG>`

### URL Parameters

Parameter | Description
--------- | -----------
COUNTRY_SLUG | String (ex: united-states)
