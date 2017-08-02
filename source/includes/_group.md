# Group API

The Group API recturns the metadata for each group. 

<div class="wrap">
  <p class="flash info">
    The Group API does not return the records associated with each group. To get the associated records use the get the `filter_id` from this API and use this value in the [Group Pages API]().
  </p>
</div>

<div class="wrap">
  <p class="flash warn">
    The Group API funcionality differs depending on if the group is a smart or a static group. For an explanation of the different types of groups see the [help center article]().
  </p>
</div>

## Group Attributes

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this filter **string**
`filter_type` | The type of records to be filtered (indidivuals, opportunities, organizations, tasks) **Enum (string)**
`rules` | Array containing rules used for this filter **Array**
`rules[x].field` | The name of the field that is used in this filter **string**
`rules[x].operator` | The operator used in this filter **string**
`rules[x].values` | Object containing the values used to apply to this filter **object**
`rules[x].values.name` | Name of the values to be applied to this filter **object**
`rules[x].values.id` | ID of the values to be applied to this filter **object**