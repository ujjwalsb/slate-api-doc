---
title: Ful.io API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://ful.io/signup'>Signup to ful.io for an API Key</a>
  # - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Ful.io API
---

# Introduction

Welcome to the Ful.io API! Use our APIs to quickly identify technology stacks behind websites, discover relevant email addresses, and effortlessly manage your account subscription and credits.

We provide ready-to-use examples in Shell, Python, JavaScript, and Ruby. Check out the code snippets in the panel to your right, and seamlessly switch languages using the tabs above.

You're all set—let's get started with Ful.io!


# Authentication

> To authorize, use this code:

```ruby
require "httparty"

response = HTTParty.get(
  "https://api.ful.io/your-endpoint",
  query: { api_key: "<YOUR_API_KEY>" }
)
puts response.body

```

```python
import requests

resp = requests.get(
    "https://api.ful.io/your-endpoint",
    params={"api_key": "<YOUR_API_KEY>"}
)
print(resp.json())

```

```shell

# Please pass your endpoint correctly.
curl --location \
  "https://api.ful.io/your-endpoint?api_key=<YOUR_API_KEY>"

```

```javascript
// Please pass your endpoint correctly.
// using axios
import axios from "axios";

axios.get("https://api.ful.io/your-endpoint", {
  params: { api_key: "<YOUR_API_KEY>" }
})
.then(res => console.log(res.data));

```

> Make sure to replace `YOUR_API_KEY` with your API key.

