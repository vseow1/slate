---
title: Spacio API Reference

language_tabs:
  - shell

toc_footers:
  # - <a href='#'></a>
  # - <a href='#'></a>

includes:
  - errors
  - changelog

search: true
---

# Introduction

The following endpoints are currently available for the production and beta Spacio API and call rates are currently limited to 12,000 hourly by default on key creation. If you require this cap to be increased or have any other inquiries regarding the API, please reach out to us at support[at]spac.io 

* **Production:** https://ws.spac.io/api/v1/
* **Beta:** https://ws.spac.io/api-stage/v1/

# Properties

## Agent Properties

```shell
curl "https://ws.spac.io/api/v1/getProperties"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'ukey=[AGENT UKEY]' 
```

> The above command returns JSON structured like this:

```json
{
    "1": {
        "title": "Beautiful Waterfront Apartment in English Bay",
        "price": "2300000",
        "beds": 2,
        "baths": 2,
        "dimens": -1,
        "type": "Apartment",
        "email": "hello[at]spac.io",
        "addr1": "231 Beach Ave.",
        "addr2": "",
        "url": "https://spac.io",
        "sid": 10191,
        "mlsNo": "AB123456",
        "image": "https://s3.amazonaws.com/spacio-user-images/55c6ca75aace0f500cabb8b5_property.jpg"
    },
    "2": {
        "title": "Penthouse In East Village, Close To Restaurants",
        "price": "$2,500,000",
        "beds": -1,
        "baths": -1,
        "dimens": -1,
        "type": "Apartment",
        "email": "hello[at]spac.io",
        "addr1": "324 East 14th Street",
        "addr2": "",
        "url": "",
        "sid": 10512,
        "mlsNo": "CD234567",
        "image": "https://s3.amazonaws.com/spacio-user-images/560b2f2caace0f3c758b4567_property.jpg"
    }
}
```

This endpoint retrieves all properties associated to the agent.

### HTTP Request

`POST https://ws.spac.io/api/v1/getProperties`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
ukey | Agent UKEY 

## Single Property

```shell
curl "https://ws.spac.io/api/v1/getProperty"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'sid=[PROPERTY SPACIO ID]' 
```

> The above command returns JSON structured like this:

```json
{
    "title": "Beautiful Waterfront Apartment in English Bay",
    "price": "2300000",
    "beds": 2,
    "baths": 2,
    "dimens": -1,
    "type": "Apartment",
    "email": "hello[at]spac.io",
    "addr1": "231 Beach Ave.",
    "addr2": "",
    "url": "https://spac.io",
    "sid": 10191,
    "mlsNo": "AB123456",
    "image": "https://s3.amazonaws.com/spacio-user-images/55c6ca75aace0f500cabb8b5_property.jpg"
}
```

This endpoint retrieves a property associated to the `sid` (Spacio property ID).

### HTTP Request

`POST https://ws.spac.io/api/v1/getProperty`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
sid | Spacio property ID 

# Leads

## Property Leads

```shell
curl "https://ws.spac.io/api/v1/getRegistrants"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'sid=[PROPERTY SPACIO ID]'
  -F 'atoken=[AGENT ACCESS TOKEN]'  
```

> The above command returns JSON structured like this:

```json
{
    "1": {
        "name": "Scott Lang",
        "email": "sl@example.com",
        "phone": "234-567-8900",
        "hasAgent": "NO",
        "hasFinancing": "NO",
        "answersObj": {
            "0": {
                "questionObj": {
                    "question": "Are you working with an agent?",
                    "questionCN": "您有否地产经纪代理?",
                    "type": "agent",
                    "caption": "Are you working with an agent? (Agent name and contact fields will appear if Yes is selected)",
                    "questionID": "583632da2b3077566f53af21"
                },
                "answer": "NO"
            },
            "1": {
                "questionObj": {
                    "questionCN": "您有否抵押贷款批准?",
                    "type": "yn",
                    "caption": "Are you mortgage pre-approved?",
                    "question": "Are you mortgage pre-approved?",
                    "questionID": "583632da2b3077566f53af1b"
                },
                "answer": "NO"
            },
            "2": {
                "questionObj": {
                    "question": "Do you currently rent or own?",
                    "questionCN": "您現在住的是?",
                    "type": "mc",
                    "choices": {
                        "0": {
                            "answer": "Own",
                            "answerCN": "购买",
                            "type": "radio"
                        },
                        "1": {
                            "answer": "Rent",
                            "answerCN": "租赁",
                            "type": "radio"
                        }
                    },
                    "questionID": "5910f9d492127dee0c2bb8cf"
                },
                "answer": "Own"
            },
            "3": {
                "questionObj": {
                    "question": "How did you hear about this open house?",
                    "questionCN": "您是如何听说到我们的",
                    "type": "text",
                    "questionID": "5910f9f392127d7e052bb8cf"
                },
                "answer": "N/A"
            }
        },
        "dateCreated": "2017-05-08 11:11:54"
    }
}
```

