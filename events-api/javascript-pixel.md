# JavaScript API

kSense Platform allows marketers and data owners to track their web-site usage through JavaScript pixel calls. This page describes the technical aspect of tracking.

## Pixel Initialization

In order to start tracking events following code should be placed at the head section of page:

```javascript
<script src="https://p.ksense.io/t/callbacks.js"></script>
```

## Tracking

General call for tracking is:

```javascript
kpix({event_json});
```

Where event\_json is a [JSON representation of event](event-json.md)

### PageView call example

```javascript
/**
 * Record a page view event of user with hashed e-mail
 */
kpix({
    "type": "pv", //pv means "Page View"
    "data_source_id": "4",
    "labels": {
        "custom_field1": "val1",
        "custom_field2": "val2"
    },
    "user_id": {
        "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8"
    }
});
```

### Conversion example

```javascript
/**
 * Record a conversion valued at $134 and user's hashed e-mail
 */
kpix({
    "type": "conversion",
    "data_source_id": "4",
    "user_id": {
        "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",

    },
    "event_data": {
        "value": 134,
        "value_currency": "USD"
    }
});
```

### Example with additional info

```javascript
/**
 * Provides information about user. Few different IDs (internal and phone and e-mail)
 * and user's data
 */
kpix({
    "type": "conversion",
    "data_source_id": "4",
    "user_id": {
        "email": "hash1:036e32c9556cc5979a0ec187cb3d45b8",
        "internal_id": "87556713",
        "phone": "enc1:bdbaef159f409ce00822ad0c58f9bbed"
    },
    "event_data": {
        "zip": 10016,
        "value_currency": "USD",
        "address_line_2": "apt 345",
        "acquisition_channel": ["online", "facebook"]
    }
});
```



