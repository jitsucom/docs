# Server API

{% api-method method="post" host="https://p.ksense.ai" path="/api/v2/post\_event" %}
{% api-method-summary %}
Post Event
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to post Event JSON to server. Request body should be properly formed event JSON
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="X-KSense-Tok" type="string" required=false %}
Authentication token. Alternatively token can be passed as query param. Token can be obtained trough kSense management console
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="tok" type="string" %}
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