This endpoint retrieves all leads associated to the property.

### HTTP Request

`POST https://ws.spac.io/api/v1/getRegistrants`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
sid | Spacio property ID
atoken | Agent access token

# Access Tokens

## Access Token (Agent)

```shell
curl "https://ws.spac.io/api/v1/getAccessToken"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'email=[AGENT EMAIL]' 
```

> The above command returns JSON structured like this:

```json
{
    "email": "agent@example.com",
    "ukey": "agentUkey",
    "accessToken": "ZtKH5J76DN5DyQ3R"
}
```

This endpoint retrieves an access token for the agent.

### HTTP Request

`POST https://ws.spac.io/api/v1/getAccessToken`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
email | Email for the agent

## Access Token (Brokerage Manager)

```shell
curl "https://ws.spac.io/api/v1/getAccessTokenBM"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'email=[BROKERAGE MANAGER EMAIL]' 
```

> The above command returns JSON structured like this:

```json
{
    "email": "manager@example.com",
    "accessToken": "ZtKH5J76DN5DyQ3R"
}
```

This endpoint retrieves an access token for the brokerage manager. Note that brokerage managers do not return an `ukey`.

### HTTP Request

`POST https://ws.spac.io/api/v1/getAccessTokenBM`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
email | Email for the brokerage manager

# Brokerages

<aside class="notice">
The <code>bid​</code> (Brokerage ID) is a shortcode we assign to brokerages and will be provided upon request. 
</aside>

## Brokerage Leads

```shell
curl "https://ws.spac.io/api/v1/getRegistrantsByBrokerage​"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'bid=[BROKERAGE ID]'
  -F 'startDate=[YYYY-MM-DD]' 
  -F 'endDate=[YYYY-MM-DD]'  
```

> The above command returns JSON structured like this:

```json
{ 
  "1": { 
    "id": "5cc84e8a92127d360d20be36",
    "name": "John", 
    "email": "jsmith@example.com", 
    "phone": "123-456-7890", 
    "hasAgent": "NO", 
    "hasFinancing": "NO", 
    "isBroker": "NO", 
    "answersObj": [
      { 
        "question": "Are you working with an agent?", 
        "answer": "NO"
      },
      {
        "question": "How did you hear about this open house?",
        "answer": "Other", 
      },
      {
        "question": "Are you mortgage pre-approved?", 
        "answer": "NO" 
      }
    ], 
    "dateCreated": "2019-02-01 09:17:03",
    "sid": 000001,
    "plid": "AAA-001",
    "agentEmail": "agent1@example.com" 
  }, 
  "2": { 
    "id": "5cc8540f92127df51f20be36",
    "name": "Alex Sanders", 
    "email": "alexs@example.com", 
    "phone": "987-654-3210", 
    "hasAgent": "UNKNOWN", 
    "hasFinancing": "UNKNOWN", 
    "isBroker": "NO", 
    "answersObj": [], 
    "dateCreated": "2019-02-01 08:33:28",
    "sid": 000002,
    "plid": "BBB-002",
    "agentEmail": "agent2@example.com"  
  }, 
  "3": { 
    "id": "5cc6f7f292127d1b7d20be36",
    "name": "Bob Cory", 
    "email": "bcory@example.com", 
    "phone": "2223334444", 
    "hasAgent": "YES", 
    "hasFinancing": "YES", 
    "isBroker": "NO", 
    "answersObj": [
      { 
        "question": "Are you working with an agent?", 
        "answer": "YES"
      },
      {
        "question": "How did you hear about this open house?",
        "answer": "Social Media", 
      },
      {
        "question": "Are you mortgage pre-approved?", 
        "answer": "YES" 
      }
    ], 
    "dateCreated": "2019-02-01 05:56:52",
    "sid": 000003,
    "plid": "CCC-003",
    "agentEmail": "agent3@example.com"  
  }
} 
```

