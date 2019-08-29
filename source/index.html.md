---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ

  - response


toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Social Discovery IQ API

Api Documentation for sending report orders via API.


# Authentication

> Sample Header parameters:

```ruby
apikey = 'FSDFSDF6AGUIRFIEJIIJFIEP590CDB2Q8'
secret = 'FSDFDS1LM26D5NSCHAQHK6VA4DSDSDSD3'
Content-Type = 'application/json'
Authorization = 'Basic c3RhZ2luZzpzdGdsdFnaW5n'
```


```javascript

```

> Make sure to replace `mingmingmingming` AND `swswswswswswswsw` with your API key and Secret.

Social Discovery uses API keys to allow access to the API.

Access and Keys are manually generated and given to specific users.

Social Discovery expects for the API key and SECRET KEY to be included in all API requests to the server in a header that looks like the following:

`apikey: mingmingmingming`

`secret: swswswswswswswsw`


<aside class="notice">
You must replace <code>mingmingmingming</code> and <code>swswswswswswswsw</code> with your personal API key and secret.
</aside>

# Orders

## Get All Orders

```ruby
OUTPUT
{
    "status": true,
    "people": [
        {
          1. #{person_hash} },
        {
          2. #{person_hash} }
    ]
}

```



```javascript

```

This endpoint retrieves all orders.

### HTTP Request

`GET http://staging.socialdiscoveryiq.com/api/v1/people`

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>

## Request an Order

> Raw hash base structure for the new order request.

```ruby
{
 "person":
  {"case_id": "case1000011",
   "first_name": "Michael",
   "middle_name": "John",
   "last_name": "Doe",
   "gender": "male",
   "dob": "01/19/1985",
   "alias": "Mike",
   "details":
    {"ethnicity": ["ethnicity"],
     "emails": [""],
     "phones":
      [{"phone_number": "9999999", "type": "Cell"},
       {"phone_number": "88888888", "type": "Home"}],
     "addresses":
      [{"type": "Current",
        "address": "",
        "city": "Los Angeles",
        "state": "California",
        "zip": "1630"}],
     "employment": ["maintenance"],
     "schools": ["New state college"],
     "relationships": ["brother"],
     "physical_descriptions": ["thin", "muscular"],
     "items_added": ""},
   "claim": "",
   "from": "",
   "orders_attributes":
    {"0":
      {"networks": "",
       "specifications": {"advance_options": ["Facebook - Friends"]},
       "kind": "iquick_scan"
      }
    },
   "description": "Test description"
   },
 "to": "Today"
}

OUTPUT
{
    "status": true,
    "person_id": "#{response_id}"
}
```


This endpoint request a new order.

### HTTP Request

`POST http://staging.socialdiscoveryiq.com/api/v1/people`

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>

### URL Parameters

