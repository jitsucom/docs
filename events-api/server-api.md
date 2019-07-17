# Server API

{% api-method method="post" host="https://events.ksense.ai" path="/api/v2/events/post\_event" %}
{% api-method-summary %}
Post Event
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to post Event JSON to server. Request body can be either single JSON event, or array of JSON events
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-KSense-Tok" type="string" required=false %}
Authentication token. Alternatively token can be passed as query param. Token can be obtained trough kSense management console
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" %}
Alternative way for passing authentication token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Event successfully saved
{% endapi-method-response-example-description %}

```javascript
{
    "status": "OK"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Event hasn't been saved
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ERROR",
    "message": "Description of error"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://insights-api.ksense.ai" path="/api/v2/insights/purge\_user" %}
{% api-method-summary %}
Purge User
{% endapi-method-summary %}

{% api-method-description %}
Removes all information about particular user \(and all events associated with that user\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="ds" type="string" required=true %}
Data Source ID 
{% endapi-method-parameter %}

{% api-method-parameter name="user\_id" type="string" required=true %}
User ID \(see User ID Object Documentation\)
{% endapi-method-parameter %}

{% api-method-parameter name="user\_id\_type" type="string" required=true %}
Type of user id \(see User ID Object documentation\)
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=true %}
Authentification token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "status": "OK"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "status": "ERROR",
    "message": "{details}"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://insights-api.ksense.ai" path="/api/v2/insights/purge\_dataset" %}
{% api-method-summary %}
Purge Datasource
{% endapi-method-summary %}

{% api-method-description %}
Deletes all events from  and user from given dataset
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="ds" type="string" required=true %}
Datasource ID
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=true %}
Auth token
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