Ful.io uses API keys to allow access to the API. You can view your API key at [dashboard portal - Security](https://ful.io/user/security).

Ful.io APIs require your API key as a query parameter in all requests:

`?api_key=ThisIsYourAPIKey`

<aside class="notice">
You must replace <code>ThisIsYourAPIKey</code> with your personal API key.
</aside>

# Lookups

## Technology Lookup

```ruby
require 'httparty'

tech = HTTParty.get(
  "https://api.ful.io/api/domain-search",
  query: { api_key: "<YOUR_API_KEY>", domain: "example.com" }
)
puts tech.body
```

```python
import requests

resp = requests.get(
    "https://api.ful.io/api/domain-search",
    params={"api_key": "<YOUR_API_KEY>", "domain": "example.com"}
)
print(resp.json())
```

```shell

curl --location \
  "https://api.ful.io/api/domain-search?api_key=<YOUR_API_KEY>&domain=example.com"

```

```javascript
const axios = require('axios');

axios.get('https://api.ful.io/api/domain-search', {
  params: { api_key: '<YOUR_API_KEY>', domain: 'example.com' }
})
.then(res => console.log(res.data));
```

> The above command returns JSON structured like this:

```json
{
  "domain_name": "example.com",
  "technologies": [
    {
      "category_slug": "Mobile",
      "category_name": "Mobile",
      "technologies": [
        {
          "name": "Viewport Meta",
          "description": "This page uses the viewport meta tag which means the content may be optimized for mobile content.",
          "icon": "Viewport Meta.png",
          "website": "https://developers.google.com/speed/docs/insights/ConfigureViewport",
          "technology_slug": "viewport-meta"
        }
      ]
    },
    {
      "category_slug": "Documentation",
      "category_name": "Documentation",
      "technologies": [
        {
          "name": "HTML5 DocType",
          "description": "A DOCTYPE is a required preamble.",
          "icon": "HTML5 DocType.png",
          "website": "https://html.spec.whatwg.org/multipage/syntax.html#the-doctype",
          "technology_slug": "html5-doctype"
        }
      ]
    }
  ]
}
```

This endpoint retrieves all technologies associated with a website name.

### HTTP Request

`GET https://api.ful.io/api/domain-search`

### Query Parameters

Parameter | Description
--------- | -----------
api_key | You have to paste the API key which has been assigned to you specifically.
domain | Enter the name of the website you want to lookup the technologies for.

<aside class="success">
Remember — a list of technology items listed is an authenticated response!
</aside>

## Email Lookup

```ruby
require 'httparty'

email = HTTParty.get(
  "https://api.ful.io/api/email-search-website",
  query: { api_key: "<YOUR_API_KEY>", email: "example.com" }
)
puts email.body
```

```python
import requests

resp = requests.get(
    "https://api.ful.io/api/email-search-website",
    params={"api_key": "<YOUR_API_KEY>", "email": "example.com"}
)
print(resp.json())
```

```shell

curl --location \
  "https://api.ful.io/api/email-search-website?api_key=<YOUR_API_KEY>&email=example.com"

```

```javascript
const axios = require('axios');

axios.get('https://api.ful.io/api/email-search-website', {
  params: { api_key: '<YOUR_API_KEY>', email: 'example.com' }
})
.then(res => console.log(res.data));
```

> The above command returns JSON structured like this:

```json
{
  "domain": "example.com",
  "total unique emails found": 2,
  "total email occurrences": 10,
  "results_found": [
    {
      "Email": "abc@example.com",
      "URLs": [
        "https://ful.io/technology/analytics/moat",
        "https://ful.io/technology/cms/wolf-cms",
        "https://ful.io/technology/cms/solidpixels",
        "https://ful.io/technology/analytics/facebook-pixel"
      ]
    },
    {
      "Email": "xyz@example.com",
      "URLs": [
        "https://ful.io/technology/cms/pyrocms",
        "https://ful.io/technology/cms/flazio",
        "https://ful.io/technology/cms/indexhibit",
        "https://ful.io/technology/tag-managers",
        "https://ful.io/technology/cms/chameleon-system",
        "https://ful.io/technology/widgets/facebook"
      ]
    }
  ]
}
```

This endpoint retrieves all the emails (along with the source) associated with a website name.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://api.ful.io/api/email-search-website`

### URL Parameters

Parameter | Description
--------- | -----------
api_key | You have to paste the API key which has been assigned to you specifically.
email | Enter the name of the website you want to lookup the emails for.

<aside class="success">
Remember — a list of emails listed is an authenticated response!
</aside>

# Memberships & Credits

```ruby
require 'httparty'

subs = HTTParty.get(
  "https://api.ful.io/user/api/subscription-details",
  query: { api_key: "<YOUR_API_KEY>" }
)
puts subs.body
```

```python
import requests

resp = requests.get(
    "https://api.ful.io/user/api/subscription-details",
    params={"api_key": "<YOUR_API_KEY>"}
)
print(resp.json())
```

```shell

curl --location \
  "https://api.ful.io/user/api/subscription-details?api_key=<YOUR_API_KEY>"

```

```javascript
const axios = require('axios');

axios.get('https://api.ful.io/user/api/subscription-details', {
  params: { api_key: '<YOUR_API_KEY>' }
})
.then(res => console.log(res.data));
```

> The above command returns JSON structured like this:

```json
{
  "user_membership": {
    "id": 8,
    "user": 2,
    "membership": {
      "id": 2,
      "name": "Individual",
      "credit_limit": 0,
      "logins": 2,
      "tech_lookup_credits_limit": 5000,
      "email_lookup_credits_limit": 5000,
      "api_credits_limit": 250,
      "lead_generation_credtis_limit": 5
    },
    "membership_id": 2,
    "membership_name": "Individual",
    "start_date": "2025-04-08T16:30:16.156305Z",
    "end_date": "2025-05-08T16:30:16.155893Z",
    "remaining_credits": 0,
    "tech_lookup_remaining_credits": 4972,
    "email_lookup_remaining_credits": 4977,
    "api_remaining_credits": 240,
    "lead_generation_remaining_credtis": 1,
    "is_active": true
  }
}
```

This endpoint retrieves all the subscription details of your account including the remaining & used credits.

### HTTP Request

`GET https://api.ful.io/user/api/subscription-details`

### URL Parameters

Parameter | Description
--------- | -----------
api_key | You have to paste the API key which has been assigned to you specifically.

<aside class="success">
Remember — a list of emails listed is an authenticated response!
</aside>

