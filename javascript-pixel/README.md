# JavaScript API

kSense Platform allows marketers and data owners to track their web-site usage through JavaScript pixel calls. This page describes the technical aspect of tracking.

## Pixel Initialization

In order to start tracking events following code should be placed at the head section of page:

```javascript
<script src="https://p.ksense.io/t/callbacks.js?sid={ds_id}"></script>
```

_{ds\_id}_ means DataSource ID which is obtained either through **kSense Performance Console** or through the account manager.

## Tracking

General call for tracking is:

```javascript
kpix('track', {event_type}, [additional_paremeters])
```

{event\_type} is either 'pv' \(means PageView\) or 'conversion'. \[additional\_parameters\] is an optional json object that allows data provider extend information about user. The following parameters are supported:

| Parameter | Description |
| :--- | :--- |
| user\_info | Ad additional user identification which helps kSense match users on cross-screen sessions. Please see a [dedicated page on user info](user-identification-calls.md) |
| labels | Arbitrary labels \(as string json array\) as "label\_name=label\_value". Those labels can be used for segment definitions |
| conversion\_name | The custom conversion event name, configured via [Mappings](./#mappings) |

### PageView call example

```javascript
kpix('track', 'pv');
```

### Conversion example

```javascript
kpix('track', 'conversion');
```

### Example with additional info

```javascript
kpix('track', 'pv', {
  "user_info": {
    'internal_id': '50b5337b-819f-4407-8bf1-a9f15e1d0504',
    'email': 'md5:00de5f451333e5d393cc49f1f0fd0200'
  },
  "labels": ["section=listing_view", "user_segment=new_users"]
});
```

### Dedicated user\_info calls

In some cases user\_info can't be sent through pv/conversion calls. It can happen if pixel is configured with external wrapper such as Google Tag Manager. In this case user can send user\_info data separately:

```javascript
kpix('user_info', {
  'internal_id': '',
  'email': 'md5:00de5f451333e5d393cc49f1f0fd0200',
  'phone': 'md5:614bb59e05c10c0aee2adb60c1d7cd42'
});
```

## Mappings

You can configure special event mappings for the pixel, which will trigger 3rd party tracking codes along with `kpix` tracking events.

For example, you can tell kSense pixel to trigger Facebook and Google trackers when an event `conversion_name` property is set `engagement` in additional info section.

First of all, configure appropriate mapping:

```javascript
kpix("map", {
    "conversion_name": {
        "engagement": {
            "fb": "Lead",
            "google": ["Videos", "play", "Fall Campaign"]
        }
    }
});
```

Next, issue an event with special properties:

```javascript
kpix("track", "pv", {
    "conversion_name": "engagement"
});
```

That's it. Along with the rest, the code above will issue additional tracking events to Facebook and Google with parameters like that:

```javascript
fbq("track", "Lead"); // Facebook tracker
ga("send", "event", "Videos", "play", "Fall Campaign"); // Google Analytics tracker
```

