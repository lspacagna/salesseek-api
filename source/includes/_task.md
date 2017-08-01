# Task API

## Task Attributes

> The JSON encoded response looks like this.

```json
{
  "id": "b59b3772-4889-4e96-9b90-df5d0817ca44",
  "text": "#Sales Retry? Old RD Customer went to OT for Bone Daddies Ltd T/A Shackfuyu",
  "due_date": "2017-03-23T11:13:15.938419",
  "assignee_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "owner_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "created": "2017-03-23T11:13:15.938419",
  "creator_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "modified": "2017-07-07T11:37:18.351486",
  "last_modified_by_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "related_type": "organization",
  "related_id": "d10a4ea4-b329-4ffb-a786-d37987e3fc79",
  "completed": false,
  "complete_date": null,
  "related": {
    "id": "d10a4ea4-b329-4ffb-a786-d37987e3fc79",
    "name": "Bone Daddies Ltd T/A Shackfuyu",
    "type": "organizations"
  },
  "tags": [
    ...
  ],
  "creator": {
    ...
  },
  "owner": {
    ...
  },
  "assignee": {
    ...   
  },
}
```


Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this task **String**
`text` 	  | User provided task detail text **String**
`due_date` | Timestamp for when the task is due **Timestamp (ISO 8601)**
`assignee_id` | The unique ID for the SalesSeek user that the task is currently assigned to **String**
`owner_id` | The unique ID for the SalesSeek user that has ownership of this task **String**
`created` | Task creation timestamp **Timestamp (ISO 8601)**
`creator_id` | The unique ID for the SalesSeek user that created this task **String**
`modified`| Task last modified timestamp **Timestamp (ISO 8601)**
`last_modified_by_id` | The unique ID for the SalesSeek user that last modified this task **String**
`related_type` | The type of record in SalesSeek that the task is related to (Organization, Individual, Deal) **Enum**
`related_id` | The ID for the record that the task is reated to **String**
`completed` | Is the task marked as completed? **Boolean**
`complete_date` | Timestamp for when the task was completed **Timestamp (ISO 8601)**
`related` | Object containing detailed information about the record the task is related to **Object**
`related.id` | The ID for the record that the task is related to **String**
`related.name` | The name of the record that the task is related to **String**
`related.type` | The type of record in SalesSeek that the task is related to (Organization, Individual, Deal) **Enum**
`tags` | User provided tags associated with this task **Array (Object)**
`creator` | Object containing detailed information about the task creator **Object**
`owner` | Object containing detailed information about the task owner **Object**
`assignee` | Object containing detailed information about the task assignee **Object**


## Get Task

Returns the task matching the `task_id`

### Request URL

`GET https://{CLIENT_ID}.salesseek.net/api/tasks/{task_id}`

Parameter |  Description
--------- | ------- 
`task_id`      | The ID for the task you'd like to retrieve **String**


## Create Task

> An example request body to create a new task that is associated to an opportunity and has a due date in 1 week.

```json
{
  "assignee_id": "1445cf43-06c5-4821-9e92-7b5810840a92",
  "due_date": "Jul 26, 2017 11:00",
  "related_id": "5f592311-4e8c-400d-b535-d4738adb7e93",
  "related_type": "opportunity",
  "text": "Follow up in one week",
  "tags": []
}
```

Creates a new task and then returns the newly created task.

### Request URL

`POST https://{CLIENT_ID}.salesseek.net/api/tasks`


## Update Organization

> A example request body to change the task due date would be:

```json
{
  "due_date": "Jul 28, 2017 11:00",
}
```

Updates values of task by `task_id`. The resulting task is returned. 

### Request URL

`PATCH https://{CLIENT_ID}.salesseek.net/api/tasks/{task_id}`

Parameter |  Description
--------- | ------- 
`task_id`      | The ID for the task you'd like to update **String**


