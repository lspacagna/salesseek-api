# Group Page API

The Group Pages API should be used in conjunction with the [Group API](#group-api). The Group API contains the metadata for each group. The Group Pages API is used to return records associated with a group in a paginated form.

## Group Page Attributes

> A sample Group Pages response on an organization group would look like:

```json
{
  "columns": [
    "photo_url",
    "first_name",
    "last_name",
    "organization.name",
    "email",
    "phone"
  ],
  "rows": [
    {
      "id": "dc1aba21-37ad-4feb-8dca-3d7ce4ec29fe",
      "cells": [
        "",
        "Anna",
        "Walker",
        "Woking Leal",
        [
          {
            "name": "Work",
            "value": "dangerdanger@mailinator.com"
          }
        ],
        []
      ]
    },
    {
      "id": "a303df0a-8caf-499c-83d8-e8455a5978b9",
      "cells": [
        "",
        "David",
        "Romero",
        "Linkbuzz",
        [
          {
            "name": "Work",
            "value": "david.romero@suremail.info"
          }
        ],
        [
          {
            "name": "Work",
            "value": "6-(186)598-3830"
          }
        ]
      ]
    }
  ],
  "order_by": [
    "full_name",
    "asc"
  ],
  "totals": null
}
```

Parameter |  Description
--------- | ------- 
`columns` | Array containing the column names in the returned data **Array (String)**
`rows` 	  | Array containing the rows of data returned as objects **Array (Object)**
`order_by` | Array of the values the returned data is ordered by **Array (String)**
`totals` | TODO


## Get Group Page

> A sample request for a maximum of 50 records from a group could look like: 

```http
GET https://example.salesseek.net/api/group_pages?item_type=individuals&group_id=5f1e7c37-2a27-4dab-b834-7f0054303555&rows=50&columns=photo_url,first_name,last_name,organization.name,email,phone,source&order_by=full_name%20asc
```

Returns the requested number of records from `group_id`

`GET https://https://{CLIENT_ID}.salesseek.net/api/group_pages`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`item_type` | The type of record to return in this group page (`individuals`, `organizations`, `opportunities`, `tasks`)
`group_id` |  The ID for the group to retrieve records from
`rows` | The maximum number of organizations to be returned
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by `&desc` or `&asc`