Parameter | Description
--------- | -----------
person (required) | person hash as a parameter Validation: Must be a hash
`person[report_type]` (optional) | Must be one of `Social Media Quick Scan`, `Social Media Investigative Report`
`person[case_id]` (required) | Must be a String
`person[first_name]` (required) | Must be a String
`person[middle_name]` (required) | Must be a String
`person[last_name]` (required) | Must be a String
`person[gender]` (required) | Must be one of `male`, `female`, `unknown`
`person[dob]` (optional) | Format: `mm/dd/yyyy`. Must be a String
`person[alias]` (optional) | Must be a String
`person[details]` (required) | Must be a Hash (Details Hash)
`person[details][ethnicity]` (optional) | Should be in Array of Strings - Must be an array of any type
`person[details][emails]` (optional) | Should be in Array of Strings - Must be an array of any
`person[details][phones]` (optional) | Should be an Array of Hashes - Must be an array of nested elements
`person[details][phones][phone_number]` (optional) | Must be a String
`person[details][phones][type]` (optional) | Must be one of `Home`, `Cell`, `Work`, `Possible`, `Other`
`person[details][employments]` (optional) | Should be an array of Hashes - Must be an Array of nested elements
`person[details][employments][employer_type]` (optional) | Must be one of: `Previous Employer`, `Current Employer`
`person[details][employments][name]` (optional) | Must be a String
`person[details][employments][city_/_state]` (optional) | Must be a String
`person[details][employments][position]` (optional) | Must be a String
`person[details][employments][start_end_year]` (optional) | Must be a String
`person[details][educations]` (optional) | Array of Hashes - Must be an Array of nested elements
`person[details][educations][institution]` (optional) | Must be a String
`person[details][educations][institution_type]` (optional) | Must be a String
`person[details][educations][city_/_state]` (optional) | Must be a String
`person[details][educations][year_graduated]` (optional) | Must be a String
`person[details][educations][degree_type]` (optional) | Must be a String
`person[details][addresses]` (optional) | Array of Hashes - Must be an Array of nested elements
`person[details][addresses][type]` (optional) | Must be one of: `Current`, `Past`, `Possible`
`person[details][addresses][address]` (optional) | Must be a String
`person[details][addresses][city]` (optional) | Must be a String
`person[details][addresses][state]` (optional) | Must be a String
`person[details][addresses][zip]` (optional) | Must be a String
`person[details][employment]` (optional) | Must be an Array of any type
`person[details][schools]` (optional) | Must be an Array of any type
`person[details][relationships]` (optional) | Must be an Array of any type
`person[details][physical_descriptions]` (optional) | Must be an Array of any type
`person[details][date_range]` (optional) | Must be a String
`person[details][report_highlights]` (optional) | Must be a String
`person[details][items_added]` (optional) | Must be a String
`person[claim]` (optional) | Must be a String
`person[from]` (optional) | Must be a String
`person[orders_attributes]` (optional) | Must be a Hash
`person[orders_attributes][0]` (optional) | Must be a Hash
`person[orders_attributes][0][networks]` (optional) | Must be one of: `quick_check`, `analyst_quick_check`, `deep_dive`, `analyst_quick_check_plus`
`person[orders_attributes][0][specifications]` (optional) | Must be a Hash
`person[orders_attributes][0][specifications][advance_options]` (optional) | Must be an Array of any type
`person[orders_attributes][0][kind]` (optional) | Must be one of: `analyst_quick_check`, `iquick_scan`, `fetch_standard`
`person[description]` (optional) | Must be a String
`person[files_attributes]` (optional) | Can be multiple key pair values 0, 1, 2 etc - Must be a Hash
`person[files_attributes][0]` (optional) | Must be a Hash
`person[files_attributes][0][kind]` (optional) | Must be one of: `user_upload`
`person[files_attributes][0][attachment_attributes]` (optional) | Must be a Hash
`person[to]` (optional) | Must be a String



## Get a Specific Order

```ruby
OUTPUT

{
    "status": true,
    "people": [
        {
          #{person_hash}
        }
    ]
}
```
```javascript

```




This endpoint retrieves a specific order.

<aside class="notice">User can fetch his/her order by calling above url with specific id</aside>

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>

### HTTP Request

`GET http://staging.socialdiscoveryiq.com/api/v1/people/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID (required) | The ID of the order to retrieve

## Delete a Specific Oder

```ruby
OUTPUT
{          
  status: true, success: 'Person successfully Deleted!'
}
```


```javascript

```



This endpoint deletes a specific order.

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>

### HTTP Request

`DELETE http://staging.socialdiscoveryiq.com/api/v1/people/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to delete




## Completed Orders

```ruby
INPUT PARAMETERS
{          
  {case_ids: '123,343,23432,4545'}
}

OUTPUT
{
  status: true, orders: [
    {'case_id': '123', 'attachment': {'pdf': 's3_url', 'html': 's3_url'} }
    {'case_id': '343', 'attachment': {'pdf': 's3_url', 'html': 's3_url'} }
  ]
}
```


```javascript

```

This endpoint checks for completed orders.

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>

### HTTP Request

`GET http://staging.socialdiscoveryiq.com/api/v1/completed_orders?case_ids=<case_id>`

### URL Parameters

Parameter | Description
--------- | -----------
case_id | The ID of the completed orders to check


## IQUICK Scan Order

> Raw hash base structure for the new iquick scan order request.

