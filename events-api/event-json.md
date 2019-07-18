# Event JSON

Each event is represented by JSON structure. Please, see the structure schema below with examples for a few types of event

{% hint style="info" %}
Event Object Model is based on protobuf definition which is available [on our public repository on GitHub](https://github.com/ksense-co/events-api)
{% endhint %}

* **time \*\*** — an event date \(always in _**UTC!**_\), formatted as 'yyyy-MM-dd HH:mm:ss' \(example: 2018-01-14 20:45:21'\)
* **type \*** — type of event
* **event\_id \*\*** — unique id of event. If two events with same ID is posted to the system the later one will completely overwrite the former. The ID could be any string up to 256 character long.
* **data\_source\_id \*** — data source id number \(provided by kSense management console\)
* **labels** — custom event labels \(as array of {"label\_name": "label\_value"}\)
* **device** — device information
  * **ip\_v4** — IP v4
  * **ip\_v6** — IP v6
* **user\_id \*\*** — information about the user
  * **email, phone, idfa, gaid, internal\_id** — any combination of fields above. Please, see User ID section for more details
* **event\_data** — a JSON structure with custom parameters specific to event type. See parameters for system event types below. Custom event types may have any data associated with

{% hint style="info" %}
Fields marked with \* \(_type, data\_source\_id_\) are mandatory. Fields marked with \*\* \(time, event\_id, user\_info\) are mandatory for Server API calls. For JavaScript they can be skipped — values will be generated on client-side.

However, providing _user\_info_ is strictly recommended \(if user is known\) for better results
{% endhint %}

#### Example

```javascript
{
  "time_utc": "2018-11-12 14:02:45",
  "type": "pv",
  "event_id": "da9ae80f-4db4/0-334",
  "data_source_id": 4,
  "labels": {
    "custom_field1": "val1",
    "custom_field2": "val2"
  },
  "device": {
    "ip_v4": "128.0.0.1"
  },
  "user_id": {
    "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
    "phone": "enc1:MWKrIsbDoPiMeUD2mINLbg==",
    "idfa": "6d92078a-8246-4ba4-ae5b-76104861e7dc",
    "gaid": "38400000-8cf0-11bd-b23e-10b96e40000d"
  },
  "event_data": {
    "platform": "web",
    "url": "http://example.com/page1/page2"
  }
}
```

#### **Event specific fields**

Parameters that are specific to event type should be set in event\_data structure. Example of such parameter is "url". It's applicable to such event as conversion and pv \(PageView\), but can't be applied to subscription. 

For custom events, event\_data can contain any JSON structure.

| Field | Applicable to | Value |
| :--- | :--- | :--- |
| url | _conversion, pv_ | URL of a page or application URL |
| platform | _conversion, pv_ | Platform, one of: WEB, IOS, ANDROID, OTHER |
| value | _conversion_ | Value of transaction |
| value\_currency | _conversion_ | Currency of transaction |
| support\_channel | _support\_contact_ | A label of  |
| zip | _user\_info_ | Zip code of user |
| address\_line\_2 | _user\_info_ | Second line of address \(unit number\) |
| acquisition\_channel | _user\_info_ | A JSON array of string characterizing the aquisition channel. Usually the first item is a class \(online, referral, organic, mail, offline\), second item is platform \(e. g. google, facebook, criteo\) if applicable. Examples: \["online", "google"\], or \["referral"\] or \["organic", "google"\] |



####  



