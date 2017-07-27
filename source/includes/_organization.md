# Organization API

## List Organizations

<blockquote class="highlight tab-request">
  <h3>Request Query</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>https://example.salesseek.net/api/organizations?rows=-1&amp;start=0&amp;order_by="name asc"</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Header</h3>
</blockquote>

<pre class="highlight json tab-response"><code>Records-Rows: 50
Records-Start: 0
Records-Total: 2000</code></pre> 

<blockquote class="highlight json tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>[
	{
		"type": "organizations",
		"name": "Sample Organization",
		"creator_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
		"tags": [],
		"created": "2017-07-03T09:24:29.482483",
		"creator": {
			...
		},
		"version": 0,
		"abbreviation": "TAO1",
		"permissions": [
			"salesseek.core.all_permissions",
			"salesseek.core.edit",
			"salesseek.core.view"
		],
		"owner_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
		"uri": "organizations/dd5a5f36-c3de-4248-bb28-ca521f32bf71",
		"owner": {
			...
		},
		"latest": true,
		"last_modified_by_id": "40575ca1-381c-4542-a556-e3c2d81ef67e",
		"short_id": "dd5a5f36-c3de-4248-bb28-ca521f32bf71",
		"twitter_screen_name": null,
		"communication": [
			...
		],
		"custom_field.2b916cc8-0b48-4d24-83d8-e5996b15f8c5": "101",
		"facebook_username": null,
		"modified": "2017-07-03T09:24:29.482483",
		"related_file_ids": [],
		"locations": [],
		"comments": ""
	},
	...
]</code></pre> 

Returns the entire list of organizations in your SalesSeek account.

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`rows` | The maximum number of organizations to be returned.
`start` | The row number to start to retrieve data. (0 for start)
`order_by` | Results are ordered by the provided field name followed by &amp;desc or &amp;asc


## Search Organizations	


<blockquote class="highlight tab-request">
  <h3>Request Query</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>https://example.salesseek.net/api/organizations?search=example%20organization</code></pre> 


<blockquote class="highlight tab-response">
  <h3>Response</h3>
</blockquote>

<blockquote class="highlight tab-response">
  <a href="#list-organizations">See List Orgnaizations</a>
</blockquote>


Provides the the subset of organizations where the Organization name matches the search_string. The set of information returned is reduced to maintain search performance.


### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations?search=search_string`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`search_string` | Searches for all Organizations containing this string.


## Get Organization

<blockquote class="highlight tab-request">
  <h3>Request Query</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>https://example.salesseek.net/api/organizations/c2401213-a985-427b-b7d3-ad697d439b8c</code></pre> 

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>{
  "name": "Test",
  "id": "cbebcd82-599e-4d53-8533-cce4c16a3bc5",
  "short_id": "cbebcd82-599e-4d53-8533-cce4c16a3ba5",
  "uri": "organizations/cbebcd82-599e-4d53-8533-cce4c16a3bc5",
  "custom_fields": {},
  "facebook_id": null,
  "abbreviation": "EXA1",
  "owner_id": "8da68e42-baef-42b2-9c73-4a00b5e20082",
  "creator_id": "8da68e42-baef-42b2-9c73-4a00b5e20082",
  "modified": "2017-07-26T13:47:00.744047",
  "comments": "",
  "last_modified_by_id": "8da68e42-baef-42b2-9c72-4a00b5e20082",
  "created": "2017-07-26T13:47:00.744047",
  "tags": [],
  "is_favorite": false,
  "type": "organizations",
  "communication": [
  	...
  ],
  "locations": [
  	...
  ],
}
</code></pre> 

Returns the unique organization matching the `organization_id`

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`









## Create Organization

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>{
  name: "Example Company",
  comments: "This company is completely focused on marketing",
  "owner": {
    "id": "8da68e42-baef-42b2-9d72-4a00b5e20083",
    "name": "SalesSeek"
  },
  "communication": [
    {
      "name": "Work",
      "medium": "phone",
      "value": "+155448855",
      "comments": "from 8:00 to 17:00"
    },
    {
    	"name": "Work"
      "medium": "email",
      "value": "example@example.com",
      "comments": "From Mon to Sat"
    },
    {
      "medium": "social",
      "name": "linkedin"
      "value": "https://www.linkedin.com/in/salesseek",
    },
    {
      "medium": "social",
      "name": "twitter"
      "value": "https://twitter.com/SalesSeek",
    },
    {
      "medium": "social",
      "name": "facebook"
      "value": "https://www.facebook.com/SalesSeek?fref=ts",
    },
  ],
  locations: [
    0: {
      address: "212B Baker Street"
      comments: "Mon to Fri"
    }
  ]
}</code></pre> 


<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<blockquote class="highlight tab-response">
  <a href="#get-organization">See Get Orgnaization</a>
</blockquote>

Creates a new organization and then returns the newly created organization.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/organizations`





## Update Organization

<blockquote class="highlight tab-request">
  <h3>Request Body</h3>
</blockquote>

<pre class="highlight json-doc tab-request"><code>{
	"name": "New Example"
}</code></pre> 



<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<blockquote class="highlight tab-response">
  <a href="#get-organization">See Get Orgnaization</a>
</blockquote>

Updates values of organization by `organization_id`. The resulting organization is returned. The only fields updated are the one passed on the request body.

### Request URL

`PATCH https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`






## Delete Organization

<blockquote class="highlight tab-response">
  <h3>Response Body</h3>
</blockquote>

<pre class="highlight json tab-response"><code>null</code></pre>


Deletes the organization matching the `organization_id`

### Request URL

`DELETE https://{CLIENT_ID}.salesseek.net/api/organizations/{organization_id}`

### Request Query Parameters

Parameter |  Description
--------- | ------- 
`organization_id` | The unique ID for the organization to be updated.
