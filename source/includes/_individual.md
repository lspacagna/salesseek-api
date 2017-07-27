# Individual API

## Get Individual

<blockquote class="highlight tab-request">
  <h3>Request Query</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>https://example.salesseek.net/api/individuals/de9e5749-23cb-4ff5-b6de-f1740978f08e</code></pre>

<blockquote class="highlight json tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>{
  "id": "de9e5749-23cb-4ff5-b6de-f1740978f08e",
  "full_name": "Aaron Henlow",
  "first_name": "Aaron",
  "last_name": "Henlow",
  "sortable_name": "Henlow, Aaron",
  "role": "Associate",
  "photo_url": "https://www.example.com/man.png",
  "organization_name": "Riffroute",
  "organization_id": "2b82b5b2-be2f-414a-b522-5d797ad57245",
  "locations": [
    ...
  ],
  "communication": [
    ...
  ],
  "custom_fields": {
    ...
  },
  "tags": [],
  "comments": "",
  "type": "individuals",
  "last_viewed": "2017-07-27T13:48:49.535554",
  "modified": "2017-03-31T11:14:42.813813",
  "last_modified_by_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
  "owner_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
  "creator_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
  "unsubscribed_all": false,
  "created": "2017-03-31T11:14:42.813813",
  "source": null,
  "source_id": null,
  "became_lead_date": null,
  "is_favorite": false,
  "uri": "individuals/de9e5749-23cb-4ff5-b6de-f1740978f08e",
}</code></pre>

### Request URL

Returns the individual matching the `individual_id`

`GET https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be retrieved.

## Add Individual

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>{
  "owner": {
    "id": "8da68e42-baef-42b2-9c72-4a00b5e20082",
    "name": "SalesSeek Support"
  },
  "photo_url": "http://www.salesseek.com/avatar.jpg",
  "first_name": "First",
  "last_name": "Last",
  "role": "CEO",
  "organization": {
    "id": "757daa37-ec92-4e71-9727-1b4f2bbb58f9"
  },
  "communication": [
    {
      "name": "Work",
      "medium": "phone",
      "value": "+44 20 3514 2513"
    },
    {
      "name": "Work",
      "medium": "email",
      "value": "example@salesseek.com"
    }
  ],
  "comments": "He is mainly interested in developing new business in EMEA",
  "source": {
    "id": "fef852d5-a77d-4d3f-b335-c4289b201c61",
  },
  "locations": [
    {
      "address": "Test Location"
    }
  ]
}</code></pre> 

<blockquote class="highlight json tab-response">
  <h3>Response Body</h3>
</blockquote>

<blockquote class="highlight tab-response">
  <a href="#get-individual">See Get Individual</a>
</blockquote>

### Request URL

Creates a new Individual and returns the resulting Individual.

`POST https://{CLIENT_ID}.salesseek.net/api/individuals/`

## Update Individual

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>{
  "first_name": "New",
  "last_name": "Name"
}</code></pre>

<blockquote class="highlight json tab-response">
  <h3>Response Body</h3>
</blockquote>

<blockquote class="highlight tab-response">
  <a href="#get-individual">See Get Individual</a>
</blockquote>

### Request URL

Updates an Individual by `individual_id` and returns the resulting Individual. Only fields passed in the request body are updated. 

`POST https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be updated.

## Delete Individual

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>null</code></pre>

Deletes the individual matching the `individual_id`

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/individuals/{individual_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`individual_id` | The unique ID for the individual to be updated.

## List Individuals

## Search Individuals

