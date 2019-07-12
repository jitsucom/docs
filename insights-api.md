# Insights API

Insights API is designed to provide thorough information on each user

{% api-method method="get" host="https://insights-api.ksense.ai" path="/api/v2/insights/user" %}
{% api-method-summary %}
User Insights
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="user\_id" type="string" required=true %}
User ID \(see User ID Object page for details\)
{% endapi-method-parameter %}

{% api-method-parameter name="user\_id\_type" type="string" required=true %}
Type of user id: email, phone or internal\_id
{% endapi-method-parameter %}

{% api-method-parameter name="ds" type="string" required=true %}
Data Source ID
{% endapi-method-parameter %}

{% api-method-parameter name="tok" type="string" required=true %}
Access token \(provided within kSense UI\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
User insights
{% endapi-method-response-example-description %}

```javascript
{
    "status": "OK",
    "expected_unsubscription_date": "2019-03-45", // a date in UTC 
    //when user is expected to unsubscribe from the service
    "unsubscription_probability_7d": "0.45", //probability that given 
    //user will unsubscribe in next 7 days
    "unsubscription_probability_3d": "0.33" //probability that given 
    //user will unsubscribe in next 3 days    
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
If request is malformed \(user doesn't exist or
{% endapi-method-response-example-description %}

```javascript
{
    "status": "ERROR",
    "message": "{error description}"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