```ruby
{
 "person":
  {"case_id": "case1000011",
   "first_name": "Michael",
   "middle_name": "John",
   "last_name": "Doe",
   "gender": "male",
   "dob": "01/19/1985",
   "alias": "Mike",
   "details":
    {"ethnicity": ["ethnicity"],
     "emails": [""],
     "phones":
      [{"phone_number": "9999999", "type": "Cell"},
       {"phone_number": "88888888", "type": "Home"}],
     "addresses":
      [{"type": "Current",
        "address": "",
        "city": "Los Angeles",
        "state": "California",
        "zip": "1630"}],
     "employment": ["maintenance"],
     "schools": ["New state college"],
     "relationships": ["brother"],
     "physical_descriptions": ["thin", "muscular"],
     "items_added": ""},
   "claim": "",
   "from": "",
   "orders_attributes":
    {"0":
      {"networks": "",
       "kind": "iquick_scan"
      }
    },
   "description": "Test description"
   },
   "to": "Today",
   "user_template":
     {"name": "social iquick scan",
      "content": {"illegal_drugs": "on", "weapons": "on", "profane_language": "on", "threats_against_third_parties": "on", "violent_acts": "on", "another_partys_race_religion": "on", "prior_employers_or_work": "on", "end_user": "on", "criminal_activity": "on", "tardiness": "on"}
     }
}

OUTPUT
{
    "status": true,
    "person_id": "#{response_id}"
}
```


This endpoint request a new order for iquick scan.

### HTTP Request

`POST http://staging.socialdiscoveryiq.com/api/v1/people`

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>



### URL Parameters

Same url parameter for requesting a new order. Iquick scan is added at the orders attribute.

Parameter | Description
--------- | -----------
`person[orders_attributes][0][kind]` (optional) | Must be `iquick_scan`


### Selected reference list 

These are the selected reference and option when ordering an Iquick Scan report.

* References to Illegal Drugs
* References to Weapons
* References to Profane Language
* References to Threats Against Third-Parties
* References to Violent Acts
* References to Another Party’s Race or Religion
* References to Prior Employers or Work
* References to End-User
* References to Criminal Activity
* References to Tardiness

## Fetch Standard Order
<aside class="default">
  <h3>(ON DEVELOPMENT)</h3>
</aside>

> Raw hash base structure for the new Fetch Standard order request.

```ruby
{
 "person":
  {"case_id": "case1000011",
   "first_name": "Michael",
   "middle_name": "John",
   "last_name": "Doe",
   "gender": "male",
   "dob": "01/19/1985",
   "alias": "Mike",
   "details":
    {"ethnicity": ["ethnicity"],
     "emails": [""],
     "phones":
      [{"phone_number": "9999999", "type": "Cell"},
       {"phone_number": "88888888", "type": "Home"}],
     "addresses":
      [{"type": "Current",
        "address": "",
        "city": "Los Angeles",
        "state": "California",
        "zip": "1630"}],
     "employment": ["maintenance"],
     "schools": ["New state college"],
     "relationships": ["brother"],
     "physical_descriptions": ["thin", "muscular"],
     "items_added": ""},
   "claim": "",
   "from": "",
   "orders_attributes":
    {"0":
      {"networks": "",
       "kind": "fetch_standard"
      }
    },
   "description": "Test description"
   },
 "to": "Today",
 "user_template":
   {"name": "Template new",
    "content": { "illegal_drugs": "on", "weapons": "on", "profane_language": "on", "threats_against_third_parties": "on", "violent_acts": "on", "another_partys_race_or_religion": "on", "prior_employers_or_work": "on", "end_user": "on", "criminal_activity": "on", "tardiness": "on", "volunteer_efforts": "on", "community_involvements": "on", "education": "on", "serving_in_a_leadership_role": "on", "participating_on_a_team": "on" }
   }

}

OUTPUT
{
    "status": true,
    "person_id": "#{response_id}"
}
```


This endpoint request a new order for fetch standard.
When ordering fetch standard, you need to add from these filters in template hash. 

### HTTP Request

`POST http://staging.socialdiscoveryiq.com/api/v1/people`

<aside class="success">
Remember — Authentication header included: apikey & secret
</aside>



### URL Parameters

Same url parameter for requesting a new order. Fetch Standard is added at the orders attribute.

Parameter | Description
--------- | -----------
`person[orders_attributes][0][kind]` (optional) | Must be `fetch_standard`


### Selected reference list 

These are the select options when ordering a Fetch Standard report. (Negative and Positive Filters)

### Negative Filters
* References to Illegal Drugs
* References to Weapons
* References to Profane Language
* References to Threats Against Third-Parties
* References to Violent Acts
* References to Another Party’s Race or Religion
* References to Prior Employers or Work
* References to End-User
* References to Criminal Activity
* References to Tardiness

### Positive Filters
* References to Volunteer Efforts
* References to Community Involvements
* References to Education
* References to Serving in a Leadership Role
* References to Participating on a Team




