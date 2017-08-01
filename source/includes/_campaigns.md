# Campaign API

## Campaign Attributes

Parameter |  Description
--------- | ------- 
`id`      | The unique identifier for this campaign **String**
`name`    | The user provided title for the campaign **String**
`status`  | Current status of the campaign (`draft`, `ready`, `scheduled`, `sent`) **Enum (String)**
`subject` | The subject line for the campaign **String**
`campaign_type` | The type of the campaign (`direct`, `campaign`) **Enum (String)**
`to_group_id` | The ID for the group the campaign is to be sent to **String**
`to_group` | Object containing detailed information about the group associated with this campaign **Object**
`sent` | Timestamp for when the campaign was sent **Timestamp (ISO 8601)**
`used_in_automations` | Set to `true` if this campaign is currently accociated with an automation **Boolean**
`used_in_live_automations` | Set to `true` if this campaign is currently accociated with an automation which is currently set to live **Boolean**
`include_signature` | Set to `true` if the signature for the user this campaign will be sent from will be appended to the email (direct emails only) **Boolean**
`campaign_schedule_id` | Unique identifier for the campaign schedule **String**
`campaign_schedule` | Object containing detailed information about the schedule assigned to this campaign **Object**
`campaign_schedule.id` | Unique identifier for the campaign schedule **String**
`campaign_schedule.timezone` | Three character representation of the timezone for this schedule. **String**
`campaign_schedule.utc_offset` | The UTC offset from schedule in minutes **Integer**
`campaign_schedule.when` | Timestamp for when this campaign should be sent **Timestamp (ISO 8601)**
`campaign_schedule.when_utc` | Timestamp for when this campaign should be sent in UTC **Timestamp (ISO 8601)**
`track` | Set to `true` if SalesSeek should track statistics on this campaign **Boolean**
`owner_id` | Object containing detailed information about the campaign owner **Object**
`creator_id` | Object containing detailed information about the campaign creator **Object**
`last_modified_by_id` | The ID for the SalesSeek user that last modified this campaign **String**
`created` | Campaign creation timestamp **Timestamp (ISO 8601)**
`modified`| Campaign last modified timestamp **Timestamp (ISO 8601)**
`from_user_id` | ID of the user the campaign will be sent from **String**
`from_user`| Object containing detailed information about the user the campaign will be sent from **Object**
`creator` | Object containing detailed information about the campaign creator **Object**
`owner` | Object containing detailed information about the campaign owner **Object**
`email_status_stats` | Object containing email status statistics **Object**
`email_status_stats.sent` | Number of sent emails in campaign **Integer**
`email_status_stats.queued` | Number of emails queued in campaign **Integer**
`email_status_stats.in_progress` | Number of emails in progress in campaign **Integer**
`email_status_stats.failed` | Number of emails failed in campaign **Integer**
`email_status_stats.cancelled` | Number of emails queued in campaign **Integer**
`email_event_stats` | Object containing email event statistics **Object**
`email_event_stats.delivered` | Number of delivered emails in campaign **Integer**
`email_event_stats.open` | Number of delivered opened in campaign **Integer**
`email_event_stats.undelivered_rate` | Rate of un-delivered emails in campaign **Integer**
`email_event_stats.queued` | Number of emails queued in campaign **Integer**
`email_event_stats.click` | Number of clicked emails in campaign **Integer**
`email_event_stats.click_rate` | Rate of clicked emails in campaign **Integer**
`email_event_stats.hard_bounce_rate` | Rate of hard bounces in campaign **Integer**
`email_event_stats.delivered_rate` | Rate of delivered emails in campaign **Integer**
`email_event_stats.soft_bounce_rate` | Rate of soft bounces in campaign **Integer**
`email_event_stats.bounce_rate` | Rate of bounces in campaign **Integer**
`email_event_stats.hard_bounce` | Rate of hard bounces in campaign **Integer**
`email_event_stats.send` | Number of emails sent in campaign **Integer**
`email_event_stats.unsubscribed` | Number of unsubscribes from this campaign **Integer**
`email_event_stats.bounce` | Number of bounces in campaign **Integer**
`email_event_stats.spam` | Number of emails marked as spam in campaign **Integer**
`email_event_stats.open_rate` | Rate of emails opened in campaign **Integer**
`email_event_stats.unsubscribed_all_rate` | Rate of unsubscribes from all email campaigns **Integer**
`email_event_stats.spam` | Rate of emails marked as spam in this campaign **Integer**
`email_event_stats.reject` | Number of emails rejected in this campaign **Integer**
`email_event_stats.send_rate` | Rate of emails sent in this campaign **Integer**
`email_event_stats.undelivered` | Rate of emails not delivered in this campaign **Integer**
`email_event_stats.soft_bounce` | Number of soft bounces in this campaign **Integer**
`email_event_stats.unsubscribed_rate` | Rate of unsubscribes in this campaign **Integer**
`email_event_stats.reject_rate` | Rate of rejections in this campaign **Integer**
`email_event_stats.unsubscribed_all` | Number of individuals who have unsubscibed from all email campaigns **Int**
`content` | HTML content for this email **String**