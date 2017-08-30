# Custom Field API

## Custom Field Attributes

> An example response body for a custom field would look like this:

```json
{
	"id": "409306ef-1e5c-4763-836a-819e65646da9",
	"name": "Data Status",
	"type": "dropDown",
    "view": "individuals",
    "required": false,
    "options": [
      {
        "id": "f84cca3b-b096-4331-9f40-dd73d830a8b4",
        "value": "subscribed"
      },
      {
        "id": "58562322-0efc-4ed8-8eb3-e5b05f0f5501",
        "value": "unsubscribed"
      },
      {
        "id": "0ff89e07-ff32-4082-93f9-d048d4439b29",
        "value": "pending"
      },
      {
        "id": "6fc3036a-8ccd-428a-b609-639d8ac438b9",
        "value": "cleaned"
      }
    ],
    "value": {
      "options": [
        {
          "id": "f84cca3b-b096-4331-9f40-dd73d830a8b4",
          "value": "subscribed"
        },
        {
          "id": "58562322-0efc-4ed8-8eb3-e5b05f0f5501",
          "value": "unsubscribed"
        },
        {
          "id": "0ff89e07-ff32-4082-93f9-d048d4439b29",
          "value": "pending"
        },
        {
          "id": "6fc3036a-8ccd-428a-b609-639d8ac438b9",
          "value": "cleaned"
        }
      ]
    },
    "creator_id": "8baadb17-d37e-47f7-b116-0f15c06f297e",
    "last_modified_by_id": "8baadb17-d37e-47f7-b116-0f15c06f297e",
    "owner_id": "8baadb17-d37e-47f7-b116-0f15c06f297e",
    "created": "2017-04-28T16:15:08.434816",
    "modified": "2017-04-28T16:15:08.434816",
   	"order": 3,
    "default": null,
    "params": null, 
  }
```

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this custom field **String**
`name` 	  | The name for the custom field, this will appear in the SalesSeek UI **String**
`type`    | The type of custom field (`text`,`dropDown`, `checkbox`, `currency`, `date`, `individual`, `number`, `organization`, `paragraph`, `url`, `urlImage`)**Enum (String)**
`view`	  | The record type the custom field should appear on (`individuals`, `organizartions`, `opportunities`) **Enum (String)**
`required` | Set to `true` if this field is a required field **Boolean**
`options` | List of options if field type is set to `dropDown` **Object**
`options[x].id` | ID for the option in the dropdown custom field **String**
`options[x].value` | The value for the option in the dropdown custom field **String**
`value` | TODO
`creator_id` | ID for the [User](#user-api) that created this custom field **String**
`last_modified_by_id` | The ID for the [User](#user-api) that last modified this custom field **String**
`owner_id` | The ID for the [User](#user-api) that owns this custom field **String**
`created` | Custom field creation timestamp **Timestamp (ISO 8601)**
`modified`| Custom field last modified timestamp **Timestamp (ISO 8601)**
`order` | The position that this custom field should be displayed in the UI **Integer**
`default` | The default value for the custom field **(Mixed)**
`params` | TODO




## Get Custom Field

Returns the custom field matching the `custom_field_id`

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/custom_fields/{custom_field_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`custom_field_id` | The ID for the custom field you'd like to retrieve **String**




## Create Custom Field

> An example request body to create a date custom field called 'First Seen Date' on individuals would look like:

```json
{
  "name": "First Seen Date",
  "type": "date",
  "view": "individuals",
  "value": {
    "default": ""
  },
  "required": false
}
```

Creates a new custom field and then returns the newly created custom field.

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/custom_fields/`




## Update Custom Field

> A sample request body to custom field name to 'Last Seen Date' would be:

```json
{
  "name": "Last Seen Date"
}
```


Updates a custom field by `custom_field_id` and returns the resulting custom field. 

### Request URL

<span class='verb post'>POST</span> `https://{CLIENT_ID}.salesseek.net/api/custom_fields/{custom_field_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`custom_field_id` | The unique ID for the individual to be updated.

### Request Body

The only fields updated are the one passed on the request body JSON. You can pass any [attribute](#custom-field-attributes) to update. 



## Delete Custom Field

Deletes the custom field matching the `custom_field_id`

### Request URL

<span class='verb delete'>DELETE</span> `https://{CLIENT_ID}.salesseek.net/api/custom_fields/{custom_field_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`custom_field_id` | The unique ID for the custom field to be updated.




## List Custom Fields

> An example request to get all custom fields for the Individual view in your SalesSeek account:

```http
GET https://example.salesseek.net/api/custom_fields?start=0&rows=-1&order_by=modified%20desc&filter=view%3Dindividuals
```

> The reponse header contains the following information:

```
Records-Rows: 50
Records-Start: 0
Records-Total: 2000
```

Returns the list of custom fields for the chosen record type.

### Request URL

<span class='verb get'>GET</span> `https://{CLIENT_ID}.salesseek.net/api/custom_fields`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by desc or asc
`filter=view` | The record type that the custom fields are related to (`individuals`, `deals`, `organizations`)

### Response Header Parameters

Parameter |  Description
--------- | ------- 
`Records-Rows` | The number of rows returned in this request
`Records-Start` | The start number of rows in this request (out of total)
`Records-Total` | The total number of rows available