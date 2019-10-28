# Events API

### Introduction

kSense provides event API for exporting events to its analytics and prediction system. Events can have different meaning \(depending on purpose of client integration\). It could be web page views, mobile app usage, conversions, subscription / un-subscription events and so on. Moreover, user can define a custom event types.  

There're two ways of exporting events: through JavaScript call \(pixel\) and server-to-server. Both options have the same JSON API with minor differences in user-indentification process. All definitions are applicable to both JavaScript and JSON APIs. 

### Basic concepts

#### Event Type

Each event has a type name. Some event types are pre-defined \(system even types\). Also, user can define its own type name. Each event may have a parent event type. It means that event can happen if only a parent type has happened before for the same user. System event types:

| ID | Description |
| :--- | :--- |
| pv | Web Page View |
| click | Click on a link |
| conversion | Conversion: an final event in sales funnel. Such as purchase, form-submit and so on |
| user\_info | An event for define a current user properties such as zip code.Each time user changes the  |
| subscribed | User subscribed to a service |
| unsubscribed | User un-subscribed  |
| sub\_pause | Subscription pause |
| sub\_resume | Subscription resume |
| support\_contact | Contact support |

Please see [Event JSON](event-json.md) page for further documentation.