This endpoint retrieves a list of leads within the specified date range.

### HTTP Request

`POST https://ws.spac.io/api/v1/getRegistrantsByBrokerage​`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
bid | Brokerage ID
startDate | Start date 
endDate | End date

<aside class="notice">
Note that the <code>dateCreated</code> may show as an exact timestamp (i.e. <code>2019-05-02 22:00:00</code>) and this is due to defaults in place when adding a visitor manually. Please refer to the tutorial video <a href='https://spac.io/tutorials/#add-visitor' target="_blank" rel="noreferrer">here</a> (https://spac.io/tutorials/#add-visitor) for more details.
</aside>

`startDate​` and `endDate​` can accept any calendar date in `YYYY-MM-DD` as a valid format. Although not required, times are stored and displayed in UTC so you may want to pad an extra day to the start or end dates to ensure results are complete. For example, if one was to look up active users from Aug. 1st to Aug. 14th, then they may want to set the `startDate​` as 2018-07-31​ and `endDate​` as 2018-08-15​. This extra step can be omitted if it’s being considered or the conversion is already handled in advance. 

## [BETA] Claimed Accounts

```shell
curl "https://ws.spac.io/api-stage/v1/getClaimedList"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'bid=[BROKERAGE ID]' 
```

> The above command returns JSON structured like this:

```json
{
  "agent1@example.com", 
  "agent2@example.com", 
  "agent3@example.com", 
  "agent4@example.com", 
  "agent5@example.com"
}
```

This endpoint retrieves a claimed list of agent emails.

### HTTP Request

`POST https://ws.spac.io/api-stage/v1/getClaimedList`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
bid | Brokerage ID

## [BETA] User Activity

```shell
curl "https://ws.spac.io/api-stage/v1/getActivityList"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'bid=[BROKERAGE ID]'
  -F 'startDate=[YYYY-MM-DD]' 
  -F 'endDate=[YYYY-MM-DD]'  
```

> The above command returns JSON structured like this:

```json
{ 
  "1": { 
    "email": "agent1@example.com", 
    "lastActive": "2018-06-28 01:08:21" 
  }, 
  "2": { 
    "email": "agent2@example.com", 
    "lastActive": "2018-04-27 01:37:59" 
  }, 
  "3": { 
    "email": "agent3@example.com", 
    "lastActive": "2018-06-09 11:06:38" 
  }
}
```

This endpoint retrieves a list of agent emails within the specified date range.

### HTTP Request

`POST https://ws.spac.io/api-stage/v1/getActivityList`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
bid | Brokerage ID
startDate | Start date 
endDate | End date

`startDate​` and `endDate​` can accept any calendar date in `YYYY-MM-DD` as a valid format. Although not required, times are stored and displayed in UTC so you may want to pad an extra day to the start or end dates to ensure results are complete. For example, if one was to look up active users from Aug. 1st to Aug. 14th, then they may want to set the `startDate​` as 2018-07-31​ and `endDate​` as 2018-08-15​. This extra step can be omitted if it’s being considered or the conversion is already handled in advance. 

## [BETA] Open House Session Counts

```shell
curl "https://ws.spac.io/api-stage/v1/getOHSessionCounts"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'bid=[BROKERAGE ID]'
  -F 'startDate=[YYYY-MM-DD]' 
  -F 'endDate=[YYYY-MM-DD]'  
```

> The above command returns JSON structured like this:

```json
{ 
  "1": { 
    "dateHosted": "2018-08-05 01:14:57", 
    "leadsCount": 0, 
    "propertyAddress": "164 Little Stannard Beach Road", 
    "propertyCity": "Westbrook", 
    "propertyState": "CT", 
    "propertyZip": "06498" 
  }, 
  "2": { 
    "dateHosted": "2018-08-05 04:52:46", 
    "leadsCount": 7, 
    "propertyAddress": "10 Southridge Road", 
    "propertyCity": "Southbury", 
    "propertyState": "CT", 
    "propertyZip": "06488" 
  }, 
  "3": { 
    "dateHosted": "2018-08-05 05:06:31", 
    "leadsCount": 1, 
    "propertyAddress": "66 White Oak Shade road", 
    "propertyCity": "New Canaan", 
    "propertyState": "CT", 
    "propertyZip": "06840" 
  }
}
```

This endpoint retrieves a list of open house session counts within the specified date range.

### HTTP Request

`POST https://ws.spac.io/api-stage/v1/getOHSessionCounts`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
bid | Brokerage ID
startDate | Start date 
endDate | End date

`startDate​` and `endDate​` can accept any calendar date in `YYYY-MM-DD` as a valid format. Although not required, times are stored and displayed in UTC so you may want to pad an extra day to the start or end dates to ensure results are complete. For example, if one was to look up active users from Aug. 1st to Aug. 14th, then they may want to set the `startDate​` as 2018-07-31​ and `endDate​` as 2018-08-15​. This extra step can be omitted if it’s being considered or the conversion is already handled in advance.

## [BETA] Brokerage Leads

```shell
curl "https://ws.spac.io/api-stage/v1/getRegistrantsByBrokerage​"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'bid=[BROKERAGE ID]'
  -F 'startDate=[YYYY-MM-DD]' 
  -F 'endDate=[YYYY-MM-DD]'
  -F 'page=[PAGE NUMBER]'
```

> The above command returns JSON structured like this:

```json
{ 
  "info": {
        "resultsOnPage": 100,
        "totalCount": 123,
        "pageNumber": 1,
        "totalPages": 2
  },
  "data": [
    {
      "id": "5cc84e8a92127d360d20be36",
      "name": "John", 
      "email": "jsmith@example.com", 
      "phone": "123-456-7890", 
      "hasAgent": "NO", 
      "hasFinancing": "NO", 
      "isBroker": "NO", 
      "answersObj": [
        { 
          "question": "Are you working with an agent?", 
          "answer": "NO"
        },
        {
          "question": "How did you hear about this open house?",
          "answer": "Other", 
        },
        {
          "question": "Are you mortgage pre-approved?", 
          "answer": "NO" 
        }
      ], 
      "dateCreated": "2019-02-01 09:17:03",
      "sid": 000001,
      "plid": "AAA-001",
      "agentEmail": "agent1@example.com" 
    }, 
    { 
      "id": "5cc8540f92127df51f20be36",
      "name": "Alex Sanders", 
      "email": "alexs@example.com", 
      "phone": "987-654-3210", 
      "hasAgent": "UNKNOWN", 
      "hasFinancing": "UNKNOWN", 
      "isBroker": "NO", 
      "answersObj": [], 
      "dateCreated": "2019-02-01 08:33:28",
      "sid": 000002,
      "plid": "BBB-002",
      "agentEmail": "agent2@example.com"  
    }, 
    { 
      "id": "5cc6f7f292127d1b7d20be36",
      "name": "Bob Cory", 
      "email": "bcory@example.com", 
      "phone": "2223334444", 
      "hasAgent": "YES", 
      "hasFinancing": "YES", 
      "isBroker": "NO", 
      "answersObj": [
        { 
          "question": "Are you working with an agent?", 
          "answer": "YES"
        },
        {
          "question": "How did you hear about this open house?",
          "answer": "Social Media", 
        },
        {
          "question": "Are you mortgage pre-approved?", 
          "answer": "YES" 
        }
      ], 
      "dateCreated": "2019-02-01 05:56:52",
      "sid": 000003,
      "plid": "CCC-003",
      "agentEmail": "agent3@example.com"  
    }
  ]
} 
```

This endpoint retrieves a list of leads within the specified date range.

### HTTP Request

`POST https://ws.spac.io/api-stage/v1/getRegistrantsByBrokerage​`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
bid | Brokerage ID
startDate | Start date 
endDate | End date
page | Page number

<aside class="notice">
Note that the <code>dateCreated</code> may show as an exact timestamp (i.e. <code>2019-05-02 22:00:00</code>) and this is due to defaults in place when adding a visitor manually. Please refer to the tutorial video <a href='https://spac.io/tutorials/#add-visitor' target="_blank" rel="noreferrer">here</a> (https://spac.io/tutorials/#add-visitor) for more details.
</aside>

`startDate​` and `endDate​` can accept any calendar date in `YYYY-MM-DD` as a valid format. Although not required, times are stored and displayed in UTC so you may want to pad an extra day to the start or end dates to ensure results are complete. For example, if one was to look up active users from Aug. 1st to Aug. 14th, then they may want to set the `startDate​` as 2018-07-31​ and `endDate​` as 2018-08-15​. This extra step can be omitted if it’s being considered or the conversion is already handled in advance.

# Teams

## [BETA] Team Leads

```shell
curl "https://ws.spac.io/api-stage/v1/getRegistrantsByTeam"
  -H "apikey:[YOUR KEY HERE]" 
  -X POST
  -F 'tid=[TEAM ID]'
  -F 'startDate=[YYYY-MM-DD]' 
  -F 'endDate=[YYYY-MM-DD]'
  -F 'page=[PAGE NUMBER]'
```

> The above command returns JSON structured like this:

```json
{ 
  "info": {
        "resultsOnPage": 100,
        "totalCount": 123,
        "pageNumber": 1,
        "totalPages": 2
  },
  "data": [
    {
      "id": "5cc84e8a92127d360d20be36",
      "name": "John", 
      "email": "jsmith@example.com", 
      "phone": "123-456-7890", 
      "hasAgent": "NO", 
      "hasFinancing": "NO", 
      "isBroker": "NO", 
      "answersObj": [
        { 
          "question": "Are you working with an agent?", 
          "answer": "NO"
        },
        {
          "question": "How did you hear about this open house?",
          "answer": "Other", 
        },
        {
          "question": "Are you mortgage pre-approved?", 
          "answer": "NO" 
        }
      ], 
      "dateCreated": "2019-02-01 09:17:03",
      "sid": 000001,
      "plid": "AAA-001",
      "agentEmail": "agent1@example.com" 
    }, 
    { 
      "id": "5cc8540f92127df51f20be36",
      "name": "Alex Sanders", 
      "email": "alexs@example.com", 
      "phone": "987-654-3210", 
      "hasAgent": "UNKNOWN", 
      "hasFinancing": "UNKNOWN", 
      "isBroker": "NO", 
      "answersObj": [], 
      "dateCreated": "2019-02-01 08:33:28",
      "sid": 000002,
      "plid": "BBB-002",
      "agentEmail": "agent2@example.com"  
    }, 
    { 
      "id": "5cc6f7f292127d1b7d20be36",
      "name": "Bob Cory", 
      "email": "bcory@example.com", 
      "phone": "2223334444", 
      "hasAgent": "YES", 
      "hasFinancing": "YES", 
      "isBroker": "NO", 
      "answersObj": [
        { 
          "question": "Are you working with an agent?", 
          "answer": "YES"
        },
        {
          "question": "How did you hear about this open house?",
          "answer": "Social Media", 
        },
        {
          "question": "Are you mortgage pre-approved?", 
          "answer": "YES" 
        }
      ], 
      "dateCreated": "2019-02-01 05:56:52",
      "sid": 000003,
      "plid": "CCC-003",
      "agentEmail": "agent3@example.com"  
    }
  ]
} 
```

This endpoint retrieves a list of leads within the specified date range.

### HTTP Request

`POST https://ws.spac.io/api-stage/v1/getRegistrantsByTeam`

### Query Parameters

Parameter | Description
--------- | -----------
apikey | Assigned API key
tid | Team ID
startDate | Start date 
endDate | End date
page | Page number

<aside class="notice">
Note that the <code>dateCreated</code> may show as an exact timestamp (i.e. <code>2019-05-02 22:00:00</code>) and this is due to defaults in place when adding a visitor manually. Please refer to the tutorial video <a href='https://spac.io/tutorials/#add-visitor' target="_blank" rel="noreferrer">here</a> (https://spac.io/tutorials/#add-visitor) for more details.
</aside>

`startDate​` and `endDate​` can accept any calendar date in `YYYY-MM-DD` as a valid format. Although not required, times are stored and displayed in UTC so you may want to pad an extra day to the start or end dates to ensure results are complete. For example, if one was to look up active users from Aug. 1st to Aug. 14th, then they may want to set the `startDate​` as 2018-07-31​ and `endDate​` as 2018-08-15​. This extra step can be omitted if it’s being considered or the conversion is already handled in advance.